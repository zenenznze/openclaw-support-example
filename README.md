# OpenClaw Support Example

Generic example repository for running an OpenClaw-style support agent setup.

This repository is one part of a three-repository sharing/demo set:

1. Frontend + bridge: https://github.com/zenenznze/support-agent-frontend
2. OpenClaw support example: this repository
3. Feishu/Lark data pipeline: https://github.com/zenenznze/feishu-support-pipeline

## What is included

- Example OpenClaw configuration using placeholders only.
- Default `main` agent workspace template.
- Default `support` agent workspace template.
- Generic support-agent prompt examples.
- Notes for connecting the support agent to the frontend bridge.

## What is intentionally excluded

- Production OpenClaw configuration.
- Real API keys, bot tokens, Feishu secrets, or provider credentials.
- Private documents, chat logs, sessions, traces, eval outputs, or customer data.
- Business-specific routing rules.

## Quick start

```bash
cp .env.example .env
cp configs/openclaw.example.json configs/openclaw.local.json
# Edit placeholder values before running OpenClaw.
```

Use the templates in `workspaces/` as a starting point for your own OpenClaw agent workspaces.

## Repository layout

```text
configs/                         Example OpenClaw configuration
workspaces/main-agent-default/    Default main agent workspace template
workspaces/support-agent-default/ Default support agent workspace template
prompts/                          Generic support prompts
docs/                             Integration and privacy notes
```
