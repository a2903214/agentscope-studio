# AgentScope Studio Docker 部署指南

## 目录结构

```
docker/
├── Dockerfile          # Docker 镜像定义
├── docker-compose.yml  # Docker Compose 配置
├── docker.sh           # 管理脚本
├── .dockerignore       # 构建忽略文件
└── README.md           # 本文档
```

## 前置条件：安装 Docker

在部署 AgentScope Studio 之前，你需要在系统中安装 Docker 与 Docker Compose。

请先安装 [Docker](https://docs.docker.com/install/#supported-platforms)。

## 快速开始

> **注意**：所有命令应在**项目根目录**下执行。

### 使用管理脚本（推荐）

```bash
# 添加可执行权限
chmod +x docker/docker.sh

# 构建镜像
./docker/docker.sh build

# 启动容器
./docker/docker.sh start

# 查看日志
./docker/docker.sh logs

# 停止容器
./docker/docker.sh stop

# 查看帮助
./docker/docker.sh help
```

### 手动命令

```bash
# 构建镜像
docker build -f docker/Dockerfile -t agentscope/studio:latest .

# 启动
docker-compose -f docker/docker-compose.yml up -d

# 停止
docker-compose -f docker/docker-compose.yml down
```

## 管理脚本命令

| 命令 | 说明 |
| ---- | ---- |
| `build` | 构建 Docker 镜像 |
| `start` | 启动容器 |
| `stop` | 停止容器 |
| `restart` | 重启容器 |
| `logs` | 查看日志 |
| `exec` | 进入容器 Shell |
| `status` | 查看运行状态 |
| `clean` | 清理资源 |
| `help` | 显示帮助 |

## 目录映射

| 容器路径 | 说明 |
| ------- | ---- |
| `/app` | 工作目录 |
| `/app/data` | 用户数据目录（建议挂载） |
| `/app/dist` | 编译产物 |

## 端口映射

| 端口 | 说明 |
| ---- | ---- |
| 3000 | HTTP 服务端口 |
| 4317 | gRPC / OpenTelemetry 端口 |

## 环境变量

| 变量 | 默认值 | 说明 |
| ---- | ------ | ---- |
| `NODE_ENV` | `production` | 运行环境 |
| `LOG_LEVEL` | `warn` | 日志级别（debug/log/warn/error/silent） |
| `PORT` | `3000` | HTTP 端口 |
| `HOME` | `/app/data` | 数据目录 |

## 数据持久化

用户数据存储在容器内 `/app/data` 目录，`docker-compose.yml` 默认将其挂载到宿主机的 `./data` 目录：

```yaml
volumes:
    - ./data:/app/data
```

## 故障排查

```bash
# 查看状态
./docker/docker.sh status

# 查看日志
./docker/docker.sh logs

# 清理并重建
./docker/docker.sh clean
./docker/docker.sh build
./docker/docker.sh start
```

