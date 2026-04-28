# Security and privacy notes

This repository is intentionally template-only.

Do not commit:

- `.env` files or provider API keys.
- Bot tokens or gateway auth tokens.
- Feishu/Lark app secrets, cookies, exported browser storage, or wiki tokens.
- Real support chat transcripts or customer docs.
- Session databases, traces, logs, eval reports, or generated analysis.

Recommended practice: keep private data in `local-data/`, which is ignored by git.
