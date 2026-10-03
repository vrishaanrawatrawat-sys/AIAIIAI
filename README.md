# linkedin_profile_ai

A local desktop assistant for preparing the user's own LinkedIn profile information. It parses supported profile files, normalizes known fields, previews deterministic mappings, and can fill high-confidence visible form fields for the user to review. It never submits a form or performs messaging, job applications, endorsements, or other consequential actions.

## Run

Python 3.10+ with Tk available:

```powershell
cd linkedin_profile_ai
python -m pip install -r requirements.txt
python -m playwright install chromium
python app.py
```

Run the offline tests with `python -m unittest discover -s tests -v`. The PDF parsing test uses a mock reader; to parse actual PDF files install requirements. DOCX extraction reads document text locally. Image-only/scanned PDFs need OCR and are not supported.

## Use

Import PDF, DOCX, TXT, Markdown, or JSON. Review/edit the structured JSON on the Profile tab and save locally if desired. Open a user-authorized LinkedIn page, detect visible fields, inspect Mapping Preview, then use Fill Form. Fill Form only writes mappings with confidence at least 0.90; uncertain/missing fields stay untouched. Review the browser page yourself. The app has no submit function; it does not inspect credentials or scrape private data.

The mock page is `mock_linkedin/profile_form.html`; use a local static server to open it if desired. Browser support uses Playwright Chromium and is optional for the offline core. LinkedIn DOM compatibility is not guaranteed and has not been verified against LinkedIn. Do not use this tool to bypass authentication, CAPTCHA, anti-bot controls, or rate limits.

Profile contents remain on the local machine; there is no networked AI service. Clear profile data removes the current in-memory display and mappings. Saved files are only created when you explicitly choose Save profile.
