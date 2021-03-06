# 可持续化集成Travis-CI入门教程
March 22, 2016
Git

[![Build Status](https://travis-ci.org/ShaoyuLee/travis-ci-tutorial.svg?branch=master)](https://travis-ci.org/ShaoyuLee/travis-ci-tutorial)

为了提高团队开发的高效性，要求每位成员提交的代码都是可编译，以保证其他成员更新后能够编译成功；当然如果有单元测试，也需要保证单元测试可通性. 而如果要求团队成员自己来完成这些工作，必然无法保证而且浪费时间. Travis-CI就是为解决这些问题而产生的. Travis-CI是一套依托于Github的可持续集成环境，可以帮助coder进行编译验证及单元测试. 本文将从零开始，为大家展现Travis-CI使用方法.

### 1. 集成步骤
* 进入[travis-ci官网](https://travis-ci.org)，点击Sign Up并取得Github授权
* 点击左侧【My Repositories】的 + 创建可持续化集成
* 打开您需要构建持续化集成的repo（当然需要在Github中已经存在的，可以点击【Sync account】来刷新）
* 在您的Github工程中添加.travis.yml文件，如:
<pre>
language: c
install:
    - make 
script:
    - "./hello"
</pre>
* 提交并push更新后，可以在travis-ci账号中心的首页参看提交及编译信息.
* 如果需要在README.md中显示build状态，可以在README.md中添加如下类似信息
<pre>
\[!\[Build Status](https://travis-ci.org/smallmuou/travis-ci-tutorial.svg?branch=master)](https://travis-ci.org/smallmuou/travis-ci-tutorial)
</pre>
PS: 进入travis-ci账号中心首页，点击build状态图标，会出现弹窗口，第二个选择框选择【Markdown】，之后拷贝文本框的内容，黏贴到README.md中即可

大家可以访问DEMO: https://github.com/smallmuou/travis-ci-tutorial

### 2. 认识.travis.yml
Travis CI分为2步: install和script

* install - 环境准备，如生成可执行文件、配置环境变量
	* before_install - install前触发
* script - 测试脚本 （返回0，表示成功，否则失败）
	* before_script - 执行测试脚本前触发	
	* after_success - 脚本执行成功后触发
	* after_failure - 脚本执行失败后触发
	* after_script - 脚本执行后触发
