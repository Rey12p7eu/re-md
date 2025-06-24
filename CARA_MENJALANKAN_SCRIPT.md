# 🤖 Cara Menjalankan Script WhatsApp Bot Re-MD

## 📋 Deskripsi
Script ini adalah WhatsApp Bot yang dibuat dengan Node.js menggunakan library Baileys untuk WhatsApp Web API. Bot ini mendukung berbagai fitur seperti sticker, downloader, games, dan banyak lagi.

## 🔧 Persyaratan Sistem

### Untuk Termux (Android):
```bash
# Update dan upgrade paket
pkg upgrade && pkg update

# Install dependensi yang diperlukan
pkg install git -y
pkg install nodejs -y
pkg install ffmpeg -y
pkg install imagemagick -y
```

### Untuk Windows/VPS/RDP:
1. Download dan Install Git: https://git-scm.com/downloads
2. Download dan Install NodeJS: https://nodejs.org/en/download
3. Download dan Install FFmpeg: https://ffmpeg.org/download.html
4. Download dan Install ImageMagick: https://imagemagick.org/script/download.php

### Untuk Ubuntu/Linux:
```bash
# Update sistem
sudo apt update && sudo apt upgrade

# Install dependensi
sudo apt install git nodejs npm ffmpeg imagemagick -y

# Install Node.js versi terbaru (opsional)
curl -fsSL https://deb.nodesource.com/setup_current.x | sudo -E bash -
sudo apt install -y nodejs
```

## 📥 Instalasi

### 1. Clone Repository
```bash
git clone https://github.com/Rlxfly/re-md
cd re-md
```

### 2. Install Dependencies
Ada beberapa cara untuk menginstall dependencies karena ada konflik versi:

#### Opsi 1: Install Normal
```bash
npm install
```

#### Opsi 2: Jika ada error, gunakan legacy peer deps
```bash
npm install --legacy-peer-deps
```

#### Opsi 3: Jika masih error, gunakan force
```bash
npm install --force
```

#### Opsi 4: Gunakan Yarn (alternatif)
```bash
# Install yarn terlebih dahulu
npm install -g yarn

# Install dependencies dengan yarn
yarn install
```

### 3. Konfigurasi Bot
Edit file `config.js` untuk mengatur:
- Nomor owner/admin
- API keys (jika diperlukan)
- Pengaturan lainnya

```javascript
global.owner = [
  ['6288888888888', 'Nama Owner', true]
]
```

## 🚀 Cara Menjalankan Script

### Metode 1: Menjalankan Langsung
```bash
node .
```

### Metode 2: Menggunakan NPM Script
```bash
npm start
```

### Metode 3: Dengan Argumen Khusus
```bash
# Mode self (hanya merespon owner)
node . --self

# Mode private chat saja
node . --pconly

# Mode group saja
node . --gconly

# Dengan prefix custom
node . --prefix .!#

# Mode server (untuk hosting)
node . --server

# Auto read pesan
node . --autoread

# Auto clear tmp folder
node . --autocleartmp
```

## 📱 Cara Scan QR Code

1. Jalankan script dengan salah satu metode di atas
2. Tunggu hingga QR code muncul di terminal
3. Buka WhatsApp di HP
4. Pergi ke **Pengaturan** > **Perangkat Tertaut**
5. Klik **Tautkan Perangkat**
6. Scan QR code yang muncul di terminal
7. Bot akan mulai berjalan setelah berhasil terhubung

## 🔧 Troubleshooting

### Error: Cannot find package 'yargs'
```bash
# Install dependencies yang hilang
npm install yargs cfonts chalk --save
```

### Error: ERESOLVE unable to resolve dependency tree
```bash
# Gunakan salah satu opsi berikut:
npm install --legacy-peer-deps
# atau
npm install --force
# atau
rm -rf node_modules package-lock.json
npm install --legacy-peer-deps
```

### Error: Cannot find package '@james-bennett-295/writefile'
```bash
# Package ini tidak tersedia, gunakan solusi berikut:
# 1. Buat package.json minimal dengan dependencies penting saja
# 2. Install dependencies secara bertahap
# 3. Atau gunakan yarn sebagai alternatif

# Solusi 1: Install dependencies penting dulu
npm install yargs cfonts chalk @adiwajshing/baileys qrcode-terminal lowdb lodash ws --legacy-peer-deps

# Solusi 2: Gunakan yarn
npm install -g yarn
yarn install
```

### Bot berhasil start tapi ada error dependencies
```bash
# Install dependencies yang hilang satu per satu
npm install lodash ws syntax-error

# Atau install semua dependencies dengan force
npm install --force
```

### Bot tidak merespon
1. Pastikan nomor sudah terdaftar sebagai owner di `config.js`
2. Cek koneksi internet
3. Restart bot dengan `Ctrl+C` lalu jalankan lagi

### QR Code tidak muncul
```bash
# Hapus session lama
rm -rf sessions
# Jalankan ulang bot
node .
```

## 📂 Struktur File Penting

```
re-md/
├── index.js          # Entry point utama
├── main.js           # Logic utama bot
├── config.js         # Konfigurasi bot
├── package.json      # Dependencies
├── handler.js        # Handler pesan
├── plugins/          # Folder plugin/fitur
├── lib/              # Library pendukung
└── sessions/         # Data session WhatsApp
```

## 🎯 Fitur Utama

- ✅ Multi-device support
- ✅ Sticker maker
- ✅ Downloader (YouTube, TikTok, Instagram, dll)
- ✅ Games (TicTacToe, dll)
- ✅ Group management
- ✅ Auto welcome/leave
- ✅ Leveling system
- ✅ Dan banyak lagi...

## 🔄 Update Bot

```bash
# Pull update terbaru
git pull origin main

# Install dependencies baru (jika ada)
npm install --legacy-peer-deps

# Restart bot
node .
```

## 🆘 Bantuan Tambahan

Jika mengalami masalah:
1. Baca dokumentasi di README.md
2. Cek issue di GitHub repository
3. Join grup diskusi: https://chat.whatsapp.com/J26yYsYdxLBJdbKdDrddEv

## ⚠️ Catatan Penting

1. **Backup session**: Selalu backup folder `sessions` untuk menghindari scan ulang QR
2. **Jangan share session**: File session berisi data login WhatsApp Anda
3. **Update berkala**: Selalu update bot untuk mendapat fitur dan perbaikan terbaru
4. **Gunakan dengan bijak**: Jangan spam atau melanggar ToS WhatsApp

## ✅ Testing Bot Functionality

### 1. Verifikasi Bot Startup
```bash
# Jalankan bot dan periksa apakah muncul tampilan ASCII art
node .

# Jika berhasil, Anda akan melihat:
# - ASCII art "Lightweight WhatsApp Bot"
# - Pesan "re-md By @Rlxfly"
# - QR code untuk scan
```

### 2. Test Basic Commands
Setelah bot terhubung, test perintah dasar:
- `.menu` - Menampilkan menu utama
- `.ping` - Test response time
- `.owner` - Info owner bot

### 3. Verifikasi Fitur Utama
- Sticker: Kirim gambar dengan caption `.s`
- Download: `.ytmp3 [url]` untuk download audio YouTube
- Info: `.botinfo` untuk informasi bot

## 🎉 Selamat!

Bot WhatsApp Anda sekarang sudah siap digunakan! Kirim pesan `.menu` ke bot untuk melihat daftar perintah yang tersedia.

---
*Dibuat dengan ❤️ oleh komunitas WhatsApp Bot Indonesia*
