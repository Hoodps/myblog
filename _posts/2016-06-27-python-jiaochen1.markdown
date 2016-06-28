---
layout: post
title:  "Pythoncode"
date:   2015-06-27 15:43:59
author: Hoodps
publish:false
categories: python
---

## Day 1 - 搭建开发环境

搭建开发环境

首先，确认系统安装的Python版本是2.7.x：

$ python --version
Python 2.7.5
然后，安装开发Web App需要的第三方库：

前端模板引擎jinja2：

$ easy_install jinja2
MySQL 5.x数据库，从官方网站下载并安装，安装完毕后，请务必牢记root口令。为避免遗忘口令，建议直接把root口令设置为password；

MySQL的Python驱动程序mysql-connector-python：

$ easy_install mysql-connector-python
项目结构

选择一个工作目录，然后，我们建立如下的目录结构：

awesome-python-webapp/   <-- 根目录
|
+- backup/               <-- 备份目录
|
+- conf/                 <-- 配置文件
|
+- dist/                 <-- 打包目录
|
+- www/                  <-- Web目录，存放.py文件
|  |
|  +- static/            <-- 存放静态文件
|  |
|  +- templates/         <-- 存放模板文件
|
+- LICENSE               <-- 代码LICENSE
创建好项目的目录结构后，建议同时建立Git仓库并同步至GitHub，保证代码修改的安全。

要了解Git和GitHub的用法，请移步Git教程。

开发工具

自备，推荐用Sublime Text。


## Day 2 - 编写数据库模块

在一个Web App中，所有数据，包括用户信息、发布的日志、评论等，都存储在数据库中。在awesome-python-app中，我们选择MySQL作为数据库。

Web App里面有很多地方都要访问数据库。访问数据库需要创建数据库连接、游标对象，然后执行SQL语句，最后处理异常，清理资源。这些访问数据库的代码如果分散到各个函数中，势必无法维护，也不利于代码复用。

此外，在一个Web App中，有多个用户会同时访问，系统以多进程或多线程模式来处理每个用户的请求。假设以多线程为例，每个线程在访问数据库时，都必须创建仅属于自身的连接，对别的线程不可见，否则，就会造成数据库操作混乱。

所以，我们还要创建一个简单可靠的数据库访问模型，在一个线程中，能既安全又简单地操作数据库。

为什么不选择SQLAlchemy？SQLAlchemy太庞大，过度地面向对象设计导致API太复杂。

所以我们决定自己设计一个封装基本的SELECT、INSERT、UPDATE和DELETE操作的db模块：transwarp.db。

设计db接口

设计底层模块的原则是，根据上层调用者设计简单易用的API接口，然后，实现模块内部代码。

假设transwarp.db模块已经编写完毕，我们希望以这样的方式来调用它：

首先，初始化数据库连接信息，通过create_engine()函数：

from transwarp import db
db.create_engine(user='root', password='password', database='test', host='127.0.0.1', port=3306)
然后，就可以直接操作SQL了。

如果需要做一个查询，可以直接调用select()方法，返回的是list，每一个元素是用dict表示的对应的行：

users = db.select('select * from user')
# users =>
# [
#     { "id": 1, "name": "Michael"},
#     { "id": 2, "name": "Bob"},
#     { "id": 3, "name": "Adam"}
# ]
如果要执行INSERT、UPDATE或DELETE操作，执行update()方法，返回受影响的行数：

n = db.update('insert into user(id, name) values(?, ?)', 4, 'Jack')
update()函数签名为：

update(sql, *args)
统一用?作为占位符，并传入可变参数来绑定，从根本上避免SQL注入攻击。

每个select()或update()调用，都隐含地自动打开并关闭了数据库连接，这样，上层调用者就完全不必关心数据库底层连接。

但是，如果要在一个数据库连接里执行多个SQL语句怎么办？我们用一个with语句实现：

with db.connection():
    db.select('...')
    db.update('...')
    db.update('...')
如果要在一个数据库事务中执行多个SQL语句怎么办？我们还是用一个with语句实现：

with db.transaction():
    db.select('...')
    db.update('...')
    db.update('...')
实现db模块

由于模块是全局对象，模块变量是全局唯一变量，所以，有两个重要的模块变量：

# db.py

# 数据库引擎对象:
	class _Engine(object):
	    def __init__(self, connect):
	        self._connect = connect
	    def connect(self):
	        return self._connect()

	engine = None

# 持有数据库连接的上下文对象:
	class _DbCtx(threading.local):
	    def __init__(self):
	        self.connection = None
	        self.transactions = 0

	    def is_init(self):
	        return not self.connection is None

	    def init(self):
	        self.connection = _LasyConnection()
	        self.transactions = 0

	    def cleanup(self):
	        self.connection.cleanup()
	        self.connection = None

	    def cursor(self):
	        return self.connection.cursor()

	_db_ctx = _DbCtx()
由于_db_ctx是threadlocal对象，所以，它持有的数据库连接对于每个线程看到的都是不一样的。任何一个线程都无法访问到其他线程持有的数据库连接。

有了这两个全局变量，我们继续实现数据库连接的上下文，目的是自动获取和释放连接：

	class _ConnectionCtx(object):
	    def __enter__(self):
	        global _db_ctx
	        self.should_cleanup = False
	        if not _db_ctx.is_init():
	            _db_ctx.init()
	            self.should_cleanup = True
	        return self

	    def __exit__(self, exctype, excvalue, traceback):
	        global _db_ctx
	        if self.should_cleanup:
	            _db_ctx.cleanup()

	def connection():
	    return _ConnectionCtx()
定义了__enter__()和__exit__()的对象可以用于with语句，确保任何情况下__exit__()方法可以被调用。

把_ConnectionCtx的作用域作用到一个函数调用上，可以这么写：

	with connection():
	    do_some_db_operation()
	但是更简单的写法是写个@decorator：

	@with_connection
	def do_some_db_operation():
	    pass
这样，我们实现select()、update()方法就更简单了：

	@with_connection
	def select(sql, *args):
	    pass

	@with_connection
	def update(sql, *args):
	    pass
注意到Connection对象是存储在_DbCtx这个threadlocal对象里的，因此，嵌套使用with connection()也没有问题。_DbCtx永远检测当前是否已存在Connection，如果存在，直接使用，如果不存在，则打开一个新的Connection。

对于transaction也是类似的，with transaction()定义了一个数据库事务：

	with db.transaction():
	    db.select('...')
	    db.update('...')
	    db.update('...')
函数作用域的事务也有一个简化的@decorator：

	@with_transaction
	def do_in_transaction():
	    pass
事务也可以嵌套，内层事务会自动合并到外层事务中，这种事务模型足够满足99%的需求。

事务嵌套比Connection嵌套复杂一点，因为事务嵌套需要计数，每遇到一层嵌套就+1，离开一层嵌套就-1，最后到0时提交事务：

	class _TransactionCtx(object):
	    def __enter__(self):
	        global _db_ctx
	        self.should_close_conn = False
	        if not _db_ctx.is_init():
	            _db_ctx.init()
	            self.should_close_conn = True
	        _db_ctx.transactions = _db_ctx.transactions + 1
	        return self

	    def __exit__(self, exctype, excvalue, traceback):
	        global _db_ctx
	        _db_ctx.transactions = _db_ctx.transactions - 1
	        try:
	            if _db_ctx.transactions==0:
	                if exctype is None:
	                    self.commit()
	                else:
	                    self.rollback()
	        finally:
	            if self.should_close_conn:
	                _db_ctx.cleanup()

	    def commit(self):
	        global _db_ctx
	        try:
	            _db_ctx.connection.commit()
	        except:
	            _db_ctx.connection.rollback()
	            raise

	    def rollback(self):
	        global _db_ctx
	        _db_ctx.connection.rollback()
最后，把select()和update()方法实现了，db模块就完成了。

## Day 3 - 编写ORM

有了db模块，操作数据库直接写SQL就很方便。但是，我们还缺少ORM。如果有了ORM，就可以用类似这样的语句获取User对象：

user = User.get('123')
而不是写SQL然后再转换成User对象：

u = db.select_one('select * from users where id=?', '123')
user = User(**u)
所以我们开始编写ORM模块：transwarp.orm。

设计ORM接口

和设计db模块类似，设计ORM也是从上层调用者角度来设计。

我们先考虑如何定义一个User对象，然后把数据库表users和它关联起来。

from transwarp.orm import Model, StringField, IntegerField

class User(Model):
    __table__ = 'users'
    id = IntegerField(primary_key=True)
    name = StringField()
注意到定义在User类中的__table__、id和name是类的属性，不是实例的属性。所以，在类级别上定义的属性用来描述User对象和表的映射关系，而实例属性必须通过__init__()方法去初始化，所以两者互不干扰：

# 创建实例:
user = User(id=123, name='Michael')
# 存入数据库:
user.insert()
实现ORM模块

有了定义，我们就可以开始实现ORM模块。

首先要定义的是所有ORM映射的基类Model：

class Model(dict):
    __metaclass__ = ModelMetaclass

    def __init__(self, **kw):
        super(Model, self).__init__(**kw)

    def __getattr__(self, key):
        try:
            return self[key]
        except KeyError:
            raise AttributeError(r"'Dict' object has no attribute '%s'" % key)

    def __setattr__(self, key, value):
        self[key] = value
Model从dict继承，所以具备所有dict的功能，同时又实现了特殊方法__getattr__()和__setattr__()，所以又可以像引用普通字段那样写：

>>> user['id']
123
>>> user.id
123
Model只是一个基类，如何将具体的子类如User的映射信息读取出来呢？答案就是通过metaclass：ModelMetaclass：

class ModelMetaclass(type):
    def __new__(cls, name, bases, attrs):
        mapping = ... # 读取cls的Field字段
        primary_key = ... # 查找primary_key字段
        __table__ = cls.__talbe__ # 读取cls的__table__字段
        # 给cls增加一些字段：
        attrs['__mapping__'] = mapping
        attrs['__primary_key__'] = __primary_key__
        attrs['__table__'] = __table__
        return type.__new__(cls, name, bases, attrs)
这样，任何继承自Model的类（比如User），会自动通过ModelMetaclass扫描映射关系，并存储到自身的class中。

然后，我们往Model类添加class方法，就可以让所有子类调用class方法：

class Model(dict):

    ...

    @classmethod
    def get(cls, pk):
        d = db.select_one('select * from %s where %s=?' % (cls.__table__, cls.__primary_key__.name), pk)
        return cls(**d) if d else None
User类就可以通过类方法实现主键查找：

user = User.get('123')
往Model类添加实例方法，就可以让所有子类调用实例方法：

class Model(dict):

    ...

    def insert(self):
        params = {}
        for k, v in self.__mappings__.iteritems():
            params[v.name] = getattr(self, k)
        db.insert(self.__table__, **params)
        return self
这样，就可以把一个User实例存入数据库：

user = User(id=123, name='Michael')
user.insert()
最后一步是完善ORM，对于查找，我们可以实现以下方法：

find_first()

find_all()

find_by()

对于count，可以实现：

count_all()

count_by()

以及update()和delete()方法。

最后看看我们实现的ORM模块一共多少行代码？加上注释和doctest才仅仅300多行。用Python写一个ORM是不是很容易呢？

