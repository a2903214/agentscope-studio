<p align="center">
  <img
    src="https://img.alicdn.com/imgextra/i1/O1CN01nTg6w21NqT5qFKH1u_!!6000000001621-55-tps-550-550.svg"
    alt="AgentScope Logo"
    width="200"
  />
</p>

<h2 align="center">AgentScope Studio：面向开发的可视化工具集</h2>

<p align="center">
[English](./README.md) | 简体中文</p>

<p align="center">
    <a href="https://arxiv.org/abs/2402.14034">
        <img
            src="https://img.shields.io/badge/cs.MA-2402.14034-B31C1C?logo=arxiv&logoColor=B31C1C"
            alt="arxiv"
        />
    </a>
    <a href="https://www.npmjs.com/package/@agentscope/studio">
        <img
            src="https://img.shields.io/badge/dynamic/json?url=https://registry.npmjs.org/%40agentscope%2Fstudio&query=$.%27dist-tags%27.latest&prefix=v&logo=npm&label=version"
            alt="npm"
        />
    </a>
    <a href="./LICENSE">
        <img
            src="https://img.shields.io/badge/license-Apache--2.0-black"
            alt="license"
        />
    </a>
    <a href="https://agentscope.io/">
        <img
            src="https://img.shields.io/badge/Tracing-OpenTelemetry-blue?logo=look&logoColor=green&color=dark-green"
            alt="tracing"
        />
    </a>
    <a href="https://agentscope.io/">
        <img
            src="https://img.shields.io/badge/Evaluation-Agent-blue?logo=look&color=red"
            alt="evaluation"
        />
    </a>
    <a href="https://agentscope.io/">
        <img
            src="https://img.shields.io/badge/Built--in_Copilot-Friday-blue?logo=look&color=cyan"
            alt="friday"
        />
    </a>
</p>

AgentScope Studio 是一款面向 [AgentScope](https://github.com/agentscope-ai/agentscope) 开发者的**本地可视化工具集**，以**透明**、**简单**、**有趣**的方式支持智能体应用的开发、调试与评测。

## 核心功能

- **项目管理**：通过项目（Projects）与运行（Runs）组织和管理 AgentScope 项目
- **运行时可视化**：聊天式界面，实时展示智能体交互
- **追踪（Tracing）**：基于 OpenTelemetry 的 LLM 调用、Token 使用与智能体调用追踪与可视化
- **智能体评测**：从统计视角进行评测与分析
- **内置 Copilot（Friday）**：开发助手、快速二次开发 playground 与高级能力集成入口

<p align="center">
    <img
        src="https://img.alicdn.com/imgextra/i1/O1CN01PG2MdF1Zc44A1QM6N_!!6000000003214-1-tps-1971-1080.gif"
        width="49%"
        alt="home"
    />
    <img
        src="https://img.alicdn.com/imgextra/i2/O1CN01pGHedL1L4ibmyPeiq_!!6000000001246-1-tps-1971-1080.gif"
        width="49%"
        alt="runtime"
    />
    <img
        src="https://img.alicdn.com/imgextra/i1/O1CN01HfFhy928SSJAcWQ8c_!!6000000007931-1-tps-1971-1080.gif"
        width="49%"
        alt="traces"
    />
    <img
        src="https://img.alicdn.com/imgextra/i1/O1CN01vovov821Arms9tEJ1_!!6000000006945-1-tps-1971-1080.gif"
        width="49%"
        alt="friday"
    />
</p>

## 📢 动态

- **[2025-08]** AgentScope Studio 已开源，我们将持续改进并欢迎社区贡献。

## 💻 安装

### 环境要求

- **Node.js >= 20.0.0**
- **npm >= 10.0.0**
- [Docker](https://docs.docker.com/install/#supported-platforms)（可选，用于 Docker 部署）

> **💡 提示**：若使用 [nvm](https://github.com/nvm-sh/nvm)，可执行 `nvm use` 自动切换至所需 Node 版本。

```bash
# 查看版本
node --version  # 应显示 v20.x.x 或更高
npm --version   # 应显示 10.x.x 或更高
```

### 从 NPM 安装（推荐）

```bash
npm install -g @agentscope/studio

# 启动 AgentScope Studio
as_studio
```

### 从源码安装

```bash
git clone https://github.com/agentscope-ai/agentscope-studio
cd agentscope-studio
npm install

# 开发模式启动
npm run dev
```

或通过 npm 全局安装后启动：

```bash
npm install -g @agentscope/studio  # 或 npm install @agentscope/studio

as_studio
```

### Docker 部署

请参阅 [docker/README.md](docker/README.md)（或 [docker/README_zh.md](docker/README_zh.md)）。

## 🚀 快速开始

在 AgentScope 应用中接入 Studio 时，需在初始化时设置 `studio_url`：

```python
import agentscope

agentscope.init(
    # ...
    studio_url="http://localhost:3000"
)

# ...
```

## 📚 文档

更多说明请参阅：

- [概述](./docs/tutorial/zh_CN/tutorial/overview.md) - AgentScope Studio 是什么以及如何工作
- [快速开始](./docs/tutorial/zh_CN/tutorial/quick_start.md) - 安装与配置
- [项目管理](./docs/tutorial/zh_CN/develop/project.md) - 项目与运行管理
- [追踪](./docs/tutorial/zh_CN/develop/tracing.md) - OpenTelemetry 集成与语义约定
- [Friday](./docs/tutorial/zh_CN/agent/friday.md) - 内置 Copilot 说明
- [贡献指南](./docs/tutorial/zh_CN/tutorial/contributing.md) - 如何参与贡献

## ⚖️ 许可证

AgentScope Studio 基于 [Apache License 2.0](./LICENSE) 发布。

## ✨ 贡献者

感谢所有贡献者：

<a href="https://github.com/agentscope-ai/agentscope-studio/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=agentscope-ai/agentscope-studio&max=999&columns=12&anon=1" />
</a>
