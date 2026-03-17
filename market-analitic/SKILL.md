---
name: market-analitic
description: Analyze the Russian stock market for the previous trading day on the Moscow Exchange and produce a short market overview with the 5 most liquid gainers and 5 most liquid losers. Use when the user asks for a review of yesterday's MOEX trading session, a short Russian equity market summary, or a leaderboard of top risers and decliners with fresh data, an exact analysis date, and source links. Use MOEX as the primary market data source and BCS Express, Alfa Capital, Finam, and Aton for analyst commentary and context. Trigger on explicit requests for $market-analitic as well as Russian requests such as "сделай обзор рынка РФ за вчера", "проведи анализ рынка ценных бумаг России за вчера", "разбери торги на Мосбирже за вчера", "покажи лидеров роста и падения на Мосбирже", or similar phrasing about the previous MOEX trading day.
---

# Moex Yesterday Review

## Overview

Produce a short market review for the previous trading day on the Moscow Exchange. Treat MOEX as the source of truth for prices and market movement. Use BCS Express, Alfa Capital, Finam, and Aton to add brief context, sentiment, and explanations.

## Example User Requests

- Сделай обзор рынка РФ за вчера.
- Проведи анализ рынка ценных бумаг России за вчерашний день.
- Разбери торги на Мосбирже за вчера.
- Покажи 5 лидеров роста и 5 лидеров падения среди ликвидных бумаг.
- Подготовь короткий обзор российского рынка акций за прошлую торговую сессию.

## Required Outcome

Always deliver:

1. The exact date of the trading session being analyzed.
2. A short market overview in concise prose.
3. The 5 most liquid gainers for that session.
4. The 5 most liquid losers for that session.
5. Source links for all data and commentary used.

## Workflow

1. Determine the previous trading day relative to the user's locale and the current date.
2. Verify that the session date is a real MOEX trading day. If the previous calendar day was not a trading day, use the latest completed trading session and state that explicitly.
3. Collect market data from MOEX first.
4. Focus on the most liquid shares rather than the entire market universe.
5. Rank candidates by session turnover or another MOEX liquidity indicator available on the day page.
6. From that liquid universe, identify the top 5 gainers and top 5 losers by percentage change for the session.
7. Read relevant commentary from BCS Express, Alfa Capital, Finam, and Aton only as needed to explain the move.
8. Write a short overview with facts first and commentary second.

## Data Rules

- Use MOEX as the primary source for prices, turnover, and daily change.
- Prefer official MOEX tables, historical session pages, or market-data endpoints over third-party summaries.
- Do not infer leaders from commentary sites if MOEX data is available.
- If several liquidity metrics are available, prefer turnover in rubles. If turnover is unavailable, use trading volume and say so.
- Exclude obviously illiquid spikes if they do not belong to the most liquid group selected from MOEX data.

## Source Priority

Use sources in this order:

1. MOEX for the factual leaderboard and session metrics.
2. BCS Express for market color and short explanations.
3. Alfa Capital for macro or sector framing.
4. Finam for additional analyst context.
5. Aton for institutional commentary when available.

If a commentary source does not have relevant material for that date, skip it rather than forcing a citation.

## Output Format

Use this structure:

### Market overview

Write 1 short paragraph on what happened in the market during the session. Mention the exact date in full.

### Top 5 gainers among liquid shares

Provide a compact table or bullet list with:

- ticker
- company name
- daily percentage change
- liquidity metric used
- one short note if commentary explains the move

### Top 5 losers among liquid shares

Provide the same fields.

### Sources

List direct links to MOEX and each commentary page actually used.

## Writing Rules

- Keep the review short and readable.
- State the exact analysis date explicitly.
- Separate facts from interpretation.
- Do not overquote sources.
- If commentary conflicts across sources, say that analysts differ rather than collapsing the disagreement into a false certainty.

## Edge Cases

- If fresh MOEX data is temporarily unavailable, say so and do not fabricate rankings.
- If the previous day was a holiday or weekend, analyze the last completed trading session and name both the calendar day and the session date when useful.
- If liquidity filtering changes the leaderboard materially, mention that the list covers liquid shares only.

## References

- Use `references/source-checklist.md` for source handling and verification.
- Use `references/brief-template.md` for the response shape.
