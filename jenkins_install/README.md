使用说明
========

[TOC]

### 一、摘要

	本roles适用于 centos6 + centos 7
	开箱即用，常规配置项目基本就绪


### 二、快速安装jenkins 最新版本
 
	ansible-playbook -i hlist deploy_jenkins.yml -uroot -k -vv -f40

	-u 指定远程主机执行脚本的账号
	-k 指定上面对应账号的密码
	-vv 显示执行过程中的详情

	Note: 如果做了公钥认证的话，可以使用下面的执行方式
	
	ansible-playbook -i hlist deploy_jenkins.yml  -vv -f40


### 三、注意事项


> 3.1、关于参数配置相关

	使用之前一定要修改hlist中的IP为你所需要部署服务的远程机器的IP

	如果场景不同，clone该代码仓库之后，请自行修改../vars/main.yml中的相关信息来满足当前场景的需求

> 3.2、关于jenkins运行账号的管理

	该roles包含的创建www账号可能会和系统初始化的账号有冲突，部署之前请再三确认

### 四、功能实现解析


> 4.1、如何跳过安全性检测

```cpp
添加一行
JENKINS_JAVA_OPTIONS="$JENKINS_JAVA_OPTIONS -Djenkins.install.runSetupWizard=false -Dpermissive-script-security.enabled=true"
```


> 4.2、如何创建管理员帐号密码

```cpp
通过启动jenkins触发groovy脚本来实现创建账号密码
```

> 4.3、如何安装插件

```cpp
通过java -jar jenkins-cli.jar -s url install-plugin plugin_name
```

### 五、具体内容

> 5.1、jdk安装 openjdk
	
	java 1.8.0

> 5.2、jenkins 安装 rpm包方式
	
	jenkins官方源最新版本

> 5.3、设置jenkins启动账号，设置jenkins家目录等

	默认账号是www
	默认账号密码是zhuima
	默认家目录是/var/www/jenkins

> 5.4、设置管理员帐号密码

	默认管理员账号密码: admin:zhuima

> 5.5、常用插件安装

- workflow-aggregator
- permissive-script-security
- rebuild
- build-name-setter
- groovy-postbuild
- postbuild-task
- jobConfigHistory
- ldap
- ansicolor
- dashboard-view
- project-stats-plugin
- extra-columns
- build-user-vars-plugin
- parameterized-trigger
- uno-choice
- git
	

### 六、FAQ

> 6.1、如何获取插件实际名称

	pip install jenkins
	s = jenkins.Jenkins(url, username, password)
	plugins = s.get_plugins_info()
	print plugins
	
	其中ShortName就是插件的名称

### 七、TODO

- [ ] docker定制
- [ ] 提供pipeline demo
- [ ] 自动替换主题


