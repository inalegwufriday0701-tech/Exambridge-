# ExamBridge — 2027 UTME learning-system foundation

Independent educational practice platform; **not affiliated with JAMB**. This release expands the previous starter to a **23-subject** provisional curriculum browser, one original sample question per subject, sign-up/sign-in, per-subject CBT timer, server-side scoring, answer explanations, attempt history, enquiry submission, and an offline reviewed-question import tool. The green-and-gold original design is retained.

**Important scope:** This is a functioning software foundation, NOT a completed/verified 2027 JAMB syllabus, full lessons, or 300 genuine past questions per subject. The 2027 syllabus and prescribed reading lists must be verified against official JAMB publications; sample questions are original illustrations, not claimed past questions. Topic descriptions are editorial placeholders. Avoid publishing the platform as a complete course until qualified subject editors fill and review it.

## Run
Install Node.js 20+. In the `exambridge` folder run `npm start`, then open `http://localhost:3000`. No external npm dependencies. Do not open the HTML file directly. On first start `data/db.json` is created. Existing starter databases are upgraded to the new sample bank; accounts and attempts are preserved. Back up your data before upgrading.

## Add reviewed questions
Create a UTF-8 JSON array following `question-bank.sample.json` (each question needs unique integer `id`, subject matching `curriculum.json`, topic, question, exactly four option strings, answer index 0–3, explanation, and optional source/rights metadata). Stop server, back up `data/db.json`, run `node import-questions.js /path/to/reviewed-bank.json`, restart. The importer replaces the bank; include ALL approved questions in each import. Only use original or appropriately licensed questions; never label generated items as authentic past papers. Edit `curriculum.json` to add reviewed lessons and verify syllabus scope.

## Before public launch
The JSON store is for local/limited testing only. Migrate to a transactional database, use HTTPS, private persistent storage, backup/restore, password reset and email verification, consent/privacy policy, admin RBAC and audit trail, stronger rate limits, monitoring, accessibility and load/security testing. Implement exam-session IDs and server-validated deadlines before high-stakes/public exams; the current timer is a practice convenience, not secure proctoring. Confirm official 2027 syllabus and approved literature texts when available. No official registration, CAPS or result retrieval.

## Official source links (checked 26 October 2026)
- JAMB IBASS syllabus: https://ibass.jamb.gov.ng/
- JAMB main website: https://www.jamb.gov.ng/
- Eligibility/subject combinations: https://eligibility.jamb.gov.ng/
The official syllabus is a curriculum reference, not a freely redistributable archive of past examination papers. No authentic past questions were copied or represented as licensed. To add them, obtain permission or a rights-cleared export, verify subject/year/answer, then use `import-questions.js`.
