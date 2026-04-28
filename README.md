# OpenClaw Support Example

这是一个面向客服场景的 OpenClaw 示例仓库，用来展示如何组织 OpenClaw 配置、默认 agent workspace、support agent workspace 和通用提示词模板。

它是本次分享的三仓库之一：

1. 前端 + bridge：<https://github.com/zenenznze/support-agent-frontend>
2. OpenClaw 示例：当前仓库
3. 飞书/Lark 数据管线：<https://github.com/zenenznze/feishu-support-pipeline>

## 这个仓库解决什么问题

很多客服 agent 项目一开始会把前端、后端配置、知识同步脚本、私有数据混在一起。这样 demo 很快，但不利于复用，也容易把生产配置或私有资料误提交。

这个仓库只聚焦 OpenClaw 侧的通用示例：

- OpenClaw 配置应该怎么写成可分享的模板。
- 默认 main agent workspace 可以怎么组织。
- support agent workspace 可以如何约束客服回答方式。
- 客服 prompt 如何优先依赖文档，而不是只靠模型自由发挥。
- 如何和 `support-agent-frontend` 的 bridge 对接。

## 仓库包含什么

- `configs/openclaw.example.json`：OpenClaw 示例配置，只使用占位符。
- `workspaces/main-agent-default/`：默认 main agent workspace 示例。
- `workspaces/support-agent-default/`：默认 support agent workspace 示例。
- `prompts/support-agent.md`：通用客服 agent 提示词。
- `docs/integration-with-support-agent-frontend.md`：如何对接前端 bridge。
- `docs/security-and-privacy.md`：安全和隐私边界说明。
- `.env.example`：环境变量示例，不包含真实密钥。

## 仓库不包含什么

为了保证这个仓库可以公开复用，以下内容不会放进来：

- 生产 OpenClaw 配置。
- 真实 API key、bot token、Feishu/Lark secret、provider credential。
- 私有文档、客服聊天记录、session、trace、日志、评测原始输出。
- 业务专用路由规则或内部工作区内容。
- 任何客户数据或内部支持资料。

真实数据和私有配置应该放在你自己的本地目录或私有仓库里，不要提交到这个公开仓库。

## 快速开始

```bash
cp .env.example .env
cp configs/openclaw.example.json configs/openclaw.local.json
```

然后根据自己的环境修改：

- `.env`：填入自己的模型 provider key、bot token、gateway token 等。
- `configs/openclaw.local.json`：调整 provider、model、agent workspace 路径和网关配置。
- `workspaces/`：基于示例 workspace 改成自己的 agent 行为约束。

注意：`.env` 和本地私有配置文件不要提交到 git。

## 目录结构

```text
configs/                         OpenClaw 示例配置
workspaces/main-agent-default/    默认 main agent workspace 模板
workspaces/support-agent-default/ 默认 support agent workspace 模板
prompts/                          通用客服提示词
docs/                             对接说明与安全/隐私说明
```

## 和前端仓库的关系

前端和 bridge 在这里：

<https://github.com/zenenznze/support-agent-frontend>

前端 bridge 可以通过下面这些环境变量接入外部客服后端：

- `BACKEND_CHAT_URL`
- `BACKEND_HISTORY_URL`
- `BACKEND_TIMEOUT_MS`

这个 OpenClaw 示例仓库提供的是后端 agent 配置和 workspace 模板；前端仓库负责用户入口和 bridge。两者分开，是为了避免前端发布、后端实验、生产配置互相影响。

## 和飞书/Lark 数据管线的关系

飞书/Lark 数据管线在这里：

<https://github.com/zenenznze/feishu-support-pipeline>

它负责把飞书 wiki 文档、飞书聊天/话题线程等支持材料同步到本地，供客服 agent 后续检索、分析和更新知识库使用。

这个仓库不直接存放飞书同步后的真实内容，只提供 OpenClaw 侧如何使用这些知识的配置和提示词示例。

## 客服回答原则

示例 support agent workspace 采用下面的基本原则：

1. 先查本地支持文档。
2. 文档有明确答案时，优先给出文档里的解决方法。
3. 文档没有明确答案时，再用自己的话补充，并说明不确定性。
4. 不编造价格、SLA、法律承诺、账号状态等需要内部系统确认的信息。
5. 不输出密钥、cookie、客户隐私内容、内部日志或未脱敏数据。

## License

MIT
