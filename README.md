# Invensis Learning Tools

Prototype tools and internal reference files for Invensis Learning's certification prep suite.

## ASM Flashcards Prototype

Recall-based flashcard study tool for the Agile Scrum Master (ASM) certification. 28 concept cards covering the full ASM syllabus, with spaced-repetition scheduling, an email gate after 3 free preview cards, and an admin analytics view accessible via `#admin` URL hash.

Two variants:

- **`ASM-Flashcards-Prototype-v3.html`** — Standalone focused study tool. Sticky header, embedded flashcard panel, session summary with score and course CTA. Meant to run as its own page.
- **`ASM-Flashcards-Final.html`** — Same underlying tool wrapped inside a mock blog article ("What Does a Scrum Master Actually Do?"). Shows how the widget appears when embedded within an Invensis Learning blog post.
- **`ASM-Flashcards-Prototype-v4.html`** — Earlier landing-page variant with hero, features grid, and how-it-works sections. Superseded by v3 for the standalone use case.

### Key features (both variants)

- Recall-first flip mechanic (see term → try to recall → flip → self-rate)
- Three rating buttons: Study Again, Almost, Nailed It
- Spaced-repetition scheduling: Almost = review in 3 days, Nailed It = review in 7 days
- Session summary with weighted percentage score (Nailed It × 100 + Almost × 70 + Study Again × 30) and grade label
- Downloadable session share image (1200x630 PNG)
- Email gate soft-locks the deck after 3 free preview cards (Scrum Master, Sprint, User Story)
- Mobile swipe gestures: left = Study Again, right = Almost, up = Nailed It
- Progress and unlock state persist to browser localStorage
- Sparkle burst animation on Nailed It
- Admin dashboard at `#admin` with sample KPI tiles, signup chart, top-studied concepts, and user activity table (demo data — production version connects to CRM)

### To reset the demo for testing

Click the "reset progress" link in the footer, or clear the browser's localStorage entry `invensis-asm-flashcards-v10`.

## Reference files (internal)

- **`Invensis Learning — Assets - Tools Browser.html`** — Master database of 1,038 planned assets across all 57 Invensis Learning certification courses. Filterable browsable list. Source of the ASM Flashcards spec.
- **`LSSBB Black Belt Practice _ Invensis Learning.html`** — Teammate's LSSBB practice tool saved from local dev server. Used as visual/structural reference for the flashcard tool's landing-page treatment.

## Notes

All prototypes are self-contained single-file HTML. No build step, no dependencies. Open in a browser and they run. Email capture, PDF delivery, and admin analytics all require backend integration (Mailchimp / HubSpot / CRM of choice) for production use.
