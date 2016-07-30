---
layout: post
title:  "Django 教程1"
date:   2015-07-25 09:34:12
author: Hoodps
categories: Django
---



## 一.写你的第一个Django APP

让我们用案例来学习，通过这个教程，我将带你一步步创建一个基本的poll应用。
它将有两部分组成：

-   一个让用户访问的polls和投票的网站
-   一个管理后台，你可以添加，修改，删除polls数据。

我将假定你已经安装了Django，你可以用一下的命令查看django的版本信息。

    $ python -m django --version
    1.9.7


如果已经安装了django，你将看到你的django版本信息，如果没安装你将得到一个“No module named django”.

## 创建项目

如果这是您第一次使用Django，你将不得不关心一些初始设置。换句话说，你需要自动生成一些代码，建立了–Django Django项目为实例的设置集合，包括数据库配置，Django特定选项和特定的应用程序设置。
打开命令行，选择一个目录，然后运行以下命令：

    $ django-admin startporject mysite

这将会创建一个叫mysite的目录在当前的目录，如果没有反应说明有错误。
可以看到刚才创建了什么：

    mysite/
        manage.py
        mysite/
            __init__.py
            settings.py
            urls.py
            wsgi.py

文件说明：
-   mysite/ 这是你项目的根目录，它的名称不重要，你可以命名为你喜欢的名字。
-   manage.py 一个命令行工具，可以让你用django项目以不同的方式进行交互。你可以阅读所有关于django和manage.    py manage.py细节。

## 运行项目
让我们来验证你的Django项目工程。改变成外mysite目录，如果你还没有，并运行下面的命令：

    $ python manage.py runserver

你将看到一下命令行输出：
    
    Performing system checks...

    System check identified no issues (0 silenced).

    You have unapplied migrations; your app may not work properly until they are applied.
    Run 'python manage.py migrate' to apply them.

    July 28, 2016 - 15:50:53
    Django version 1.9, using settings 'mysite.settings'
    Starting development server at http://127.0.0.1:8000/
    Quit the server with CONTROL-C.




































