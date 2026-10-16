# Octop · 自托管多智能体助手

支持多用户、多 Agent 的 AI 助手平台，集成 Web 控制台、命令行、即时通讯渠道、定时任务与工作区工具，适合个人及团队在自有环境中部署使用。

**仓库来源：** 本仓库是 [TencentCloud/Octop](https://github.com/TencentCloud/Octop) 的 Fork，保留上游项目归属与 MIT 许可。项目整体能力来自上游工程，本 Fork 的具体修改以[提交记录](https://github.com/geyaovip/Octop/commits/main/)及[与上游的差异](https://github.com/TencentCloud/Octop/compare/main...geyaovip:main)为准。

[完整中文说明](README_CN.md) · [英文说明](README_EN.md) · [上游官网](https://octop.cloud/) · [上游发行版本](https://github.com/TencentCloud/Octop/releases) · [贡献指南](CONTRIBUTING.md)

上游官网与发行版本属于原项目入口，不代表本 Fork 部署了可公开使用的在线服务。

## 核心能力

| 模块 | 功能说明 |
| --- | --- |
| 用户与 Agent | 多用户认证、管理员角色、独立 Agent 及工作区。 |
| Web 控制台 | 对话、Agent 配置、模型与渠道管理、任务与文件操作。 |
| 工具与自动化 | 终端、浏览器、远程桌面和定时任务，按运行环境配置。 |
| 扩展与知识 | 专家库、Skill、插件、Connector、MCP 与文档检索。 |
| 渠道与开发协作 | 即时通讯接入、HTTP/SSE/WebSocket API 与 ACP 集成。 |

模型、渠道与远程工具需按部署环境分别配置授权，具体支持范围见[中文说明](README_CN.md)。

## 技术架构

| 层级 | 技术 |
| --- | --- |
| 服务端 | Python 3.12+、FastAPI、Uvicorn、asyncio |
| Agent 运行时 | harness-agent、harness-gateway 及相关运行组件 |
| 控制台 | React、TypeScript、Vite |
| 数据 | SQLite（默认 WAL 模式）或 PostgreSQL |
| 入口 | Click CLI、Web、消息渠道、定时任务 |
| 质量工具 | Ruff、mypy、pytest、前端类型与构建检查 |

平台将 API、控制台和运行管理组合在同一服务中；默认数据目录为 `~/.octop/`。外部模型调用和已连接服务仍受各自的数据处理与授权规则约束。

## 快速体验上游发行包

以下命令安装 PyPI 上游发行包，不会自动安装本 Fork 的修改：

```bash
pip install octop
octop init
octop run
```

默认访问 [http://localhost:8088](http://localhost:8088)，完成管理员与模型配置。其他安装方式和桌面客户端说明见[完整中文文档](README_CN.md)。

## 阅读与开发本仓库

```bash
git clone https://github.com/geyaovip/Octop.git
cd Octop
```

| 路径 | 用途 |
| --- | --- |
| [`src/octop/`](src/octop/) | 配置、领域服务、API 与命令行 |
| [`dashboard/`](dashboard/) | Web 控制台源码 |
| [`desktop/`](desktop/) | 桌面客户端 |
| [`tests/`](tests/) | 单元与集成测试 |
| [`docs/`](docs/) | 架构、API 与使用文档 |

按 [AGENTS.md](AGENTS.md) 与[贡献指南](CONTRIBUTING.md)配置开发环境。仓库的综合检查命令为 `make all`；涉及控制台的修改还需验证前端构建。

## 许可与来源

本仓库遵循 [MIT License](LICENSE)。第三方组件及上游贡献者的归属应保留；本 Fork 不将上游整体成果表述为个人独立开发成果。
