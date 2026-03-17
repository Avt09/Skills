# Skills

This repository contains custom Codex skills.

## Available skills

### market_day_analitic

Short review skill for the previous Moscow Exchange trading session.

What it does:

- analyzes the latest completed MOEX trading day
- focuses on the most liquid shares
- highlights 5 gainers and 5 losers
- uses MOEX as the primary data source
- uses BCS Express, Alfa Capital, Finam, and Aton for commentary
- produces a short text summary
- writes a JSON result file named `market_day_analitic.json`

Files:

- `market_day_analitic/SKILL.md`
- `market_day_analitic/agents/openai.yaml`
- `market_day_analitic/references/market_day_analitic.json`
