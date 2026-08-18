# Triptiix animated GitHub profile — beginner setup

This folder is ready to become the special `Triptiix/Triptiix` profile repository. The source portrait is deliberately excluded; only its generated ASCII artwork is public.

The large full-green heatmap in the README is a labelled demonstration visualization. GitHub's native contribution calendar remains the authoritative activity record. The separate `contribution-graph.svg` continues to use genuine public data; `demo-contribution-graph.svg` is presentation artwork.

## Option A — easiest: upload through the GitHub website

1. Sign in to GitHub and open `https://github.com/Triptiix`.
2. Create a **public** repository named exactly `Triptiix` if it does not already exist. Tick **Add a README file**.
3. Open the repository, choose **Add file → Upload files**.
4. Upload everything in this package except the `tests` folder if you prefer a smaller repository.
5. GitHub's browser uploader does not reliably preserve hidden nested folders. Create the workflow separately:
   - Choose **Add file → Create new file**.
   - In the filename box enter `.github/workflows/update-profile-art.yml`.
   - Copy the contents of the packaged workflow file into the editor.
   - Commit the file.
6. Open your public profile at `https://github.com/Triptiix` and confirm the artwork appears.

## Option B — recommended: GitHub Desktop

1. Install GitHub Desktop from `https://desktop.github.com/` and sign in.
2. Create the public `Triptiix` repository on GitHub as described above.
3. In GitHub Desktop choose **File → Clone repository**, select `Triptiix`, and click **Clone**.
4. Open the cloned folder on your computer.
5. Copy every file and folder from this package into the cloned folder. Select **Replace** if asked about `README.md`.
6. Return to GitHub Desktop. In **Summary**, write `Create animated profile`.
7. Click **Commit to main**, then **Push origin**.

## Run the daily updater once

1. Open the `Triptiix` repository on GitHub.
2. Click **Actions**.
3. Select **Update profile contribution graph** on the left.
4. Click **Run workflow**, then click the green **Run workflow** button.
5. Wait around a minute and refresh. A green check means it worked.

The workflow runs every day at approximately 11:47 AM India time. GitHub may delay scheduled jobs during busy periods; that is normal.

## Regenerate the portrait later

You do not need this for the included portrait—the SVG has already been generated.

1. Install Python 3 from `https://www.python.org/downloads/`.
2. Open Terminal (macOS) or PowerShell (Windows) inside the profile folder.
3. Create an isolated Python environment:

   macOS/Linux:

   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   pip install -r requirements.txt
   ```

   Windows PowerShell:

   ```powershell
   py -m venv .venv
   .venv\Scripts\Activate.ps1
   pip install -r requirements.txt
   ```

4. Put the new photo in the folder as `source-photo.jpg`.
5. Run:

   macOS/Linux:

   ```bash
   python3 scripts/prep_photo.py source-photo.jpg
   python3 scripts/make_ascii_svg.py
   ```

   Windows:

   ```powershell
   py scripts/prep_photo.py source-photo.jpg
   py scripts/make_ascii_svg.py
   ```

6. Commit only the updated `portrait-ascii.svg`. The `.gitignore` prevents the private source photo and temporary prepared image from being uploaded.

## Safe customisation

- Edit personal information and colours in `profile_config.py`.
- Run `python scripts/make_profile_card.py` after changing card information.
- Keep the repository public, because a private profile repository will not display to visitors.
- Never add passwords, API keys, `.env` files, identity documents or private datasets.
