# TruthLens Full-Stack Chrome Extension Prototype

This ZIP contains BOTH parts:
- `extension/` — Chrome extension user interface and webpage text extraction.
- `backend/` — Node.js server that securely calls Gemini. Your Gemini API key stays in the backend `.env` file, not in the extension.

## Requirements
- Google Chrome
- Node.js 18+ (recommended current LTS)
- Gemini API key from Google AI Studio: https://aistudio.google.com/app/apikey

## A. Configure and start backend (do this first)
1. Extract this ZIP to a normal folder.
2. Open the extracted `backend` folder in VS Code.
3. Open Terminal in VS Code.
4. Run:
   ```bash
   npm install
   ```
5. Copy `.env.example` and rename the copy to `.env`.
6. Open `.env` and replace `PASTE_YOUR_GEMINI_API_KEY_HERE` with your own Gemini API key. Do not share this file or upload it to GitHub.
7. Start the backend:
   ```bash
   npm start
   ```
8. Keep this terminal running. Open `http://localhost:3000/health` in Chrome; it should show a JSON status with `"status":"ok"`.

## B. Load Chrome extension
1. In Chrome, open `chrome://extensions`.
2. Turn on Developer mode.
3. Click **Load unpacked**.
4. Select the `extension` folder inside the extracted TruthLens folder.
5. Open a normal website with a policy/terms page.
6. Click the TruthLens extension icon.
7. Select category, language and analysis type, then click **Analyze with Gemini**.

## Included categories
Privacy Policy; Terms & Conditions; Refund & Return Policy; Cancellation Policy; Subscription Policy; Shipping & Delivery Policy; Payment Policy; User Agreement; Cookie Policy; Data Protection Policy.

## Included analysis types
Simple summary; Clause-by-clause analysis; Hidden charges analysis.

## How the data flows
Webpage -> Chrome extension extracts visible text -> local Node.js backend -> Gemini API -> backend returns analysis -> extension displays result.

## Important limitations
- This is a local development prototype. It is not deployed online; the backend must be running on your computer while you use the extension.
- The extension reads ordinary webpages only. Chrome internal pages and some protected pages cannot be read. Paste text manually if needed.
- Extracted text is limited to 90,000 characters. Dynamic content, PDFs and scanned documents may need manual copy/paste or a future PDF/OCR module.
- Gemini receives the extracted webpage text. Do not submit sensitive content unless you are comfortable sending it to Google.
- AI can miss legal details. Verify important terms and charges against the original document. This is not legal advice.
- For a public release, deploy the backend on HTTPS hosting and add authentication, rate limits, request-size limits, and appropriate privacy controls.
