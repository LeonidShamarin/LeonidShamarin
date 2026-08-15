# Hi, I'm Leonid Shamarin 👋

**AI Automation Engineer (n8n / JavaScript / Python)** — ERP/CRM and marketplace integrations.
Full-stack developer with an AI focus.

[![Role](https://img.shields.io/badge/AI_Automation_Engineer-n8n_·_Python_·_JavaScript-6C4DF6)](https://github.com/LeonidShamarin)
[![Portfolio](https://img.shields.io/badge/Portfolio-Visit-0A7B70)](https://portfolio-shamarin-leonid.vercel.app/)
[![Location](https://img.shields.io/badge/Location-Lviv,_Ukraine-green)](https://www.google.com/maps/place/Lviv)
[![Email](https://img.shields.io/badge/Email-leonideko1@gmail.com-red)](mailto:leonideko1@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://www.linkedin.com/in/leonid-shamarin-749649272/)

---

## 🚀 About Me

I build workflow automation, e-commerce integrations and self-hosted Python
micro-services. For a pan-European multi-brand retailer that meant **350+ n8n and
Windmill workflows**, **5+ FastAPI/Flask services** running on Coolify, and
integrations across **11+ marketplaces** — with the DevOps ownership that comes
with running your own infrastructure: Docker, Hetzner, Cloudflare, GitHub
auto-deploy.

The integration work goes deep — Odoo over JSON-RPC, Bitrix24, VTEX, Metro DE,
eBay, Mirakl — and the AI work is the part I care most about: category and
content resolution with structured output and fallback chains, retrieval over
document corpora, and agents that stop and ask a human before doing anything
irreversible. My frontend background means I can deliver a system end to end,
from the data pipeline to the interface someone actually uses.

---

## 🏆 Featured Projects

Automation and AI projects, each built to be **measured rather than
demonstrated** — the numbers below come from their own evaluation sets, and the
tests run without touching the network.

### [KB RAG Assistant](https://github.com/LeonidShamarin/kb-rag-assistant)
Retrieval-augmented assistant over a Ukrainian regulatory corpus, evaluated on
**122 golden questions**. Embedding choice dominated everything else:
all-MiniLM-L6-v2 scored hit@k 0.526 / MRR 0.310, while multilingual-e5-small at
the same 384 dimensions scored **1.000 / 0.983**. A Ukrainian stemmer added
+18.9 pp MRR on inflected queries. Hybrid retrieval reached perfect recall but
ranked *worse* than plain dense search — so the assumption that hybrid always
wins does not hold here. Answers cite the source snippet, and it refuses instead
of inventing. 61 tests.

`Python · sentence-transformers · multilingual-e5 · BM25 · Docker · pytest`

### [Doc to CRM](https://github.com/LeonidShamarin/doc-to-crm)
Reads invoices and delivery notes — PDFs or phone photos — into ledger entries,
with a review UI for whatever it is unsure about. On 40 documents: **90% fully
correct** (100% on PDFs, 100% on clean photos, 60% on difficult ones — the honest
split an aggregate hides). Human-review routing reaches 88.9% recall with zero
false alarms and caught all 5 planted mismatches. The main finding is negative:
the model's self-reported confidence was **1.00 on 36 of 40 documents, including
ones it got wrong**, so routing is driven by cross-checks instead. 111 tests.

`Python · Gemini Vision · Pydantic · FastAPI · Docker · pytest`

### [Inbox Agent](https://github.com/LeonidShamarin/inbox-agent)
A tool-calling agent that triages a queue and **stops before anything
irreversible**. Across 8 evaluation scenarios it picked the correct first tool
every time and attempted 6 irreversible actions: 5 were surfaced for human
confirmation, 1 was rejected by argument validation, none executed unattended.
Arguments are validated *before* the pause — otherwise people confirm calls that
then fail, and learn to click through without reading. Its own BM25 search
reaches hit@1 76% / hit@3 92% and stays silent 100% of the time on out-of-corpus
questions. 2.62 steps per scenario against a limit of 6; $1.16 per 1000
requests; 50 tests.

`Python · Gemini · tool calling · BM25 · human-in-the-loop · pytest`

### [AI Request Classifier](https://github.com/LeonidShamarin/request-classifier-ai)
Turns a free-form stream of internal requests (Slack, Telegram, email, in
Ukrainian) into structured records: category, priority, department, summary.
Resilience is **split by class of failure** instead of piled into one retry — a
rate limiter for quota, backoff for transient 429/5xx, a circuit breaker that
recognises a daily quota by its `quotaId` rather than blindly obeying the
API's `retryDelay`, and a self-repair pass that shows the model its own validation
error. No input row is ever dropped: a request that fails every retry still
lands in the output flagged for a human. 35 tests.

`Python · Gemini · Pydantic · asyncio · Docker · Google Sheets API · pytest`

### [Lead Processor](https://github.com/LeonidShamarin/lead-processor)
A webhook service that turns a raw landing-page enquiry into something sales can
act on in seconds: Pydantic normalises the payload (a Ukrainian mobile
written `0XXXXXXXXX` becomes `+380XXXXXXXXX`, a budget written `15k` becomes `15000`),
Llama 3.3 70B on Groq writes the summary and scores the lead, and the result
fans out to Airtable and Telegram in parallel. Everything downstream of the AI
step is **non-fatal**: if Airtable or Telegram is unreachable the endpoint still
returns 200, because losing the lead to a notification outage is the worse
failure. Classification falls back to a rule-based score if the model is down.

`Python · FastAPI · Groq (Llama 3.3 70B) · Pydantic · Airtable · Telegram Bot API`

More, including the frontend work, on my
**[portfolio](https://portfolio-shamarin-leonid.vercel.app/)**.

---

## 🛠️ Skills

- **Workflow automation** — n8n.io, Windmill, REST and webhook design
- **Languages** — Python, JavaScript, TypeScript, Node.js
- **Python web** — FastAPI, Flask, uvicorn, gunicorn, pydantic, pytest
- **AI** — OpenAI, Google Gemini, xAI Grok (incl. Vision), Anthropic Claude, RAG, structured output and fallback chains
- **Browser automation** — Playwright (Chromium), TOTP/2FA automation
- **DevOps** — Docker, Coolify, Hetzner, Cloudflare, GitHub Actions
- **Cloud and images** — AWS (S3, CloudFront, IAM, Lambda), Thumbor
- **ERP / CRM** — Odoo (JSON-RPC), Bitrix24
- **Marketplaces** — eBay, Bol.com, Mirakl, VTEX (OBI), Metro DE, Praktiker.de, Aukro, Okazii, Pigu
- **Frontend** — React.js, Angular, Redux, HTML5, CSS3, Sass, TailwindCSS, Material-UI, Bootstrap
- **Data** — Supabase, MongoDB, SQL, Firebase, Airtable, Google Sheets API
- **Testing** — pytest, Jest, React Testing Library, SonarQube

---

## 💼 Experience

### Developer, n8n / JavaScript / Python — Hajus AG
*06/2025 — 07/2026*

Designed and maintained 350+ workflows across 11+ European marketplaces; built
5+ production Python micro-services on Coolify; re-architected the OBI/VTEX
auto-posting pipeline from n8n to Windmill with AI resolution of category,
dimensions and attributes; built a pricing-intelligence system on Bitrix24 order
data; architected the AWS image pipeline (S3 + CloudFront + Thumbor), cutting
hosting costs by ~70%.

### Front-End Developer, internship — SoftServe LLC
*11/2023 — 11/2024*

React/TypeScript applications with Node.js/MongoDB backends, CI via GitHub
Actions, unit testing with Jest.

### Project Engineer — Eco-Techgroup LLC
*06/2016 — 10/2022*

End-to-end management of engineering projects: cross-functional teams,
procurement, budgeting, client communication.

---

## 🎓 Certificates

- **IBM Generative AI Engineering Professional Certificate** — 16 courses, IBM via Coursera, 08/2026 · [verify](https://www.coursera.org/account/accomplishments/specialization/5OBWSAXNAZVU)
- **Generative AI Engineering with LLMs Specialization** — IBM via Coursera, 08/2026 · [verify](https://www.coursera.org/account/accomplishments/specialization/KH4ITH2XH52M)
- **Google AI Professional Certificate** — 7 courses, Google via Coursera, 07/2026 · [verify](https://www.coursera.org/account/accomplishments/specialization/GRXNDXGMGTHC)
- **Anthropic: Claude Code 101** — 07/2026 · [verify](https://verify.skilljar.com/c/fyedtsckkc8e)
- **Mastering Claude Code: From Setup to Real Projects** — SkillsBooster via Coursera, 07/2026 · [verify](https://www.coursera.org/account/accomplishments/verify/8YPMYGZDBFP8)
- **Anthropic: AI Fluency — Framework & Foundations** — 06/2026 · [verify](https://verify.skilljar.com/c/5y6xb6hns8gn)
- **Hugging Face: AI Agents Fundamentals** — 06/2026 · [certificate](https://drive.google.com/file/d/1z-SJgGFywpgo-VqEuDoshHmMwSznLC2z/view?usp=sharing)
- **Google: AI Fundamentals** — Google via Coursera, 06/2026 · [verify](https://www.coursera.org/account/accomplishments/verify/YUEBPTUSDHJ0)
- **SoftServe Academy: Complete WebUI Engineer Course** — 01/2024 · [verify](https://career.softserveinc.com/en-us/certification/verification)
- **EF SET English Certificate** — 57/100, B2 Upper Intermediate, 05/2024 · [verify](https://cert.efset.org/w68yVi)

[All certificates](https://drive.google.com/drive/folders/1HmTlgvKdW3XtKHc_6xuCmTRQtIqBiuuJ?usp=drive_link)

**Education** — M.S. Computer Science with Honors, European University
(10/2022 — 01/2024)

---

## 📫 Let's connect

- **Email**: [leonideko1@gmail.com](mailto:leonideko1@gmail.com)
- **LinkedIn**: [Leonid Shamarin](https://www.linkedin.com/in/leonid-shamarin-749649272/)
- **Portfolio**: [portfolio-shamarin-leonid.vercel.app](https://portfolio-shamarin-leonid.vercel.app/)

Open to automation, integration and AI engineering work.