# wordpress搭建博客

[install-wordpress-with-docker-compose](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-docker-compose)


部署一个支持SSL的博客网站，只需要如下几步：

* 配置`.env`环境变量文件
* 启动docker容器
* 配置`crontab`任务来定期更新证书

## .env文件

在本项目根目录下创建`.env`的一个环境变量配置文件，配置你的mysql账号密码：

```bash
MYSQL_ROOT_PASSWORD=$YOUR_MYSQL_ROOT_PASS
MYSQL_USER=$YOUR_MYSQL_USER
MYSQL_PASSWORD=$YOUR_MYSQL_PASS
```

## 启动docker容器

在`docker-compose.yaml`文件和`nginx-conf`目录下的两个配置文件，按需配置你自己的域名，即把**所有**的`luozhouyang.com`和`www.luozhouyang.com`替换成你自己的域名。

```bash
cd $PROJECT_PATH
# 我这里是 /root/GitHub/luozhouyang/wordpress
docker-compose up -d
```

## 配置`crontab`任务定时更新SSL证书

```bash
crontab -e

# 增加一行
* * * * 7 /root/GitHub/luozhouyang/wordpress/ssl_renew.sh >> /var/log/cron.log 2>&1
```

上面的路径换成你自己的路径。

更多`crontab`的文档自行Google。


至此，博客网站已经搭建好了。访问`https://$YOUR_DOMAIN`来访问即可。

初次访问，按照步骤进行`wordpress`配置即可。


```
