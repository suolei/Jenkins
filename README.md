# Jenkins
第一章 Jenkins简介<br/>
Jenkins 是一个可扩展的持续集成引擎。<br/>

主要用于：<br/>
1.持续、自动地构建/测试软件项目。<br/>
2.监控一些定时执行的任务。<br/>

Jenkins拥有的特性包括：<br/>
1.易于安装-只要把jenkins.war部署到servlet容器，不需要数据库支持。<br/>
2.易于配置-所有配置都是通过其提供的web界面实现。<br/>
3.集成RSS/E-mail通过RSS发布构建结果或当构建完成时通过e-mail通知。<br/>
4.生成JUnit/TestNG测试报告。<br/>
5.分布式构建支持Jenkins能够让多台计算机一起构建/测试。<br/>
6.文件识别:Jenkins能够跟踪哪次构建生成哪些jar，哪次构建使用哪个版本的jar等。<br/>
7.插件支持:支持扩展插件，你可以开发适合自己团队使用的工具。<br/>

第二章 Jenkins环境准备

第三章 Jenkins安装与配置<br/>

 1 Jenkins安装：<br/>
在最简单的情况下，Jenkins 只需要两个步骤：<br/>

1.1.下载最新的版本（一个 WAR 文件）。Jenkins官方网址: http://Jenkins-ci.org/<br/>

1.2.运行 java -jar jenkins.war<br/>

注意：Jenkins 需要运行 Java 5以及以上的版本。<br/>

还有一种安装方式就是将下载的war包文件部署到 servlet 容器，然后启动容器，在浏览器的URL地址栏中输入类似http://localhost:8080/jenkins/这样的地址即可。<br/>

2 系统管理</br>
 在已运行的Jenkins主页中，点击左侧的系统管理
