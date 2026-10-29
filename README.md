## Sean Cook

I build AI agent systems and own them end to end: architecture, data model, integrations, testing, and the rollout into a live operation. I'm the founder of [Halan Digital](https://halandigital.com), most recently Chief of AI (fractional) for a staffing firm, and before that a reservoir engineer for 15 years, working on-site inside client teams at Saudi Aramco and ExxonMobil.

I also owned and ran a chiropractic clinic for two and a half years (intake, scheduling, billing, insurance credentialing), so I know healthcare administration from the front desk, not only from a spec.

**How I build:** I design the system and build it with AI coding agents (multi-agent orchestration in Claude Code). I own the architecture, data model, integration design, code review and testing, and I ship behind shadow modes, allowlists and fail-closed gates before anything touches real users.

---

### Public code

| Repo | What it is |
|---|---|
| [**rag-demo**](https://github.com/scook20/rag-demo) | A RAG pipeline in Python: Gemini embeddings, Postgres + pgvector hybrid search (vector + full-text, reciprocal rank fusion), cited answers, a three-layer fail-closed refusal gate, per-request cost and latency metrics, and a labeled eval suite. 67 tests, CI against a live pgvector service. |
| [**quill-meeting-notes**](https://github.com/scook20/quill-meeting-notes) | A native macOS meeting recorder I use every day. Two Core Audio process taps give speaker separation without a diarization model; transcription runs on-device; Claude writes the notes over a single host-pinned connection. Swift, about 6,700 lines. |
| [**personal-projects**](https://github.com/scook20/personal-projects) | Live demos and sanitized examples, including the [portfolio site](https://sean-cook-portfolio.vercel.app). |

### Production systems (client work, anonymized; code is private)

**AI recruiting pipeline: staffing firm · live in production**
Six n8n workflows screen résumés against the job, send asynchronous voice interviews, score them with Claude and Speechace, and post decisions to the firm's ATS. They include LLM retry and backoff, model-tier routing, a rate-limited API client with 429 backoff, a drift audit across 9 integration surfaces, and an error handler that logs, alerts and comments on every fault so nothing fails silently. The pipeline saved 5 recruiters 10 hours a week each.
`TypeScript` `Node.js` `n8n` `Supabase Postgres (RLS)` `Claude` `Vercel`

**Voice agent + ERP integration: field-services operation · live in sandbox**
An AI voice agent calls field technicians after each job and writes the verified work, parts and billable time into the client's ERP. Three n8n workflows handle it: a call-queue poller, a mid-call tool webhook, and a REST write-back. It fails closed by design: shadow mode, a call log written before every dial, duplicate-call protection, a phone allowlist, and throughput sized to the ERP's API license. The Python test harness covers 237 offline checks and 48 end-to-end smoke checks.
`n8n` `REST` `OData` `webhooks` `voice AI` `Python`

**NIL sports-tech platform: pre-launch startup · hosted pilot**
I'm the platform architect for a privacy-first product that handles minors' data with guardian consent. The architecture uses ports and adapters with a versioned, fail-closed rules engine; an idempotent, state-driven orchestrator; and an insert-only audit log. A model router sends sensitive data only to US-hosted, zero-retention models and has a kill switch with no silent fallback. Row-level security and separate runtime database roles are built into every migration, and the page CSP is enforced. CI runs typechecks, import-boundary checks, database policy tests (pgTAP), a Docker boot smoke test and a dependency audit on every change.
`TypeScript` `Next.js` `Postgres` `Anthropic API` `AWS Bedrock` `Vitest` `Playwright` `GitHub Actions` `Sentry`

**Six-agent AI operating dashboard: real-estate investing summit**
Specialist agents (deal sourcing, portfolio, tax, maintenance triage, rehab, lead reactivation) sit under a CEO-level orchestrator. The LLM is proxied server-side, responses stream, and pre-generated fallbacks let it run offline on a conference floor. [Live demo](https://client-rei-summit-command-center.vercel.app)
`React` `TypeScript` `Next.js` `Claude`

### Systems I run on

**A personal agent layer.** Two runtimes share one Markdown knowledge base: Claude Code on my Mac for engineering, and an always-on agent on a Tailscale-sealed VPS for the daily loop (morning brief, overnight research scouts, an approval queue, evening reconciliation). A watchdog verifies each cycle. Spend is capped through a fail-closed provider allowlist. The base holds about 700 pages, all plain Markdown + YAML, so no proprietary format holds the only copy of anything.

---

**Stack:** Python · TypeScript · SQL · Swift · Postgres / Supabase · pgvector · n8n · Claude, Gemini and OpenAI models · AWS Bedrock · Docker · GitHub Actions · Vercel · Netlify · Google Cloud (service accounts, Workspace APIs)

**Contact:** [LinkedIn](https://linkedin.com/in/sean-cook-2018) · [Portfolio](https://sean-cook-portfolio.vercel.app) · sean@halandigital.com
