# Features — FB Automation Pro

Dokumen ini fokus ke fitur yang paling membantu kerja “Facebook ops” (bukan sekadar list panjang).

## 1) Ops \u0026 Scheduling
- Scheduler berbasis `time`/`days` atau `cron` + randomize menit untuk variasi eksekusi.
- Isolasi proses per task: satu bot error tidak menjatuhkan yang lain.
- Safety limits per akun: batas run per jam/hari + quiet hours.

## 2) Multi-Account
- Setiap akun punya folder dan konfigurasi sendiri (schedule, cookies, target, dll).
- Struktur rapi untuk skalabilitas (cocok untuk agency/owner multi brand).

## 3) AI Content Engine
- Generator komentar/caption/status via Gemini/OpenRouter/Groq.
- Persona style per akun (tone friendly/professional/humorous/motivational).
- Anti repetisi: memory/log untuk mengurangi konten yang sama.

## 4) Telegram Command Center
- Notifikasi real-time (start/success/error).
- Remote control: start/stop/check status per akun dan per bot.
- Monitoring jarak jauh tanpa buka VPS.

## 5) Media Pipeline
- Folder media terpusat: `photos/` dan `videos/`.
- “Processed flow”: media yang sudah dipakai dipindahkan ke folder processed + log.
- Opsi prioritas sumber: local vs AI untuk foto/video (mudah diatur per akun).

## 6) Cookie \u0026 Session
- Auto cookie refresh (opsional login config + 2FA).
- Validasi cookies di startup.

## 7) Build Hardening (Distribusi)
- Dukungan build terenkripsi untuk deploy/distribusi agar code tidak mudah dibaca.

## Modul Bot (Ringkas)
- autolike
- confirm
- groupcomment
- timelinecomment
- videocomment
- reply
- scrape
- sharereels
- uploadreels
- updatestatus
- viewstory

