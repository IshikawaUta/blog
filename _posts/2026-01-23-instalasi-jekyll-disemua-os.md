---
layout: post
title: "Panduan Lengkap Instalasi Jekyll di Windows, macOS, dan Linux"
date: 2026-01-23 08:00:00 +0700
categories: tutorial linux
---

Jekyll adalah generator situs statis (SSG) berbasis **Ruby**. Karena berbasis Ruby, langkah utama di semua OS adalah memastikan Ruby dan pengelola paketnya (RubyGems) terpasang dengan benar.

---

## 1. Persiapan Berdasarkan Sistem Operasi

### 🍎 macOS

macOS biasanya sudah memiliki Ruby, namun disarankan menggunakan versi terbaru via **Homebrew**.

1. Install Homebrew (jika belum):

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
2. Install Ruby: `brew install ruby`
3. Update PATH di shell profil kamu (`.zshrc` atau `.bash_profile`):

```bash
if [ -d "/usr/local/opt/ruby/bin" ]; then
  export PATH=/usr/local/opt/ruby/bin:$PATH
  export PATH=`gem env user_dir`/bin:$PATH
fi
```



### 🐧 Linux (Ubuntu/Debian)

1. Update package manager: `sudo apt update`
2. Install Ruby dan dependencies:

```bash
sudo apt install ruby-full build-essential zlib1g-dev
```
3. Konfigurasi path agar gem tidak memerlukan `sudo`:

```bash
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```



### 🖥️ Windows

Cara termudah adalah menggunakan **RubyInstaller for Windows**.

1. Download di [rubyinstaller.org](https://rubyinstaller.org/downloads/). Pilih versi **Ruby+Devkit**.
2. Jalankan installer dan ikuti instruksi.
3. Di akhir instalasi, centang "Run 'ridk install'" untuk memasang MSYS2 (diperlukan untuk ekstensi C). Pilih opsi nomor **3** (MSYS2 and MINGW development toolchain).

---

## 2. Instalasi Jekyll dan Bundler

Setelah Ruby siap, buka terminal (atau Command Prompt/PowerShell di Windows) dan jalankan:

```bash
gem install jekyll bundler
```

Periksa apakah instalasi berhasil:

```bash
jekyll -v
```

---

## 3. Membuat Website Jekyll Baru

Ikuti langkah-langkah ini untuk membangun situs pertama kamu:

1. **Buat Projek Baru**

```bash
jekyll new my-awesome-site
```

*Perintah ini akan membuat folder bernama `my-awesome-site` dengan struktur standar Jekyll.*
2. **Masuk ke Direktori**

```bash
cd my-awesome-site
```

3. **Build dan Jalankan Server Lokal**

```bash
bundle exec jekyll serve
```

4. **Buka Browser**
Akses website kamu di: `http://localhost:4000`

---

## 📂 Struktur Folder Jekyll

* `_config.yml`: Pengaturan utama situs (judul, deskripsi, dll).
* `_posts`: Tempat kamu menulis konten blog (format Markdown).
* `_site`: Hasil akhir website (jangan diedit manual, folder ini akan terhapus saat build).
* `index.markdown`: Halaman utama situs kamu.

---

## 💡 Tips Tambahan

* **Live Reload:** Gunakan `bundle exec jekyll serve --livereload` agar browser otomatis refresh saat kamu menyimpan perubahan file.
* **Error Windows:** Jika muncul error terkait `tzinfo-data`, jalankan `gem install tzinfo-data` dan tambahkan `gem "tzinfo-data", platforms: [:mingw, :mswin, :x64_mingw, :jruby]` ke dalam file `Gemfile`.

---
<a href="https://ishikawauta.github.io/blog/"><button style="margin-top: 2rem;">Kembali</button></a>