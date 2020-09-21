基于HTML、CSS、JS、JQ等对后台管理系统进行组件化封装
======

### 交流方式
* 暂无填充

## 版本说明
| 版本名称 |后端主要技术| 前端主要技术 | 浏览器兼容性 |
| ---------| ----------|----------|----------|
1.0.0|SpringBoot2.33+|原生、JQuery|主流浏览器、IE9+|

##本版本说明（v1.0.0）

#### 运行必备环境
* JDK8 181+ 
* Maven 3.5+
* Mysql 5.7+
* undertow
* Nginx

#### 技术选型
* 核心框架：NimbleCloud
* 分布式框架：SpringCloud全家桶
* 响应式框架：Spring WebFlux
* 安全框架：SpringSecurity
* 数据库连接池：Druid 
* 支持数据库：MySql、MongoDB
* 缓存：Redis、Memcached
* 文件系统：APACHE-FTP
* 前端技术：HTML、CSS、JS
* jquery 3.5+
* log4.js
* 阿里矢量图标库
* 组件：fully-auto 1.0

## 项目包名生成修改
生成规则为：
````${project.artifactId}-${project.alias}-${maven.build.timestamp}````
可以根据团队风格自由切换，均可在项目````pom.properties````中进行修改
最后更新与2020-9-21

## consul 集群部署
当前项目注册的集群使用版本为1.8.4  
如果连接不上外网的情况下，建议使用本项目中的安装包  
所有生成工具均放在 nimble-cloud-fully-auto 中，寓意全自动，当然，依照目前来看要有很长一段路需要走  
````
$_current_ip1
$_current_ip2
$_current_ip3
$_current_in_ip1
$_current_in_ip2
$_current_in_ip3

yum -y install pcre-devel openssl openssl-devel zlib zlib-devel pcre pcre-devel gcc gcc-c++  libevent libevent-devel perl unzip net-tools wget
yum -y update
mkdir -p /data/consul
cd /data/consul
touch consul.log
wget https://releases.hashicorp.com/consul/1.8.4/consul_1.8.4_linux_amd64.zip
unzip consul_1.8.4_linux_amd64.zip
rm -rf consul_1.8.4_linux_amd64.zip
./consul agent -server -ui -bootstrap-expect 3 -data-dir=data -node=$_current_ip1-$_current_in_ip1 -bind=$_current_in_ip1 -join=$_current_in_ip2 -client=0.0.0.0 -datacenter=dc1 &
./consul join $_current_in_ip2

yum -y install pcre-devel openssl openssl-devel zlib zlib-devel pcre pcre-devel gcc gcc-c++  libevent libevent-devel perl unzip net-tools wget
yum -y update
mkdir -p /data/consul
cd /data/consul
touch consul.log
wget https://releases.hashicorp.com/consul/1.8.4/consul_1.8.4_linux_amd64.zip
unzip consul_1.8.4_linux_amd64.zip
rm -rf consul_1.8.4_linux_amd64.zip
./consul agent -server -ui -bootstrap-expect 3 -data-dir=data -node=$_current_ip2-$_current_in_ip2 -bind=$_current_in_ip2 -client=0.0.0.0 -datacenter=dc1 &

yum -y install pcre-devel openssl openssl-devel zlib zlib-devel pcre pcre-devel gcc gcc-c++  libevent libevent-devel perl unzip net-tools wget
yum -y update
mkdir -p /data/consul
cd /data/consul
touch consul.log
wget https://releases.hashicorp.com/consul/1.8.4/consul_1.8.4_linux_amd64.zip
unzip consul_1.8.4_linux_amd64.zip
rm -rf consul_1.8.4_linux_amd64.zip
./consul agent -server -ui -bootstrap-expect 3 -data-dir=data -node=$_current_ip3-$_current_in_ip3 -bind=$_current_in_ip3 -join=$_current_in_ip2 -client=0.0.0.0 -datacenter=dc1 &
./consul join $_current_in_ip2

==================client
mkdir -p /etc/consul.d/
vim /etc/consul.d/client.json
{
"data_dir":"/data/consul",
"enable_script_checks":true,
"bind_addr":"",
"retry_join":[""],
"retry_interval":"30s",
"rejoin_after_leave":true,
"start_join":[""],
"node_name":""
}
````

## 功能完成进度树
- [x] 代码生成工具
    - [x] 1
        - [x] 1
- []  工作流
    - [x] 2-1
        - [x] 2-2
- [x] 后台管理
    - [x] 人员管理
    - [x] 角色管理
    - [x] 菜单管理
    - [] 
    - [] 
    - [] 
    - [] 
    - [] 
    - [] 
    - [] 

###### author：SortfGrowingup
