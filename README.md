# Moulding Defect Record – shared via GitHub

A single-page dashboard (`index.html`) hosted free on **GitHub Pages**. Everyone opens the same web link,
and all defect records (including photos) are kept in this repository so the whole team sees the same data.

```
index.html          the dashboard
data/records.json   shared records (updated automatically by the dashboard)
data/images/        defect photos (added automatically)
.nojekyll           tells GitHub Pages to serve files as-is
```

## 1. One-time setup (admin, ~5 minutes)

1. Sign in to GitHub → **New repository** → name it e.g. `moulding-defects`.
   - **Public** repo: anyone with the link can view the data. Free Pages hosting.
   - **Private** repo: data stays private, but GitHub Pages for private repos needs a paid GitHub plan.
     (On a private repo every user must enter a token, even to view.)
2. Upload the contents of this folder (`index.html`, `.nojekyll`, `data/records.json`) to the repo root
   (**Add file → Upload files**; drag the `data` folder in too).
3. Repo **Settings → Pages** → Source: *Deploy from a branch* → Branch: `main` / `(root)` → Save.
4. After about a minute the dashboard is live at `https://<your-user>.github.io/moulding-defects/`.
   Share that link with your team.

## 2. Create an access token (needed to ADD / EDIT records)

Viewing on a public repo needs no token. To save records, each person who enters data needs a token:

1. GitHub → profile picture → **Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**.
2. *Repository access*: **Only select repositories** → pick `moulding-defects`.
3. *Permissions → Repository permissions → Contents*: **Read and write**.
4. Generate, then copy the token (starts with `github_pat_`).
5. Anyone other than the repo owner must first be added under repo **Settings → Collaborators** (write access), then create their own token the same way.

## 3. Using the dashboard

1. Open the page link → click **⚙ GitHub Setup**.
   On `github.io` the user/repo are filled automatically; paste your token and click **Save & Sync**.
   The token is stored only in that browser (never in the repo).
2. Enter defects as before. A moment after each save the record is uploaded to GitHub automatically.
   **🔄 Sync with GitHub** pulls colleagues' latest records; it also runs on page open and every 2 minutes.
3. Excel export, filters and analysis work on the combined shared data.

## Notes

- If two people edit the same record, the most recent edit wins. New records from different people are all kept.
- Deleting a record removes it for everyone after the next sync.
- Photos are compressed in the browser (~900 px) before upload. Very large volumes of photos will grow the repo; GitHub recommends repos stay under ~1 GB.
- Don't share your token. If it leaks, revoke it on GitHub and create a new one.
- Anyone who can open the page of a **public** repo can read `data/records.json`. Don't put confidential information in a public repo.
- "Backup Data" / "Load Backup" still work and merge into the shared data on the next sync.
