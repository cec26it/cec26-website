# CEC26 Website

The website for the **Community Education Council, District 26** (northeast Queens, NYC).
Live at **https://cdec26.org**.

This is a small, fast, **static** site (plain HTML/CSS — no database, no logins, no build
step). It is bilingual (**English / 简体中文**) and is designed to be cheap to host and
simple to keep up to date by rotating, non-technical council volunteers.

---

## How it works in one paragraph

The **website** is these files, hosted for free on **GitHub Pages**. The **documents**
(minutes, agendas, etc.) are **not** in these files — they live in the **council's Google
Drive** and are shown on the site through an embedded folder. That split is deliberate: it
keeps the website tiny and means the routine monthly task is just dropping a PDF into Drive.

---

## What's in this folder

| File | What it is |
|------|------------|
| `index.html` | The entire website (all pages, both languages, styling). |
| `404.html` | The "page not found" page. |
| `CNAME` | Tells GitHub Pages to serve the site at `cdec26.org`. Leave it alone. |
| `.nojekyll` | Tells GitHub Pages to serve files as-is. Leave it alone. |
| `robots.txt` | Lets search engines list the site. |
| `README.md` | This file. |
| `DEPLOY.md` | One-time setup instructions (creating the site and pointing the domain). |

---

## The monthly job: posting minutes / agendas after a meeting

**You do not edit the website for this.** Just:

1. Sign in to the **council's Google Drive** (the council-owned account).
2. Open the **"Meeting Minutes"** folder.
3. Drag the new PDF in. Name it tidily, e.g. `2026-06 Minutes.pdf` or `2026-06 Agenda.pdf`.

That's it — it appears on the website automatically within a minute or two. No publishing,
no code.

> The folder is shared **"Anyone with the link → Viewer"**, so anything you put in it is
> public the moment it's added. Never put drafts or anything with personal information in
> that folder.

---

## Editing the website itself (occasional)

When you need to change wording, the meeting date, or the Zoom link — not documents — you
edit `index.html`. The easiest way, with no software installed:

1. Go to the repository on **github.com**.
2. Click `index.html`, then the **pencil ✏️ (Edit)** button.
3. Make the change, then click **Commit changes**. The live site updates automatically.

**Common edits** (open `index.html` and search for the text):

- **Meeting date/time/place** — search for `June 11, 2026`. It appears twice (Home and
  Meetings). Update both.
- **Zoom registration link** — search for `zoom.us/meeting/register`. Replace **every**
  occurrence (4 of them).
- **Drive documents folder** — search for `YOUR_MINUTES_FOLDER_ID` (see DEPLOY.md).

### Important: the site is bilingual

Most text exists twice, like this:

```html
<h2 data-en="Join the next meeting" data-zh="参加下次会议">Join the next meeting</h2>
```

When you change wording, update **both** `data-en` (English) and `data-zh` (Simplified
Chinese) so the two languages stay in sync. If you can't translate, ask a Chinese-speaking
council member to fill in the `data-zh` value.

---

## Who owns what (please keep current)

To avoid losing control when volunteers change, everything should be under **council-owned
accounts**, not a personal one:

- **Domain** `cdec26.org` — registrar account (currently Network Solutions).
- **Website** — the council's **GitHub** account/organization.
- **Documents** — the council's **Google** account (Drive).

Record the logins somewhere the executive committee controls, and hand them to the next
webmaster at turnover.

---

## Costs

- GitHub Pages hosting: **free**.
- Google Drive (documents): **free** (15 GB shared; the full archive is well under that).
- Domain name: the only recurring cost (~$10–25/year), paid to the registrar.
