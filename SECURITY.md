# Security \u0026 Privacy

## Prinsip
- Konfigurasi bot per akun, tapi **API key disimpan terpusat** (folder `config/`) atau via environment variables.
- Hindari commit secrets (token, cookies, password) ke git.

## Data yang Sensitif
- Cookies (session)
- Login credentials (jika auto-login digunakan)
- API keys (Gemini/OpenRouter/Groq/Pollinations, dll)
- Telegram bot token + chat id

## Rekomendasi Praktis
- Simpan kunci di file lokal yang di-ignore git (mis. `*.local.json`) atau ENV di VPS.
- Aktifkan limit dan quiet hours untuk mengurangi risiko.
- Gunakan akun yang sudah “warm” dan selalu monitor via Telegram alerts.

## Disclaimer
Automation dapat berisiko terhadap akun. Gunakan secara bertanggung jawab dan pahami kebijakan platform.

