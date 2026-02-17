# OpenTelemetry Proto 到 TypeScript 生成器

本文档说明如何从 OpenTelemetry 的 protobuf 文件生成 TypeScript 定义。

## 用法

1. 克隆 OpenTelemetry proto 文件仓库：

```bash
git clone https://github.com/open-telemetry/opentelemetry-proto.git opentelemetry-proto
```

2. 生成 TypeScript 文件：

```bash
npm install protoc-gen-ts
CURRENT_PATH=$(pwd)
PROJECT_PATH="${CURRENT_PATH}/../../../../"

protoc \
    --plugin="${PROJECT_PATH}/node_modules/.bin/protoc-gen-ts"  \
    --ts_out="${CURRENT_PATH}/" \
    --ts_opt=esModuleInterop=true \
    --ts_opt=stringEnums=true \
    --proto_path=./opentelemetry-proto/ \
    opentelemetry-proto/opentelemetry/proto/common/v1/*.proto \
    opentelemetry-proto/opentelemetry/proto/resource/v1/*.proto \
    opentelemetry-proto/opentelemetry/proto/trace/v1/*.proto
```

3. 清理临时依赖与文件：

```bash
npm uninstall protoc-gen-ts
rm -rf opentelemetry-proto
```

## 参数说明

- `--plugin`：指定要使用的 ts-proto 插件
- `--ts_out`：生成的 TypeScript 文件输出目录
- `--ts_opt=esModuleInterop=true`：启用 ES Module 互操作
- `--ts_opt=stringEnums=true`：生成字符串枚举（而不是数字枚举）
- `--proto_path`：proto 文件的基准路径

## 生成内容

该脚本将生成以下 proto 的 TypeScript 定义：

- Common proto 文件
- Resource proto 文件
- Trace proto 文件

