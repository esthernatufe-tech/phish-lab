# Esther Natufe's Phish Lab – Phishing Simulator

A browser-based, safe training inbox for learning to spot phishing and social engineering, created by Esther Natufe.
Players review 20 emails (13 phishing, 7 legitimate) and decide: **report as phishing** or **looks legitimate**.
After each decision they get an explanation of the red flags (or why the email is safe).

## What it covers
- Homoglyph domains (Cyrillic "а" vs Latin "a", "1" vs "l", "lnc" vs "inc")
- Typosquatting: missing letter, transposed letters, doubled letter, wrong TLD
- AI-generated spear phishing (flawless, personalised, no typos)
- Display-name spoofing and Reply-To mismatch (CEO fraud / BEC)
- Subdomain tricks (`cloudvault.com.account-verify.net`)
- Double-extension malware (`Invoice.pdf.exe`)
- Macro malware leading to a **ransomware simulation** (visual only)
- QR-code phishing (quishing)
- Thread hijacking with lookalike vendor domains
- 7 realistic legitimate emails, so players learn to avoid false alarms

## Analysis tools in each email
- Sender address always visible (`Name <address>`), plus **Inspect sender** (flags non-ASCII lookalike characters) and **View headers** (Reply-To, Return-Path, SPF/DKIM/DMARC).
- Hover any link to see the real URL in a status bar at the bottom-left; **click** it to open the Link Inspector with the full URL, host/domain breakdown and an "Open anyway (simulated)" option.
- Attachments are shown as visible chips; click to see the full filename, the real final extension, the file type, and how Windows would display it.

## Emailing results
At the end, players can enter their address and click **Email my results**, which opens a prefilled draft in their own mail app (via `mailto:`), or **Copy results**. Nothing is sent or stored by the site. To prefill an organizer address, set `ORGANIZER_EMAIL` at the top of the script. Automatic collection of scores would need a backend or a form service (e.g. Formspree, EmailJS), which this static site deliberately avoids.

## Safety
Everything is fictional and runs locally in the browser. No emails are sent, no data is collected, no real files are touched, and the "ransomware" screen is just an animated overlay with a clear SIMULATION banner. All brands (Zentra Bank, Cloudvault, Parcelo, Lumen HR, Paystream, Brightfield) are made up. Please keep it that way: do not swap in real company names or logos.

## Deploy on GitHub Pages
1. Create a repo and add `index.html` and `README.md`.
2. Go to **Settings → Pages**, choose **Deploy from a branch**, select `main` and `/ (root)`, then Save.
3. Your site will be live at `https://<username>.github.io/<repo>/` within a minute or two.

## Add or edit emails
Edit the `emails` array near the top of the script in `index.html`. Each entry has: `from`, `addr`, `ret` (Return-Path), optional `replyto`, `subject`, `body` (HTML; use `L(url, text)` for links), optional `atts` (attachments) and `qr`, `phish` (true/false), `tech`, and `flags` (the lesson shown after the player answers).
