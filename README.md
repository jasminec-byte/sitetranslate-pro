# SiteTranslate Pro — runnable prototype

Responsive installable web prototype for English, Brazilian Portuguese, and Simplified Mandarin Chinese construction communication.

## Run locally

```bash
cd sitetranslate-pro
python3 -m http.server 8000
```

Open http://localhost:8000. On another device, deploy the folder to an HTTPS static host; microphone and PWA features require a secure context.

## Features

- Offline exact-match glossary and common jobsite phrase translations (not a general machine translator)
- Browser speech recognition where supported and text-to-speech where available
- Photo attachments with notes (no automatic photo interpretation)
- Device-local history, JSON export, and delete
- Responsive interface and basic service worker caching
- Optional AI translation backend

## Optional AI translation backend

```bash
pip install fastapi uvicorn openai
export OPENAI_API_KEY='your-secret-key'
export ALLOWED_ORIGINS='http://localhost:8000'
uvicorn server:app --host 127.0.0.1 --port 8001
```

In app Settings, enter `http://localhost:8001` when testing on the same machine. For remote clients, deploy backend behind HTTPS and configure `ALLOWED_ORIGINS` to your exact frontend origin. Never put your API key in client-side code. Check the OpenAI SDK/model availability and pricing for your account before deployment.

## Production gaps

This is a functional MVP prototype, not a store-ready native app. For production: authentication, multi-tenant project storage, database and encrypted object storage, image analysis endpoint, server-side speech recognition, streaming voice, audit logs, privacy policies, rate limiting, billing, proper iOS/Android packaging, and human validation for safety-critical translations. Browser localStorage is limited and not suitable for large photo libraries. PWA install support varies by browser; the manifest currently has no app icons.
