# AI-Powered Job Search — Cowork Skill

An end-to-end job search system built on Claude Cowork. Say what you want to do — Claude handles the rest.

Created by [Edwin Sequeira](https://github.com/edwinseq)

→ [How it works](docs/how-it-works.html)

---

## What it does

- **Sweeps** job boards and target company career pages, scores roles against your profile, and imports only qualifying ones
- **Researches** companies and roles — fetches JDs, pulls company data, produces a research brief
- **Tailors your resume** for each role — gap analysis, targeted edits, AI feedback
- **Writes cover letters** — specific, not generic, with AI review
- **Applies** through company portals via Claude in Chrome
- **Finds hiring managers** and sends LinkedIn connection requests
- **Preps you for interviews** — likely questions, suggested answers, questions to ask
- **Tracks everything** in a live pipeline dashboard or Notion

---

## Requirements

| Tool | Required | Notes |
|------|----------|-------|
| [Claude Cowork](https://claude.ai) | ✅ Yes | Desktop app |
| [Claude in Chrome Extension](https://chromewebstore.google.com) | ✅ Yes | Needed for LinkedIn, job applications |
| Notion | Optional | For Notion-backed state |
| OpenAI API key | Optional | For AI resume/cover letter feedback |

**Supported browsers for dashboard editing:** Chrome, Edge, Safari
**Read-only dashboard:** works in all browsers

---

## Install

1. Download both `.skill` files from the `skills/` folder
2. In Cowork, go to **Settings → Skills → Install from file**
3. Install `job-search-setup.skill` first, then `job-search.skill`
4. Make sure the Claude in Chrome extension is installed and running

---

## Quick start

Once installed, open Cowork and say:

> **"set up job search"**

Claude will ask two questions (your name and target roles) and have you ready to go in under 2 minutes. Then say:

> **"run a sweep"**

That's it.

---

## Commands

Say any of these during a session:

```
run a sweep              — find new jobs matching your profile
research [company]       — deep-dive a role before applying
tailor my resume         — customize your resume for a company
cover letter             — write a targeted cover letter
apply to [company]       — final checks + submit application
find hiring manager      — locate contact and draft outreach
interview prep           — coaching for an upcoming interview
show my pipeline         — current status of all applications
show my dashboard        — open the visual pipeline view
what's next              — prioritized recommendation
commands                 — show the full command list
```

---

## Advanced options

These can be set up any time after the initial 2-minute setup:

**`add target companies`** — specify companies to monitor every sweep (Claude checks their career pages directly, regardless of job boards)

**`connect Notion`** — sync your pipeline to 6 linked Notion databases (jobs, companies, contacts, resumes, interviews, messages). Claude creates and wires everything.

**`add OpenAI key`** — enable AI-powered resume and cover letter feedback via the OpenAI API (~$0.01–0.02 per review)

**`update my profile`** — add industries, location preferences, salary floor, seniority level

**`set scoring weights`** — tune the fit-score model used during sweeps (role match, industry, location, seniority, company size)

---

## How state is stored

**Local JSON (default):** Everything lives in `job_search_state.json` in your working folder. A `job_search_dashboard.html` is auto-regenerated after every session — open it in your browser to see your pipeline. In Chrome/Edge/Safari, you can enable inline editing to update statuses and notes directly.

**Notion:** Claude creates 6 linked databases and syncs all activity. Requires a connected Notion integration in Cowork.

---

## File structure (your working folder)

After setup, your working folder will contain:

```
your-folder/
├── job_search_config.json       — your settings (state backend, AI backend, profile)
├── job_search_state.json        — pipeline data (local mode)
├── job_search_dashboard.html    — visual pipeline view (auto-regenerated)
├── openai.env                   — OpenAI key (if configured)
├── scripts/
│   └── chatgpt_feedback.py      — AI feedback helper script
├── job-applications/
│   └── CompanyName/
│       ├── jd_RoleTitle.md      — saved job description
│       ├── YourName_Role_Company_MonYYYY.docx   — tailored resume
│       └── cover_letter_Company.docx
└── resume-archive/              — old resume versions
```

---

## Scoring model

During sweeps, each role is scored 1–10 across five dimensions:

| Dimension | Default weight |
|-----------|---------------|
| Role title match | 3 |
| Industry match | 2 |
| Location fit | 2 |
| Seniority match | 2 |
| Company size fit | 1 |

Roles below your threshold (default: 6/10) are skipped. Dimensions with no configured preference score neutrally — you don't need to fill everything in.

---

## Gold resume

Your Gold resume is the master file — never edited directly. For each application, Claude copies it, renames it, and tailors only the copy. This keeps your base clean across every application.

Naming convention: `FirstLastName_Resume_2026_Gold.docx`

---

## Dashboard

The pipeline dashboard is a self-contained HTML file that Claude regenerates after every session.

- **All browsers:** read-only pipeline view, grouped by status, with fit scores and overdue follow-ups highlighted
- **Chrome / Edge / Safari:** click "Enable editing" to grant file access — status dropdowns, inline notes, and follow-up completion all write back to `job_search_state.json` instantly

---

## Reporting bugs & feedback

This is a beta release — feedback is very welcome.

**To report a bug or suggest a feature:**
1. Go to [github.com/edwinseq/job-search/issues](https://github.com/edwinseq/job-search/issues)
2. Click **New Issue**
3. Describe what happened (or what you'd like to see)

You don't need to know how to code — just describe the problem in plain language. Screenshots help if something looks broken.

**Good things to include in a bug report:**
- What you said to Claude (the exact prompt)
- What Claude did vs. what you expected
- Which state backend you're using (local JSON or Notion)
- Which AI backend (Claude only, OpenAI API, ChatGPT manual)

**Want to contribute code?** Fork the repo, make your changes, and open a Pull Request. All contributions are reviewed before merging.

---

## License

MIT — see [LICENSE](LICENSE)
