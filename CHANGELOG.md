# Changelog

All notable changes to the Job Search Skill will be documented here.

---

## [0.1.0] — 2026-04-08

Initial public beta release.

### Skills
- `job-search-setup` — one-time setup with fast path (2 questions, under 2 min) and advanced options
- `job-search` — daily workflow skill covering all 7 phases

### Features
- 7-phase workflow: Discovery → Research → Resume → Cover Letter → Apply → Network → Interview Prep
- Two state backends: local JSON (default) or Notion
- Three AI feedback modes: Claude only (default), OpenAI API, ChatGPT manual
- Fit scoring model with configurable weights and threshold
- Target company watchlist — career pages checked every sweep
- Exclude list — companies to never surface
- Auto-generated pipeline dashboard (HTML)
- Dashboard inline editing via File System Access API (Chrome / Edge / Safari)
- Pipeline summary and prioritization commands
- LinkedIn outreach with JS-first, minimal-screenshot approach
- Deduplication via seen jobs ledger
- Gold resume protection — master file never edited directly

### Requirements
- Claude Cowork (desktop)
- Claude in Chrome extension (required for LinkedIn and job applications)
- Notion integration (optional, for Notion state backend)
- OpenAI API key (optional, for AI feedback mode)
