
# PiVerse AI Proxy (Node/Express)

Biztonságos köztes szerver a mobil app és az OpenAI API között.

## Telepítés

```bash
npm i
cp .env.example .env   # töltsd ki az OPENAI_API_KEY-t
npm run start
```

Alapértelmezés: `http://localhost:3000`

## Környezeti változók

Lásd: `.env.example`

- `OPENAI_API_KEY` – kötelező
- `ALLOW_ORIGIN` – CORS origin (pl. `https://app.piverse.hu`), devben `*` is lehet
- `CLIENT_KEYS` – vesszővel elválasztott engedélyezett klienskulcsok (ha üres, nem ellenőrzünk)
- `RATE_LIMIT` – kérelmek/perc

## Endpointok

- `POST /ai/chat` `{ "prompt": "..." }` → `{ "answer": "..." }`
- `POST /ai/support` `{ "prompt": "..." }` → `{ "answer": "..." }`
- `POST /ai/help` `{ "prompt": "..." }` → `{ "answer": "..." }`
- `POST /ai/image-search` multipart `image` → `{ "answer": "..." }`
- `POST /ai/transcribe` multipart `file` → `{ "text": "..." }`

## Deploy tippek

- Vercel/Render/Cloud Run: Node 18+, állítsd be az env változókat.
- CORS: állítsd `ALLOW_ORIGIN`-t az app domainjeidre.
- Biztonság: használd a `CLIENT_KEYS`-t vagy JWT-t. Adj per-user kvótát és naplózást.
