## volumes配置
docker-compose的volume配置成db和wordpress共享，参考博客: [Docker-Compose](https://www.cnblogs.com/sparkdev/p/9803554.html)

写好docker-compose.yml文件之后，可以这样查看创建的共享volume:

```bash
docker volume ls
```

## docker-compose.yml

[Docker的wordpress示例](https://docs.docker.com/compose/wordpress/)

