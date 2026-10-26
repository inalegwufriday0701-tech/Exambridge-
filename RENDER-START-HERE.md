# Publish ExamBridge on Render

This is a small pilot, NOT a complete 2027 syllabus or an archive of official JAMB past questions. The question bank contains illustrative original questions.

## 1. Upload the code to GitHub
Create a new repository and upload the **contents of this folder to the repository root**, including `render.yaml`, `Dockerfile`, `server.js`, `public/`, `curriculum.json`, `question-bank.sample.json`, and `package.json`. Do not upload `data/db.json` if you ran the app locally: it contains private user data.

## 2. Deploy on Render
In the Render dashboard select New > Blueprint, connect the GitHub repository, and approve the blueprint in `render.yaml`. It requests a paid Starter web service and a 1 GB persistent disk. Confirm current pricing before approving. The disk at `/app/data` is necessary because this pilot stores accounts, enquiries and results in `/app/data/db.json`. Never switch to a diskless/free instance without migrating to a persistent database.

Render builds from `Dockerfile`, runs `node server.js`, and checks `/api/subjects`. When the deploy completes, open the `onrender.com` URL shown in your dashboard. Render provides HTTPS for that URL.

## 3. Verify
Open `/api/subjects` and confirm JSON is returned. Register a TEST account, log in, answer a practice question and check progress. Restart the service and check that the test account still exists. Back up the disk and configure monitoring.

## Before inviting real students
Migrate to a production database, add email verification, account recovery, secure cookie sessions, privacy/consent and deletion flows, stronger abuse protection, and an independent security review. Verify the syllabus against current JAMB publications and use only original/licensed questions. This independent site is NOT affiliated with JAMB and cannot issue JAMB results or register candidates.
