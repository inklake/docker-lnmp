#docker-lnmp

## 说明

使用 Docker 容器快速启动 PHP 开发环境

1. 运行环境为 Linux alpine
2. 通过 Nginx 搭建和管理 WEB 服务器
3. 使用 Mysql 作为数据库系统，默认 root 初始密码为空，可在 docker-compose.yml 修改初始密码
4. 使用 php-fpm 作为 PHP 脚本运行环境
5. 可选接入 Redis 服务器
6. 可选接入 PHP SocketLog 调试工具

## 文件夹结构

```
dockr-lnmp
├─ html                                  # WEB 根目录
├─ mysql                                 # Mysql 数据本地化存储目录
├─ nginx                                 # Nginx 本地配置目录
│  ├─ ca                                 # WEB 域名证书存放目录
│  |  ├─ test.localhost                  # test.localhost 证书存放目录
│  |  |  ├─ server.key                   # test.localhost 测试用证书
│  |  |  └─ server.pem                   # test.localhost 测试用证书
│  |  ├─ .gitkeep                        # Git 目录占位文件
│  |  ├─ server.key                      # Nginx default 测试用证书
│  |  └─ server.pem                      # Nginx default 测试用证书
│  ├─ conf.d                             # Vhost 配置目录
│  │  ├─ default.conf                    # Nginx default 站点配置
│  │  └─ test.localhost.conf             # test.localhost 站点配置
│  ├─ config                             # Nginx 公用配置目录
│  │  ├─ common_rewrite.conf             # 公用 PHP 重定向配置
│  │  ├─ common_server.conf              # 公用 PHP 服务器配置
│  ├─ logs                               # Nginx 及站点日志存放目录
│  ├─ php                                # PHP 镜像创建及配置目录
│  │  ├─ alpine                          # PHP alpine 版本镜像编译目录
|  │  │  ├─ src                          # 镜像创建所需资源存放目录
|  │  |  │  └─ composer.phar             # PHP composer 脚本文件
│  |  │  └─ Dockerfile                   # PHP 镜像创建脚本
│  │  └─ php.ini                         # PHP 配置文件
│  ├─ redis                              # Redis 配置文件目录
│  │  └─ redis.conf                      # Redis 配置文件
│  └─ socketLog                          # PHP SocketLog 调试工具镜像编译目录
│     ├─ socketLog                       # PHP SocketLog 调试工具镜像编译目录
│     |  ├─ demo.php                     # PHP SocketLog 示例用法
│     |  ├─ slog.function.php            # PHP SocketLog 配置示例
│     |  └─ slog.php                     # PHP SocketLog 引用类库
│     └─ Dockerfile                      # PHP SocketLog 镜像创建脚本
├─ gitignore                             # Git 忽略配置
├─ docker-compose.yml                    # Docker compose 执行脚本
└─ README.md                             # 项目说明文件
```

## 用法

启动命令

```shell
docker compose up -d
```

重启命令

```shell
docker compose restart
```

停止容器

```shell
docker compose stop
```

删除所有已停止的容器

```shell
docker compose rm
```
