# Sydney Philosophy Seminar Series — Maintenance Guide

This guide explains the basic tasks you will need to do to maintain the website: updating speaker lists, dates, and semester schedules. It assumes you have basic git/GitHub skills (clone, branch, commit, push, open a PR or edit on GitHub).

What the site uses
- The site is driven by YAML data files in the `_data` directory (one file per semester). The site templates (Jekyll-style layout) read those YAML files to render the schedule and pages.
- Each talk is represented by a YAML list item containing fields such as `week`, `date`, `fulldate`, `speaker`, `affiliation`, `title`, `abstract`, and `notes`.

Basic workflow (recommended)
1. Clone the repo (or open the file in the GitHub web editor if you prefer):
   - git clone <repo-url>
   - cd sydphilseminarseries
2. Create a branch for your changes:
   - git checkout -b update-sem2-2026
3. Edit the relevant `_data/sem*.yaml` file(s) for the semester you are updating.
4. Validate and preview (see "Validate & preview" below).
5. Commit your changes:
   - git add _data/sem2_2026.yaml
   - git commit -m "Update sem2_2026 schedule: add speakers for Aug–Nov 2026"
6. Push to main:
   - git push -u origin update-sem2-2026

Editing the schedule: YAML entry explained
- Each talk is an item in the YAML list. Example minimal entry:

```yaml
- week: 3
  date: Aug 20
  fulldate: 2026-08-20
  speaker: Jane Example
  affiliation: University of Sydney
  title: The Title of the Talk
  abstract: |
    One or more paragraphs of abstract text. Use YAML block style `|` for multi-line text.
  notes: Room 123 or "No seminar" text
```

Important field conventions
- `date` — short, human-friendly display date (e.g. "Aug 20", "Feb 19").
- `fulldate` — ISO-style full date used by templates (YYYY-MM-DD). Keep this accurate; it may be used for sorting and calendar generation.
- `week` — integer or descriptive label (some files use `week: Out of Semester Seminar` or `week: Special Seminar`). Match the existing pattern in the file you edit.
- `abstract` — use `|` to preserve newlines and paragraphs. For short one-line abstracts you can put the text directly.
- If a week has no seminar, you can either:
  - Put `speaker: No seminar this week.` and leave other fields blank; or
  - Leave speaker/title blank and put a note in `notes:`, following examples already in the repo.

Adding a new semester
1. Copy an existing file for the same semester type and year, e.g.:
   - cp _data/sem1_2025.yaml _data/sem1_2026.yaml
2. Update the filename and the entries (dates, years, week numbers). Remove or comment out placeholder entries you don't yet have.
3. Commit and push as described above.

Validate & preview
- YAML mistakes (invalid indentation, tabs, incorrect list/item structure) will break the site rendering. Quick checks:
  - Use an online YAML validator or `yamllint` locally.
  - Run a local preview if you want to see the site before pushing. The site appears to be a Jekyll-style site; to preview locally:
    - Install Ruby, Bundler, Jekyll (follow Jekyll docs).
    - Run `jekyll serve` (or the equivalent bundler command) in the repo root and visit http://localhost:4000 to preview.
  - Alternatively push your branch and let GitHub Pages build/preview it (if the repo uses Pages). Check the Pages build or commit status for build errors.

Common gotchas & troubleshooting
- Wrong `fulldate` format prevents correct sorting or calendar generation — always use YYYY-MM-DD.
- YAML indentation errors: use spaces (not tabs).
- If a page looks broken after a merge, check the site build logs (Pages or CI) for YAML or Liquid/template errors.
- If abstracts include triple-backticks or other markdown that may break YAML, ensure they are properly indented and use block pipes `|`.
