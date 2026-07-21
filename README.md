# Invensis Learning Tools

Prototype tools for Invensis Learning's certification prep suite. This repo holds the ASM (Agile Scrum Master) Flashcards prototype and a few internal reference files. Once the development team picks this up, the tool is meant to be embedded in the Invensis Learning website — email capture and study progress get wired into the existing CRM.

## Main deliverable

**`index.html`** — the ASM Flashcards study tool. Single-file HTML, no build step, no dependencies. Open it in any browser.

### What it does

- 75-card deck covering the full Agile Scrum Master certification syllabus across 10 categories (Agile Concepts, Scrum Roles, Scrum Events, Scrum Artifacts, Estimation & Planning, Metrics & Reporting, Scaling & Adoption, Facilitation & Team Dynamics, Kanban & Complementary, Technical Practices)
- Session-based study: 15 cards per session, randomised on each restart so the same user sees different subsets
- Recall-first mechanic: see term, try to answer, flip to check, self-rate Hard / Good / Easy
- Spaced-repetition scheduling: rated cards return the next day for another attempt
- Email gate soft-locks the deck after 3 free preview cards (Scrum Master, Sprint, User Story). Gate captures name + email
- Session summary with weighted percentage score (Easy × 100 + Good × 70 + Hard × 30) and grade label
- Downloadable PDF report of the session: name, score, grade, per-card breakdown with rating badges, course CTA, contact block
- Downloadable session share image (1200×630 PNG) with user's name, brand mark, score, and rating column
- Related tools grid: LSSBB Practice, PMP Flashcards (coming soon), Change Management Flashcards (coming soon)
- Contact strip: email `contact@invensislearning.com` · phone `+1 470-260-0084` · blog link
- All progress and unlock state persists to browser localStorage. Reset progress link in footer for testing

### Integration notes for the dev team

- **Email capture**: the gate form (`#gateForm`) currently stores name + email in `localStorage` only. Wire the submit handler to your CRM endpoint (HubSpot / Mailchimp / internal API). Fields are `#gateName` and `#gateEmail`.
- **PDF delivery**: the "Download PDF report" button opens a print-ready page and triggers browser print. For real delivery via email, generate the PDF server-side and attach to the welcome email that fires when the CRM captures the lead.
- **Analytics**: the tool tracks per-user session data in localStorage (`cardStates`, `totalSessionsCompleted`, `streak`, etc.). To capture aggregated analytics across all users, POST session results to your data warehouse on each `showSummary()` call.
- **Storage key**: currently `invensis-asm-flashcards-v15`. Bump the version number to force fresh state for all users after a major update.

## Other files

- **`ASM-Flashcards-Final.html`** — Same underlying tool wrapped inside a mock blog article. Shows how the widget appears when embedded within an Invensis Learning blog post.
- **`ASM-Flashcards-Prototype-v4.html`** — Older landing-page variant. Superseded — kept for reference only.
- **`Invensis Learning — Assets - Tools Browser.html`** — Internal master database of 1,038 planned assets across all 57 Invensis Learning certification courses. Source of the ASM Flashcards spec.
- **`LSSBB Black Belt Practice _ Invensis Learning.html`** — Teammate's LSSBB practice tool. Used as visual and structural reference.
