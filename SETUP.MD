# FacebookPro Blaster - Setup Guide (Preview)
<div align="right">
  <a href="#english"><strong>EN</strong> English</a> | <a href="#indonesian"><strong>ID</strong> Bahasa Indonesia</a>
</div>

---

<div id="english">

# Setup Guide (Preview) for FacebookPro Blaster

Welcome! This document is a **preview** of how setup works in the full version. This repository does not ship the operational build.

➡️ Get the full package (download + license): https://facebookpro.gt.tc/

---

## Table of Contents
1.  [Prerequisites](#1-prerequisites)
2.  [Setting Up Folders & Configuration](#2-setting-up-folders--configuration)
3.  [How to Get API Keys](#3-how-to-get-api-keys)
4.  [Installation & Running Bot on Windows](#4-installation--running-bot-on-windows-local)
5.  [Installation & Running Bot on Linux VPS](#5-installation--running-bot-on-linux-vps)
6.  [Troubleshooting](#6-troubleshooting)

---

### 1. Prerequisites

Before you begin, make sure you have:
- **Node.js:** Version 18.x or newer. You can download it from [nodejs.org](https://nodejs.org/).
- **Text Editor:** A program for editing text files, such as [Visual Studio Code](https://code.visualstudio.com/), Notepad++, or even the built-in Windows Notepad.
- **Facebook Account:** Prepare the account you will use for the bot.
- **License Key:** You will receive a license key from the seller after purchase.

---

### 2. Folder Structure & Configuration (Per Account)

This bot is folder-based. Each Facebook account you want to automate must have its own folder inside the `accounts` directory.

1.  **Extract ZIP File:** Extract the FacebookPro Blaster ZIP file you received to your desired location (for example, `D:\FacebookProBlaster`).
2.  **Open the `accounts` Folder:** Inside, you will see example folders.
3.  **Create Your Account Folders:** Create a new folder for each of your Facebook accounts. Give them memorable names, such as `account1` or `account2`.

Inside each account folder (e.g., `accounts/account1/`), you need to create and fill in several `.txt` files. These files are where you control what the bot does.

**Main Configuration Files (must be filled as needed):**
*   `cookies.json`: **(Very Important)** This file will be created automatically by the bot when you first log in. **Do not edit manually.**
*   `facebook_login.json`: Fill with your Facebook account login credentials in JSON format.
    ```json
    {
      "email": "your_facebook_email",
      "password": "your_facebook_password",
      "fa_key": "your_2fa_key_if_any"
    }
    ```
*   `comments.txt`: Fill with a list of comments that the bot will use, **one comment per line**.
    ```
    Great post!
    Awesome, very useful.
    Thanks for the info.
    ```
*   `target_groups.txt`: Fill with the complete URLs of the target Facebook groups, **one URL per line**.
    ```
    https://www.facebook.com/groups/1234567890
    https://www.facebook.com/groups/0987654321
    ```
*   `gemini_keys.txt`: Fill with your Google Gemini API keys for features that use AI, **one key per line**.

---

### 3. API Keys (Centralized)

FacebookPro Blaster uses external services that require API Keys. In the full version, keys are stored **centrally** in `config/` (or via ENV) while bot settings remain **per account**.

#### A. Google Gemini API Key (For AI Comments)
1.  Open [Google AI Studio](https://aistudio.google.com/app/apikey).
2.  Login with your Google account.
3.  Click **"Create API key in new project"**.
4.  Copy the key that appears and paste it into the `gemini_keys.txt` file.

#### B. Telegram Notifications
To enable the bot to send notifications, you need to get a **Bot Token** and **Chat ID**.
1.  **Getting Bot Token:**
    *   In the Telegram app, search for an account named **`@BotFather`**.
    *   Start a conversation by typing `/start`.
    *   Type `/newbot` to create a new bot.
    *   Follow the instructions to name your bot.
    *   When finished, BotFather will give you a **token**. Copy this token.
2.  **Getting Chat ID:**
    *   Search for an account named **`@userinfobot`**.
    *   Start a conversation with it. This bot will immediately display your **Chat ID**. Copy this ID.
3.  **Enter into Configuration:**
    *   Open the `config/telegram.json` file and enter the token and ID you have copied.

---

### 4. Running on Windows (Local)

This method is suitable for personal use or testing.

1.  **Open Command Prompt (CMD) or PowerShell:**
    *   Navigate to the folder where you extracted FacebookPro Blaster (for example `D:\FacebookProBlaster`). To do this, in File Explorer, right-click inside the folder while holding the `Shift` key, then select "Open PowerShell window here" or "Open command window here".
2.  **Install Dependencies:**
    *   Run the following command and wait until it's complete:
        ```bash
        npm install --production
        ```
3.  **Run the Bot:**
    *   You can run specific tasks with the command `node dist/bot/executor.js run <TASK_NAME> <ACCOUNT_NAME>`.
    *   **Example:** To run the `autolike` task on the `account1` account:
        ```bash
        node dist/bot/executor.js run autolike account1
        ```

---

### 5. Running on VPS (Linux)

This method is recommended so that FacebookPro Blaster can run 24/7.

1.  **Upload and Extract Files:**
    *   Upload the FacebookPro Blaster ZIP file to your VPS and extract it.
2.  **Open Terminal:**
    *   Navigate to your bot folder.
3.  **Install Dependencies:**
    *   Run the command:
        ```bash
        npm install --production
        ```
4.  **Install PM2 (Process Manager):**
    *   PM2 is a tool that will keep your bot running. Install it globally:
        ```bash
        npm install -g pm2
        ```
5.  **Run FacebookPro Blaster with PM2:**
    *   Use the provided configuration file to start all FacebookPro Blaster services (scheduler, telegram, etc.):
        ```bash
        pm2 start dist/ecosystem.config.js
        ```
6.  **Useful PM2 Commands:**
    *   View all running FacebookPro Blaster processes: `pm2 list`
    *   View FacebookPro Blaster logs (activity) in real-time: `pm2 logs`
    *   Stop all FacebookPro Blaster processes: `pm2 stop all`
    *   Restart all FacebookPro Blaster processes: `pm2 restart all`
    *   Save configuration so FacebookPro Blaster automatically runs when VPS restarts: `pm2 save` then `pm2 startup`.

---

### 6. Troubleshooting

*   **Error `Cannot find module`:** Make sure you have run `npm install --production` and you are running the command from the correct directory.
*   **FacebookPro Blaster Failed to Login:** Check `facebook_login.json` again. Make sure email, password, and 2FA key (if any) are correct.
*   **Telegram Notifications Not Arriving:** Make sure Bot Token and Chat ID in `config/telegram.json` are correct.

If you need help onboarding, contact support after purchase.

</div>

---

<div id="indonesian">

# Panduan Setup (Preview) FacebookPro Blaster

Selamat datang! Dokumen ini adalah **preview** alur setup pada versi full. Repo ini tidak menyertakan build operasional.

➡️ Dapatkan paket full (download + lisensi): https://facebookpro.gt.tc/

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

### 2. Struktur Folder & Konfigurasi (Per Akun)

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

### 3. Kunci API (Terpusat)

FacebookPro Blaster menggunakan layanan eksternal yang memerlukan Kunci API. Di versi full, key disimpan **terpusat** di folder `config/` (atau ENV) sedangkan setting bot tetap **per akun**.

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

</div>
