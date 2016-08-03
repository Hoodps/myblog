---
layout: post
title:  "Django"
date:   2015-07-28 16:23:59
author: Hoodps
categories: python
---



## 七.url分发器
可以在settings.py文件看到，当项目一加载的时候会加载ROOT_URLCONF = 'mysite.urls'跟url.

在项目的下urls.py中的内容如下，用include包含app中的urls.py文件

	from django.conf.urls import include, url
	from django.contrib import admin

	urlpatterns = [
	    url(r'^admin/', admin.site.urls),
	    url(r'^polls/', include('polls.urls'))
	]

在app中的urls.py 文件中内容

	from django.conf.urls import url

	from . import views

	urlpatterns = [
		url(r'^$', views.index, name='index'),
		url(r'^(?P<question_id>[0-9]+)/$', views.detail, name='detail'),
		url(r'^(?P<question_id>[0-9]+)/result/$', views.result, name='result'),
		url(r'^(?P<question_id>[0-9]+)/vote/$', views.vote, name='vote'),

	]

url的正则表达式

	url(r'^test/\d{2}/$', views.test) #表示在test后面必须接一个两位数字
	# http://127.0.0.1:8000/test/23

	url(r'^test/(?P<id>\d{2})/$',views.test)
	# http://127.0.0.1:8000/test/?id=23


## 八.views.py详解
1.





