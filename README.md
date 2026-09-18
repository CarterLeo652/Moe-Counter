# Moe Counter

一个可自托管、支持多种主题的计数器服务。

## 使用 Docker

镜像同时支持 `linux/amd64` 和 `linux/arm64`。Docker 会按宿主机架构自动拉取相应镜像。

```shell
docker pull ghcr.io/carterleo652/moe-counter:latest
```

启动服务：

```shell
docker run -d --name moe-counter -p 3000:3000 \
  -v "$(pwd)/data:/app/data" \
  -e APP_PORT=3000 \
  -e DB_TYPE=sqlite \
  ghcr.io/carterleo652/moe-counter:latest
```

也可以使用 `docker-compose.yml` 从当前目录构建并启动：

```shell
docker compose up -d --build
```

## 从源码部署

```shell
git clone https://github.com/CarterLeo652/Moe-Counter.git
cd Moe-Counter
pnpm install
pnpm start
```

## 配置

在项目根目录创建 `.env` 文件，按需设置以下变量：

```dosini
# 对外访问的站点地址，例如 https://counter.example.com
# APP_SITE=https://counter.example.com

# 服务端口
APP_PORT=3000

# 数据库类型：sqlite 或 mongodb
DB_TYPE=sqlite

# 使用 MongoDB 时的连接地址
# DB_URL=mongodb://127.0.0.1:27017

# 数据库写入间隔（秒；0 表示实时写入）
DB_INTERVAL=60

# 日志级别：debug、info、warn、error 或 none
LOG_LEVEL=debug

# Google Analytics G-Tag ID
# GA_ID=G-XXXX
```

## 许可证

[MIT License](./LICENSE)，主题资源除外。
