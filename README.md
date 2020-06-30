##dockerfile打包nginx+php（多版本）环境
######本套部署环境打包，考虑实际生产中一般mysql、ES等服务或集群环境独立，故不考虑将此类三方服务打包，如需打包，可在`docker-compose.yml`文件 [service]下链入即可
#### mac 部署文档（windows同理）
* 下载安装好docker环境  https://hub.docker.com/editions/community/docker-ce-desktop-mac
##### nginx
* 新增项目则 在`/nginx/conf.d/` 下新增项目配置 如 `www.demo.com.conf`
* 使用[links]将多版本php链入
##### php
* 不同版本php 通过独立service的方式链入NGINX，不同项目根据版本需求配置到对应版本php_service[extra_hosts]下
* 将 `docker-composer.yml` 里面的 `/opt/htdocst` 替换成本地的代码根目录
#### 网络连接
* 10.254.254.1根据以下情况替换为：   
* Mac: lo0设置的别名ip   
* Win7 + Virtualbox: 虚拟机的ip 

宿主机可使用[switchhost]进行 host绑定
新增项目 需绑定host 如 [10.254.354.1 www.demo.com]

####启动docker
* 在docker-composer.yml同级目录下 执行`docker-compose up`; `docker-compose up`前台运行；`docker-compose up -d`后台运行。服务即可访问

### 项目进度
- [x] 实现一份配置文件，运行docker+nginx+php运行项目 项目浏览器可访问
- [x] 实现一份配置文件，支持多版本PHP运行项目 项目浏览器可访问
- [ ] 实现php.ini可配置化 （镜像已支持，只是本例尚未给出配置demo）
- [ ] 相关日志配置完善 （镜像已支持，只是本例尚未给出配置demo）
- [ ] 实现启动docker时 supervisor自动重启（镜像已支持，只是本例尚未给出配置demo）
- [ ] 实现镜像重启 swoole 自动重启

###docker常用命令 
* 参考：https://www.runoob.com/docker/docker-command-manual.html

