# Deploying the CEC26 site to GitHub Pages

This is the **one-time setup** to get the site live. After this, updates are just commits
(for the website) or Drive drops (for documents) — see `README.md`.

The steps are split into **what you do** (you have to be logged in) and **what Claude Code
can do for you** (the file and git work). Claude Code never needs your passwords — you log
in through GitHub's and Google's own screens.

---

## Before you start — you do these (logins required)

1. **Create a council GitHub account.** Use a council-owned email (not personal). A free
   account is fine. Pick a clear name like `cec26` or `cec26nyc`.
   > GitHub Pages free hosting requires the repository to be **public**. That's fine here —
   > everything on the site is public anyway. Do not put private files in the repo.

2. **Create the Google Drive folders** (in the council Google account):
   - A folder named **Meeting Minutes**.
   - Share it: **Share → General access → Anyone with the link → Viewer**.
   - Open the folder and copy its ID from the URL
     `https://drive.google.com/drive/folders/`**`THIS_PART`** — you'll give this to Claude Code.

---

## Hand this to Claude Code

> Paste the block below to Claude Code, in the folder that contains these files
> (`index.html`, `CNAME`, etc.), after you've created the GitHub account.

```
I have a static website in this folder for CEC26 (NYC Community Education Council
District 26). Please deploy it to GitHub Pages on the council's GitHub account.

1. In index.html, replace YOUR_MINUTES_FOLDER_ID with: <paste the Drive folder ID here>
2. Initialize a git repository here, commit all files (include the .nojekyll and CNAME files).
3. Create a new PUBLIC repo on the cec26 GitHub account named "cec26-website" and push to it.
   (Pause and let me complete the GitHub login/authorization when prompted.)
4. Tell me exactly what to click to turn on GitHub Pages (Settings → Pages → Deploy from a
   branch → main / root) and to confirm the custom domain cdec26.org is set.
5. Then give me the DNS records I need to add at my domain registrar, and a way to check
   when it's live.
```

### What Claude Code will do
- Set the Drive folder ID in `index.html`.
- Run the git commands: `git init`, `git add .`, `git commit`, create the repo, `git push`.
- Walk you through enabling Pages and verifying the domain.

### What you'll do during that
- **Authorize GitHub** once, in GitHub's own login window (Claude Code will pause for this).
- In the repo on github.com: **Settings → Pages → Build and deployment → Deploy from a
  branch → Branch: `main` / folder: `/ (root)` → Save.**
- Confirm **Settings → Pages → Custom domain** shows `cdec26.org` (the `CNAME` file sets this
  automatically) and tick **Enforce HTTPS** once it becomes available.

---

## Pointing cdec26.org at GitHub Pages (DNS)

Do this at your domain registrar (currently Network Solutions). These are GitHub's current
published values — if anything fails, re-check them against GitHub's official docs, as they
can change.

**Apex domain `cdec26.org` — four A records (all with host `@`):**

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

**Optional IPv6 — four AAAA records (host `@`):**

```
2606:50c0:8000::153
2606:50c0:8001::153
2606:50c0:8002::153
2606:50c0:8003::153
```

**`www` subdomain — one CNAME record:**

```
Host: www      →      Points to: cec26.github.io
```
(Use your actual GitHub account name in place of `cec26` if you chose a different one.)

> **Heads-up:** while the domain still points at the old Network Solutions site, changing
> these records is what switches `cdec26.org` over to the new site. Test everything on the
> temporary `cec26.github.io` address first, and only change DNS when you're ready to go
> live. DNS can take anywhere from a few minutes to 24 hours to take effect.

---

## How to know it worked

1. **Before DNS:** the site should load at `https://<your-account>.github.io/cec26-website/`.
2. **After DNS:** `https://cdec26.org` loads the new site, the padlock (HTTPS) is valid, and
   `https://www.cdec26.org` redirects to it.
3. On the **Meetings** page, the embedded Drive folder shows your PDFs (once the folder ID is
   set and the folder is shared publicly).

---

## Quick recovery notes

- **Drive box says "not found":** the folder isn't shared publicly, or the ID is wrong.
- **Domain shows the old site:** DNS hasn't propagated yet, or an old record is still present.
- **HTTPS warning:** wait — GitHub issues the certificate automatically a little after DNS
  resolves; then tick **Enforce HTTPS**.
