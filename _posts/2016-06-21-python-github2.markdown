---
layout: post
title:  "github 优秀Python项目2"
date:   2015-06-21 10:43:59
author: Hoodps
categories: python
---

优酷会员宽带提速脚本(电信/联通)[github地址](https://github.com/0x5e/youku_speed_up)

## Python优秀项目源码

	#!/usr/bin/env python
	# coding=utf-8

	import requests
	import json
	import time

	def main():

		username = raw_input('用户名: ')
		password = raw_input('密码: ')

		session = requests.session()

		payload = {
			'passport': username,
			'password': password,
			'captcha': '',
			'remember': '1',
			'callback': 'logincallback_%d' % (time.time() * 1000),
			'from': 'http://login.youku.com/@@@@',
			'wintype': 'page',
		}
		response = session.post(url = 'https://login.youku.com/user/login_submit/', data = payload)
		print(response.text)

		response = session.post(url = 'http://vip.youku.com/?c=ajax&a=ajax_do_speed_up')
		print(json.dumps(response.json(), ensure_ascii=False, indent=2))

	if __name__ == '__main__':
		main()



