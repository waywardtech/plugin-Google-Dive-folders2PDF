# Drive PDF Consolidator

Single-file browser tool that signs in with Google, lets you pick files and folders from Google Drive, generates a PDF per file (with a cover page showing filename, folder, type, page count and generated time), splits output into numbered volumes, and optionally consolidates everything into one PDF.

- `gdrive_pdf_generator.html` — the whole app. Open it from a web origin (not `file://`).

## Features

- Google sign-in and Drive browsing with drill-down folders and search
- Select files and/or whole folders (folders are expanded recursively)
- Inputs: PDF, Google Docs/Sheets/Slides/Drawings (exported to PDF), JPEG, PNG. Other types are skipped and listed.
- Pages per volume: 200–999. Volumes are named `Name_001.pdf` … `Name_999.pdf`; a file that fits in one volume has no suffix.
- Consolidated PDF (also split into volumes), with a chosen output name
- Save to a Drive folder (picker) or download to this computer
- Optional clean-up of generated per-file PDFs after consolidating

## Setup (one time)

1. In Google Cloud Console, create a project and enable the **Google Drive API**.
2. OAuth consent screen: External, add your Google account as a test user. Scopes: Drive, openid, email, profile.
3. Credentials → Create credentials → **OAuth client ID** → Web application.
4. Authorised JavaScript origins: the origin the page is served from, e.g. `https://waywardtech.github.io` (no path). `file://` is not accepted by Google.
5. Open the page and paste the client ID. It is stored in this browser only. You can also set `CONFIG.clientId` in the file.

## Limits

- Everything runs in the browser. Very large selections use a lot of memory.
- Google's PDF export is capped at 10 MB per file.
- The `drive` scope is broad and is classed as restricted by Google; personal use in testing mode works, public use needs verification.
