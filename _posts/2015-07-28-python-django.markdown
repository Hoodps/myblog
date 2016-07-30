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

