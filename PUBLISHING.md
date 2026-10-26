# ExamBridge 2027 — publishing instructions

This is an independent UTME preparation **starter**, not an official JAMB service. The subject outlines are provisional and the questions are original illustrative samples, not authenticated past papers. Do not market it as a complete syllabus or a verified past-question archive.

## Run locally
Install Node.js 20+; in the exambridge directory run `npm start`; open http://localhost:3000. No npm install is necessary (built-in Node modules only).

## Deploy with Docker and persistent storage
`docker build -t exambridge .`
`docker volume create exambridge-data`
`docker run -d --name exambridge -p 3000:3000 -v exambridge-data:/app/data -e PORT=3000 --restart unless-stopped exambridge`
Use a reverse proxy with HTTPS and a domain for public access. Back up the Docker volume regularly.

## Deploy with Render
Push the `exambridge` directory as the root of a GitHub repository. In Render, create a Blueprint from the repository's `render.yaml`. Select a plan that supports a persistent disk; the JSON database **must** live on the mounted `/app/data` directory or user accounts and attempts may be lost after redeploy. Configure your custom domain and HTTPS. Check current Render pricing before proceeding.

## Critical limits before public launch
- JSON-file storage is suitable for a small pilot with **one server instance only**, not large concurrent traffic. Migrate to PostgreSQL for scale and reliable backups.
- Add email verification, password reset, admin moderation, a privacy policy, consent and deletion workflows, stronger per-route login throttling, monitoring, and independent security testing.
- The frontend stores a session bearer token in browser storage. For a public service, prefer secure HttpOnly SameSite cookies and CSRF protection.
- The CBT currently uses client-side timing and grades the current subject bank on submission; it is **practice mode**, not a secure proctored examination. Implement server-side exam sessions, fixed question snapshots, deadlines, and attempt limits before claiming otherwise.
- Obtain appropriate rights for all imported questions and confirm the curriculum against the official current JAMB syllabus.
- Never collect JAMB passwords, PINs or OTPs.
