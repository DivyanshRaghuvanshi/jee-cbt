# JEE CBT Practice

A static website: no server, no Python. Upload a question PDF, pick the pages, paste the answer key and take a CBT-style timed test.

## Deploy with GitHub Pages
1. Create a new GitHub repository (public).
2. Upload everything in this folder to the repository root: `index.html`, the `lib` folder (2 files), `.nojekyll` and this README. On github.com use "Add file > Upload files" and drag them all in.
3. Repository Settings > Pages > "Deploy from a branch" > branch `main`, folder `/ (root)` > Save. Your site appears at `https://<username>.github.io/<repo>/`.
4. Your own domain: in the same Pages settings, enter the domain under "Custom domain". At your DNS provider add a CNAME record pointing the subdomain to `<username>.github.io` (for a bare domain use GitHub's four A records, listed in the GitHub Pages docs). Tick "Enforce HTTPS".

Netlify or Cloudflare Pages also work: drag this folder into their dashboard.

The site must be opened through its web address. Double-clicking `index.html` will not work, because browsers block the PDF reader script on local files.

## Hosts that demand a start command
Use these (the app has no dependencies; `server.py` only uses Python's standard library):
- Build / install command: `pip install -r requirements.txt` (or leave it empty)
- Start command: `python3 server.py`
- It listens on the `PORT` environment variable that the host provides.

## Using it
- Pages: the PDF page numbers that hold the questions, for example `2-3`. Do one exercise per test.
- Answer key in order: single `D` or `4`, multiple `ACD`, numerical `12.5`.
- Question types: `S 1-8, M 9-12, N 13-20` (blank means all single-correct).
- Marking is +4 / -4 / 0 by default and can be changed per test.

## Saving your data
Attempts are stored in your browser (localStorage). Use "Download my data" on the home screen or the result screen to save a `.json` backup. On a new device or after clearing the browser, use "Load saved data" to restore it. Loading the same file twice does not create duplicates.
Your PDF is never uploaded anywhere; it is read inside your browser.
