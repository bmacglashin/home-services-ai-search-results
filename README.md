# Canopy AI Visibility Dataset — Aggregates (October 2026)

When a homeowner asks ChatGPT or Gemini to recommend — or book — a local home-service company, the answer almost never leads to a booking: in **79.1% of 5,788 paired answers** captured across 20 Southeast US metros in October 2026, the assistant offered no booking path and mentioned no connector of any kind.

This repository publishes the aggregates from that audit — metro × trade × platform counts computed from 5,932 captured answers (5,788 ChatGPT/Gemini answers plus a 144-answer Google Search comparison set) — so anyone can check, cite, or build on the numbers.

## Key findings

- **Named, not booked.** Assistants named at least one company in 99% of answers, yet 79.1% of answers dead-ended: no booking path, no connector, just names.
- **The platforms disagree.** ChatGPT and Gemini named the identical #1 company in only 10.3% of the 2,828 questions where both named a #1.
- **Connectors mean directories.** The connectors assistants mentioned were overwhelmingly directories and marketplaces — Angi (128 answers), HomeAdvisor (63), Yelp (50), Thumbtack (36). An operator's own scheduling system (Housecall Pro, Jobber class) was named in **4 of 5,788 answers**.

Full analysis: *Named, Not Booked* (working paper, Copp Oak Advisors, October 2026). Zenodo: https://doi.org/10.5281/zenodo.23745742

## The data

**File:** `canopy-ai-visibility-aggregates-2026-10.csv` — 493 rows: 20 metros × 12 trades × ChatGPT/Gemini, plus the Google Search comparison cells (12).

| Column | Meaning |
|---|---|
| `metro`, `state` | Southeast US metro as parameterized in the questions |
| `trade` | One of 12 home-service trades (HVAC, plumbing, electrical, roofing, …) |
| `platform` | ChatGPT, Gemini, or Google Search (comparison set) |
| `answers` | Answers captured in the cell (12 per cell per platform, before reruns) |
| `answers_naming_company` | Answers naming at least one company |
| `company_mentions` | Total company names recorded in the cell |
| `distinct_companies` | Distinct company-name strings (not entity-resolved; variants count separately) |
| `avg_companies_per_answer` | company_mentions / answers |
| `top_company_share_pct` | Share of the cell's mentions taken by its most-mentioned company |
| `answers_booking_offered` | Answers coded as offering a booking path |
| `answers_connector_mentioned` | Answers coded as mentioning a connector/plugin of any kind |
| `answers_neither_booking_nor_connector` | "Dead-end" answers — neither of the above |

The answer-level dataset (JSONL, 5,932 rows) is maintained by Copp Oak Advisors and is available on request.

## Methods

- **Questions.** 12 verbatim homeowner-style templates per metro × trade cell — best, emergency, specific, price, book, recommend, compare, followup, seasonal, reviews, fast, value — e.g., "What's the best HVAC company in Savannah, GA?" and "Can you book a HVAC company to come to my house in Savannah, GA this week?"
- **Paired protocol.** Every question was asked of both ChatGPT and Gemini, one fresh chat per question, verbatim. 5,916 distinct (question, platform) pairs; 16 pairs were captured twice (reruns) and are retained.
- **Models.** Consumer defaults a homeowner would encounter: Gemini on its default Flash configuration; ChatGPT on free-tier default Instant (964 answers carry runner-reported "Latest / Medium"-family configuration labels instead — the paper's Finding 4 shows the conclusions hold on the standardized subset). No Pro, reasoning, or deep-research modes.
- **Window.** Captured 2026-10-05 to 2026-10-28. AI answers drift; this is a snapshot, not a panel.
- **Limitations.** Company names are raw strings as returned (variants not entity-resolved, so the 10.3% agreement figure is a lower bound). A "phone-only" rate is **not** measurable from this capture schema and is not claimed anywhere. Connector counts are a floor (see the paper's Limitations).

## How to cite

> Copp Oak Advisors (2026). *Named, Not Booked: What ChatGPT and Gemini Actually Do When Homeowners Ask for a Local Service Company — 5,788 Paired Answers Across 20 Southeast US Metros (October 2026).* Working paper v1.0. Zenodo. https://doi.org/10.5281/zenodo.23745742

Aggregates dataset: this repository, `canopy-ai-visibility-aggregates-2026-10.csv`, CC BY 4.0.

## License

CC BY 4.0 — use the data freely with attribution to Copp Oak Advisors. See `LICENSE`.

## About

Copp Oak Advisors builds Canopy, which makes home-service companies bookable inside AI assistants. The live research summary lives at coppoak.com/canopy/research/ai-assistant-booking. Contact: support@coppoak.com.
