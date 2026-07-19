# 🧠 Decision Log — E-Commerce API Service

## Logged Architectural Decisions

| # | Decision | Alternatives Considered | Chosen Because | Impact |
|---|---|---|---|---|
| 1 | FastAPI over Flask | Flask, Django | Built-in Pydantic data validation and async IO performance | Reduced latency by 40% |
| 2 | PostgreSQL over MongoDB | MongoDB, MySQL | Transactional ACID compliance required for payment orders | Zero race conditions on stock inventory |
| 3 | Notion MCP Hub | Custom dashboard, Wiki | Standardized workspace for team review with zero setup overhead | Faster team onboarding |
