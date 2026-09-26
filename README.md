# SafeHer — Full-stack web app

SafeHer has been upgraded from a browser-only prototype to a full-stack application. It now has server-side accounts, hashed passwords, an SQLite database, HTTP-only session cookies, trusted-contact management, GPS-based SOS incidents, incident history, and private expiring location links.

## Requirements
- Node.js 22.5 or newer

## Run locally
1. Copy `.env.example` to `.env`.
2. Change `JWT_SECRET` to a long random value.
3. In this folder run `npm install`.
4. Run `npm start`.
5. Open `http://localhost:3000`.

The SQLite database is created automatically in `data/safeher.db`.

## Trusted-contact notifications
SafeHer always creates a private 24-hour location link for each trusted contact. To send these links automatically by email, configure the SMTP variables in `.env`. If SMTP is not configured, the dashboard displays the generated links so the user can share them manually.

## Emergency-services limitation
This release does **not** claim to notify or dispatch SAPS. A real police/emergency integration requires an authorized service/API and operational agreements. The app explicitly tells users this.

## Production checklist
- Deploy only over HTTPS.
- Use a strong unique `JWT_SECRET` and keep `.env` private.
- Configure a transactional email/SMS provider.
- Replace local SQLite with a managed database if usage grows substantially.
- Add rate limiting, account verification, password reset, monitoring/backups, privacy/retention controls, and a formal security review before public launch.
- Obtain legal/privacy review appropriate to processing precise location and emergency-contact data in South Africa.

## Important: run SafeHer through its Node server
Do not open `portal.html` directly and do not run this full-stack version with VS Code Live Server. Trusted contacts are stored by the Node/SQLite API. From this project folder run `npm start`, then open `http://localhost:3000` in the browser. Contacts saved there are persisted in `data/safeher.db` and are reloaded after refresh/login.
