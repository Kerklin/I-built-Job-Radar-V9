# Damir Job Radar V9

Every 6 hours GitHub collects vacancies from **9 sources**: UNDP, IOM, Save the Children, UNICEF, UN Careers, UNOPS, 2× ReliefWeb and Impactpool. It scores each vacancy against your profile in English and Bosnian/Croatian/Serbian, checks it for eligibility blockers, and publishes a **web page** you can bookmark.
No AI, no passwords, no packages, and **no GitHub actions, so no Node.js warnings**.

## Setup: 5 steps in the browser, about 10 minutes
1. **New repository**: name it `job-radar`, set it to **Public**, tick **Add a README** → **Create**.
2. **Add file → Upload files**: drag in all 7 files → **Commit changes**.
3. **Add file → Create new file**: type the name `.github/workflows/radar.yml` (typing `/` creates the folders). Paste the full contents of **radar.yml** → **Commit changes**.
4. **Settings → Actions → General → Workflow permissions** → **Read and write permissions** → **Save**.
5. **Actions → Job Radar → Run workflow**. Wait for the green ✓ (about 2 minutes). Then **Settings → Pages → Source: Deploy from a branch → Branch: main, folder / (root) → Save**. About a minute later, open `https://YOUR-USERNAME.github.io/job-radar/` and bookmark it.

**No web page yet?** Open **Actions → latest run → Summary**. The same list is there on every run.

## Reading the page
| Badge | Meaning |
|---|---|
| **OK** | Matches your profile, and no blocker was found in the text |
| **CHECK** | Matches, but the deadline or eligibility couldn't be read. Open the vacancy |
| **INELIGIBLE** | Explicit blocker: internal only, nationals of another country only, EU only, local post outside BiH, or deadline passed. Greyed out, never hidden; untick the box to see these |
| *NEW* | Found in the last 24 hours |
| *old data* | That source failed this run; this is the last good result (kept max 7 days) |

**Source health** at the bottom shows every source as OK or FAIL, with the reason and a manual link.

## Moving from V8
Delete `hunter.py`, `setup.py`, `hunt.yml`, `JOBS.md` and **every file in `.github/workflows/`** except `radar.yml`. An old workflow file left in that folder is what keeps showing Node.js warnings.

## Change things
- **Keywords, penalties, cut-off, sources:** `config.json` (pencil icon → Commit). Keywords match whole words; `građevin*` matches word beginnings.
- **Claude Code on your PC:** `git clone …` → `python radar.py --install` → `claude`
