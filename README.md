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

第二章 Jenkins环境准备<br/>
1.java环境的配置<br/>
2.安装配置Tomcat<br/>
详情可参考：http://jingyan.baidu.com/article/870c6fc33e62bcb03fe4be90.html<br/>

第三章 Jenkins安装与配置<br/>

1 Jenkins安装：<br/>
在最简单的情况下，Jenkins 只需要两个步骤：<br/>

1.1.下载最新的版本（一个 WAR 文件）。Jenkins官方网址: http://Jenkins-ci.org/<br/>

1.2.运行 java -jar jenkins.war<br/>

注意：Jenkins 需要运行 Java 5以及以上的版本。<br/>

还有一种安装方式就是将下载的war包文件部署到 servlet 容器，然后启动容器，在浏览器的URL地址栏中输入类似http://localhost:8080/jenkins/这样的地址即可。<br/>

Jenkins+MSBuild+SVN实现dotnet持续集成 快速搭建持续集成环境：详情参考：http://www.cnblogs.com/linJie1930906722/p/5966581.html
<br/>
第四章 jenkins使用

一：Jenkins+MSbuild+SVN实现dotnet持续集成 快速搭建持续集成环境<br/>

第一步：准备工作<br/>
1、系统管理--》管理插件--》可选插件中找到MSBuild Plugin， 安装插件 MSBuild Plugin<br/>
2、配置MSBuild（系统管理--》Global Tool Configuration--》MSBuild安装）<br/>
<image src='\Images\852343-20161016132049874-860505317.png'></image>
<image src='\Images\852343-20161016132337717-1687182581.png'></image>
<image src='\Images\852343-20161016132507124-318616163.png'></image>
参数填写说明：
MSBuild Name 只是一个名称可以随便填，但建议填有点意义名称，例如：MSBuild_v4.0
Path to MSBuild 这个是安装MSBuild所在的路径，例如：C:\Windows\Microsoft.NET\Framework64\v4.0.30319\MSBuild.exe

3、邮件通知配置(邮件的发送者信息)
邮件通知需要配置两个地方，一处是在系统设置，一处是在job配置中的 构建后操作 Extended E-mail Notification与E-mail Notification节点配置：

系统管理--》系统设置 找到 Extended E-mail Notification（此插件需要安装，图中的部分信息需要点击 高级 按钮才能显示）

<image src='\Images\852343-20161016140737686-1180454777.png'></image>
<image src='\Images\852343-20161016140936092-422269951.png'></image>
<image src='\Images\852343-20161016141026483-5367024.png'></image>

邮件通知节点配置（图中的部分信息需要点击 高级 按钮才能显示）：
<image src='\Images\852343-20161016141309983-1885105444.png'></image>

上面的配置是邮件的发送者的163邮件信息
说明：

SMTP server（SMTP服务器） ：登录163邮箱进行获取（ 设置--》POP3/SMTP/IMAP）

User Name（用户名）：登录163邮箱的账号名称
Password（密码）：163邮箱的 客户端授权码

登录163邮箱--》设置--》POP3/SMTP/IMAP

开启 服务POP3/SMTP/IMAP
<image src='\Images\852343-20161016143715249-925022850.png'></image>
<image src='\Images\852343-20161016144049374-1134278468.png'></image>
选中上图的 开启 获得 授权码  此授权码就是  配置邮件通知时的密码

<image src='\Images\852343-20161016144509342-17956129.png'></image>
设置客户端授权码成功：

<image src='\Images\852343-20161016144812467-843351909.png'></image>
<image src='\Images\852343-20161016144909514-974894411.png'></image>
<image src='\Images\852343-20161016145215202-1893788664.png'></image>
系统管理员邮件地址配置 可以不配置：

<image src='\Images\852343-20161016140541795-427623772.png'></image>
job里面邮件通知的配置（配置邮件接收者的信息）

<image src='\Images\852343-20161016150001170-822796692.png'></image>
进入配置：

<image src='\Images\852343-20161016151239295-731174816.png'></image>
default Content 为邮件模板：

点击 advanced settings 进入高级设置：
<image src='\Images\852343-20161016152102842-740428036.png'></image>
这里选择了成功和失败的情况下发送：

<image src='\Images\852343-20161016151716249-1774634163.png'></image>
<image src='\Images\852343-20161016152602686-1418720107.png'></image>
<image src='\Images\852343-20161016152624264-309110766.png'></image>
现在开始进行搭建job 点击 

<image src='\Images\852343-20161016193032655-1183878078.png'></image>
进入下图的界面：

<image src='\Images\852343-20161016193533608-196799265.png'></image>
点击 OK 按钮后 进入一下页面

<image src='\Images\852343-20161016194827952-1749987114.png'></image>
到处一个新的 job就新建完成了，下面开始配置job
点击 源代码管理(tab)--》选中Subversion

<image src='\Images\852343-20161016200324092-509052253.png'></image>
添加登录SVN账号和密码

<image src='\Images\852343-20161016200812030-764100282.png'></image>
最后 源代码管理(tab) 配置为：

<image src='\Images\852343-20161016201016170-49995862.png'></image>
构建触发器（tab）此项是设置间隔多长时间去检查一次SVN的代码有没有变化，如果有变化则重新编译

<image src='\Images\852343-20161016201633249-1293520517.png'></image>
构建环境(tab) 未研究此项配置有何作用，使用默认的，不做任何修改

<image src='\Images\852343-20161016202004874-1143279438.png'></image>
构建(tab)此项设置编译方式、将站点文件拷贝到iis的站点目录下发布站点

<image src='\Images\852343-20161016203153092-552938836.png'></image>
<image src='\Images\852343-20161016203856124-2140779098.png'></image>
说明：

/t:ResolveReferences;Compile /t:_CopyWebApplication /p:Configuration=Release /property:TargetFrameworkVersion=v4.0 /p:WebProjectOutputDir=D:\Jenkins_Publish\DEV_Metadata /p:OutputPath=D:\Jenkins_Publish\DEV_Metadata\bin

MSBuilder Version 为之前配置的 "MSBuild V4.0"   

MSBuild Build File 是项目文件或者工程文件的名称    

/t:Rebuild 表示每次都重建，不使用增量编译   

/property:Configuration=Release 表示编译Release版本，   

/p:WebProjectOutputDir=E:\Jenkins_Publish\DEV_Metadata表示网站发布文件的输出路径

/p:OutputPath=E:\Jenkins_Publish\DEV_Metadata\bin  表示项目Dll输出路径   

/property:TargetFrameworkVersion=v4.0表示编译的目标是.NET 4.0

 

xcopy d:\Jenkins_Publish d:\JenkinsWeb /s/e/y/exclude:C:\Users\jie\Desktop\exclude.txt    站点的文件拷贝命令

d:\Jenkins_Publish 要拷贝的文件目录

d:\JenkinsWeb 拷贝文件到此目录下

/s 复制目录和子目录，除了空的。

/e 复制目录和子目录，包括空的。

/y 禁止提示以确认改写一个现存目标文件（如果文件存在则覆盖）。

/exclude:C:\Users\jie\Desktop\exclude.txt  /exclude 指定含有字符串的文件列表。如果有任何字符串与要被复制的文件的绝对路径相符，那个文件将不会得到复制。例如，指定如 \obj\ 或 .obj 的字符串会排除目录 obj 下面的所有文件或带有.obj 扩展名的件。exclude.txt文档是排除文件或者目录，如果有排除多种类型的文件或者目录，则用户换行分割

<image src='Images\852343-20161016210312155-904591075.png'></image>
说明：
排除 .pdb后缀的文件，和web.config 文件

构建后操作(tab) 此项主要是配置邮件通知 将编译情况发送给开发者

<image src='Images\852343-20161016215214545-583119719.png'></image>
<image src='Images\852343-20161016212422842-552893537.png'></image>
编译错误时发送通知：

<image src='Images\852343-20161016213405920-582291345.png'></image>

编译成功时发送邮件通知：

<image src='\Images\852343-20161016213549780-1997556262.png'></image>
<image src='\Images\852343-20161016213917811-841888291.png'></image>
说明：
Recipient List ：接收邮件的邮箱（如果有多个用英文逗号隔开）
Content ：发送邮件的模板

到此已经job配置完成，下面来看看 构建结果


<image src='\Images\852343-20161016220914342-833636600.png'></image>
构建成功
此次测试安装的插件：

<image src='\Images\852343-20161016221108170-905562741.png'></image>




