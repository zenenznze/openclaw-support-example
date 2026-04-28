# Integration with support-agent-frontend

The frontend + bridge repository is:

https://github.com/zenenznze/support-agent-frontend

The bridge can call an external support backend using:

- `BACKEND_CHAT_URL`
- `BACKEND_HISTORY_URL`
- `BACKEND_TIMEOUT_MS`

A minimal backend should expose:

- `POST /api/chat`
- `GET /api/history`

Keep bridge/frontend deployment separate from OpenClaw backend configuration so experiments do not break production traffic.
