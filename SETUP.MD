# Panduan Lengkap Instalasi dan Setup FacebookPro Blaster

Selamat datang! Dokumen ini akan memandu Anda langkah demi langkah untuk menyiapkan dan menjalankan FacebookPro Blaster di komputer Windows atau VPS Linux.

---

## Daftar Isi
1.  [Prasyarat](#1-prasyarat)
2.  [Menyiapkan Folder & Konfigurasi](#2-menyiapkan-folder--konfigurasi)
3.  [Cara Mendapatkan Kunci API](#3-cara-mendapatkan-kunci-api)
4.  [Instalasi & Menjalankan Bot di Windows](#4-instalasi--menjalankan-bot-di-windows-lokal)
5.  [Instalasi & Menjalankan Bot di VPS Linux](#5-instalasi--menjalankan-bot-di-vps-linux)
6.  [Troubleshooting](#6-troubleshooting)

---

### 1. Prasyarat

Sebelum memulai, pastikan Anda sudah memiliki:
- **Node.js:** Versi 18.x atau yang lebih baru. Anda bisa mengunduhnya dari [nodejs.org](https://nodejs.org/).
- **Text Editor:** Program untuk mengedit file teks, seperti [Visual Studio Code](https://code.visualstudio.com/), Notepad++, atau bahkan Notepad bawaan Windows.
- **Akun Facebook:** Siapkan akun yang akan digunakan untuk bot.
- **Kunci Lisensi:** Anda akan mendapatkan kunci lisensi dari penjual setelah pembelian.

---

### 2. Menyiapkan Folder & Konfigurasi

Struktur bot ini berbasis folder. Setiap akun Facebook yang ingin Anda otomatisasi harus memiliki foldernya sendiri di dalam direktori `accounts`.

1.  **Ekstrak File ZIP:** Ekstrak file FacebookPro Blaster ZIP yang Anda terima ke lokasi yang Anda inginkan (misalnya, `D:\FacebookProBlaster`).
2.  **Buka Folder `accounts`:** Di dalamnya, Anda akan melihat contoh folder.
3.  **Buat Folder Akun Anda:** Buat folder baru untuk setiap akun Facebook Anda. Beri nama yang mudah diingat, misalnya `account1` atau `account2`.

Di dalam setiap folder akun (misal, `accounts/account1/`), Anda perlu membuat dan mengisi beberapa file `.txt`. File-file ini adalah tempat Anda mengontrol apa yang dilakukan bot.

**File-file Konfigurasi Utama (wajib diisi sesuai kebutuhan):**
*   `cookies.json`: **(Sangat Penting)** File ini akan dibuat secara otomatis oleh bot saat pertama kali login. **Jangan diubah secara manual.**
*   `facebook_login.json`: Isi dengan kredensial login akun Facebook Anda dalam format JSON.
    ```json
    {
      "email": "email_facebook_anda",
      "password": "password_facebook_anda",
      "fa_key": "kunci_2fa_anda_jika_ada"
    }
    ```
*   `comments.txt`: Isi dengan daftar komentar yang akan digunakan bot, **satu komentar per baris**.
    ```
    Keren banget postingannya!
    Mantap, sangat bermanfaat.
    Terima kasih infonya.
    ```
*   `target_groups.txt`: Isi dengan URL lengkap grup-grup Facebook yang menjadi target, **satu URL per baris**.
    ```
    https://www.facebook.com/groups/1234567890
    https://www.facebook.com/groups/0987654321
    ```
*   `gemini_keys.txt`: Isi dengan kunci API Google Gemini Anda untuk fitur-fitur yang menggunakan AI, **satu kunci per baris**.

---

### 3. Cara Mendapatkan Kunci API

FacebookPro Blaster menggunakan beberapa layanan eksternal yang memerlukan Kunci API.

#### A. Kunci API Google Gemini (Untuk Komentar AI)
1.  Buka [Google AI Studio](https://aistudio.google.com/app/apikey).
2.  Login dengan akun Google Anda.
3.  Klik **"Create API key in new project"**.
4.  Salin kunci yang muncul dan tempelkan ke dalam file `gemini_keys.txt`.

#### B. Notifikasi Telegram
Agar bot bisa mengirim notifikasi, Anda perlu mendapatkan **Bot Token** dan **Chat ID**.
1.  **Mendapatkan Bot Token:**
    *   Di aplikasi Telegram, cari akun bernama **`@BotFather`**.
    *   Mulai percakapan dengan mengetik `/start`.
    *   Ketik `/newbot` untuk membuat bot baru.
    *   Ikuti instruksinya untuk memberi nama bot Anda.
    *   Setelah selesai, BotFather akan memberi Anda sebuah **token**. Salin token ini.
2.  **Mendapatkan Chat ID:**
    *   Cari akun bernama **`@userinfobot`**.
    *   Mulai percakapan dengannya. Bot ini akan langsung menampilkan **Chat ID** Anda. Salin ID ini.
3.  **Masukkan ke Konfigurasi:**
    *   Buka file `config/telegram.json` dan masukkan token serta ID yang sudah Anda salin.

---

### 4. Instalasi & Menjalankan FacebookPro Blaster di Windows (Lokal)

Metode ini cocok untuk penggunaan pribadi atau pengujian.

1.  **Buka Command Prompt (CMD) atau PowerShell:**
    *   Arahkan ke folder tempat Anda mengekstrak FacebookPro Blaster (misalnya `D:\FacebookProBlaster`). Caranya, di File Explorer, klik kanan di dalam folder sambil menekan tombol `Shift`, lalu pilih "Open PowerShell window here" atau "Open command window here".
2.  **Instal Dependensi:**
    *   Jalankan perintah berikut dan tunggu hingga selesai:
        ```bash
        npm install --production
        ```
3.  **Jalankan Bot:**
    *   Anda dapat menjalankan tugas spesifik dengan perintah `node dist/bot/executor.js run <NAMA_TUGAS> <NAMA_AKUN>`.
    *   **Contoh:** Untuk menjalankan tugas `autolike` pada akun `account1`:
        ```bash
        node dist/bot/executor.js run autolike account1
        ```

---

### 5. Instalasi & Menjalankan FacebookPro Blaster di VPS (Linux)

Metode ini direkomendasikan agar FacebookPro Blaster bisa berjalan 24/7.

1.  **Unggah dan Ekstrak File:**
    *   Unggah file ZIP FacebookPro Blaster ke VPS Anda dan ekstrak.
2.  **Buka Terminal:**
    *   Arahkan ke folder bot Anda.
3.  **Instal Dependensi:**
    *   Jalankan perintah:
        ```bash
        npm install --production
        ```
4.  **Instal PM2 (Process Manager):**
    *   PM2 adalah tool yang akan menjaga bot Anda tetap berjalan. Instal secara global:
        ```bash
        npm install -g pm2
        ```
5.  **Jalankan FacebookPro Blaster dengan PM2:**
    *   Gunakan file konfigurasi yang sudah disediakan untuk memulai semua layanan FacebookPro Blaster (scheduler, telegram, dll.):
        ```bash
        pm2 start dist/ecosystem.config.js
        ```
6.  **Perintah PM2 yang Berguna:**
    *   Melihat semua proses FacebookPro Blaster yang berjalan: `pm2 list`
    *   Melihat log (aktivitas) FacebookPro Blaster secara real-time: `pm2 logs`
    *   Menghentikan semua proses FacebookPro Blaster: `pm2 stop all`
    *   Menghidupkan ulang semua proses FacebookPro Blaster: `pm2 restart all`
    *   Menyimpan konfigurasi agar FacebookPro Blaster otomatis berjalan saat VPS restart: `pm2 save` lalu `pm2 startup`.

---

### 6. Troubleshooting

*   **Error `Cannot find module`:** Pastikan Anda sudah menjalankan `npm install --production` dan Anda menjalankan perintah dari direktori yang benar.
*   **FacebookPro Blaster Gagal Login:** Periksa kembali `facebook_login.json`. Pastikan email, password, dan kunci 2FA (jika ada) sudah benar.
*   **Notifikasi Telegram Tidak Masuk:** Pastikan Bot Token dan Chat ID di `config/telegram.json` sudah benar.

Jika Anda mengalami masalah lain, jangan ragu untuk menghubungi kembali penjual. Selamat menggunakan FacebookPro Blaster!
