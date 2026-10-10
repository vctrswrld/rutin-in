# Management Habit

## Nama Project

- **RutinIn ← TERPILIH**
- RutinKan
- BiasaIn
- BiasaKan
- HabitTracker

## User Story

| ID | Requirement |
| --- | --- |
| US-01 | User bisa memiliki landing page |
| US-02 | User bisa registrasi akun |
| US-03 | User bisa verifikasi akun menggunakan email |
| US-04 | User bisa login apabila sudah memiliki akun |
| US-05 | User bisa melihat dashboard terkait kebiasaan dia |
| US-06 | User bisa memanipulasi (CRUD) habit |
| US-07 | User bisa checklist habit |
| US-08 | User bisa memanipulasi (CRUD) profile |
| US-09 | User bisa melihat achievement yang disediakan sistem |
| US-10 | User bisa memiliki level |
| US-11 | User bisa mendapatkan exp dan badge ketika suatu achievement tercapai |
| US-12 | User bisa check-in daily untuk mendapatkan streak |
| US-13 | User bisa mendapatkan streak achievement habit |
| US-14 | User bisa mendapatkan notifikasi |

# Functional Requirements

### 1. Landing Page (US 1)

| ID | Requirement |
| --- | --- |
| FR-01 | Sistem menampilkan landing page publik di `/` (hero, fitur, cara kerja, CTA daftar/login) |
| FR-02 | Landing page dapat diakses tanpa autentikasi |

### 2. Autentikasi (US 2, 3, 4, 5)

| ID | Requirement |
| --- | --- |
| FR-03 | Registrasi dengan nama, email, dan password (email unik, validasi format email dan kekuatan password) |
| FR-04 | Password disimpan dalam bentuk hash (bcrypt/argon2) |
| FR-05 | Sistem mengirim email berisi link/token verifikasi setelah registrasi |
| FR-06 | Token verifikasi memiliki masa berlaku dan sekali pakai; tersedia fitur kirim ulang verifikasi |
| FR-07 | Akun yang belum terverifikasi tidak dapat login |
| FR-08 | Login dengan email dan password, menghasilkan access token dan refresh token |
| FR-09 | Logout dan refresh token |
| FR-10 | Rate limiting pada endpoint login dan registrasi |
| FR-11 | *(Disarankan)* Lupa dan reset password melalui email |

### 3. Dashboard (US 6)

| ID | Requirement |
| --- | --- |
| FR-12 | Dashboard menampilkan habit hari ini beserta status selesai/belum |
| FR-13 | Dashboard menampilkan ringkasan: streak saat ini, level, EXP, dan progres menuju level berikutnya |
| FR-14 | Dashboard menampilkan statistik sederhana (persentase selesai, riwayat mingguan) |

### 4. Habit (US 7, 8)

| ID | Requirement |
| --- | --- |
| FR-15 | Daftar jenis habit disediakan sistem (master data, read-only bagi user) |
| FR-16 | User membuat habit dengan memilih jenis habit, nama, frekuensi/jadwal, target, dan pengingat |
| FR-17 | User dapat melihat, mengubah, dan menghapus (soft delete/arsip) habit miliknya |
| FR-18 | User hanya dapat mengakses habit miliknya sendiri |
| FR-19 | User menandai habit selesai pada hari tertentu dan dapat membatalkannya pada hari yang sama |
| FR-20 | Satu habit hanya dapat dicentang sekali per periode/hari |
| FR-21 | Pencatatan check-in menyimpan timestamp dan mengikuti zona waktu user |

### 5. Profil (US 9)

| ID | Requirement |
| --- | --- |
| FR-22 | Profil dibuat otomatis saat registrasi |
| FR-23 | User dapat melihat dan mengubah nama, avatar, zona waktu, dan preferensi notifikasi |
| FR-24 | User dapat mengganti password (wajib memasukkan password lama) |
| FR-25 | User dapat menghapus akun beserta data terkait |

### 6. Gamifikasi (US 10, 11, 12, 13, 14)

| ID | Requirement |
| --- | --- |
| FR-26 | Daftar achievement dan badge disediakan sistem (kriteria, deskripsi, hadiah EXP) |
| FR-27 | User dapat melihat achievement: terkunci/terbuka beserta progresnya |
| FR-28 | User mendapat EXP dari aksi tertentu (checklist habit, check-in harian, achievement) |
| FR-29 | Level dihitung dari total EXP berdasarkan tabel/rumus level |
| FR-30 | Level naik otomatis saat EXP mencapai ambang batas |
| FR-31 | Sistem memberi badge dan EXP ketika achievement tercapai (idempoten, tidak diberikan dua kali) |
| FR-32 | Check-in harian menambah streak; streak reset jika satu hari terlewat |
| FR-33 | Sistem menyimpan streak saat ini dan streak terpanjang, per user dan per habit |
| FR-34 | Achievement streak (mis. 3, 7, 30, 100 hari) dievaluasi otomatis |

### 7. Notifikasi (US 15)

| ID | Requirement |
| --- | --- |
| FR-35 | Notifikasi email untuk: verifikasi, pengingat habit, achievement/level up |
| FR-36 | Notifikasi di web (in-app): daftar notifikasi, penanda sudah dibaca, jumlah belum dibaca |
| FR-37 | Pengiriman notifikasi ke web secara real-time (WebSocket/SSE) atau polling |
| FR-38 | User dapat mengatur preferensi notifikasi (aktif/nonaktif per kanal) |
| FR-39 | Pengingat dijadwalkan berdasarkan jam dan zona waktu user |