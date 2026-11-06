# Website 5,74 A

Website kelas satu halaman (HOME · TENTANG · MEDIA · STRUKTUR · ANGGOTA · PRESTASI) dengan login,
galeri foto, struktur kelas bergaya neon, 32 profil anggota, dan panel admin.
Statis (HTML + CSS + JS), bisa langsung di-deploy ke Vercel.

## 1. Coba dulu (mode demo)
Buka `index.html` di browser (atau jalankan `npx serve`). Daftar akun, **akun pertama otomatis jadi admin**.
Di mode demo data hanya tersimpan di browser itu sendiri. Agar dipakai bersama satu kelas, lanjut ke langkah 2.

## 2. Hubungkan database (Supabase, gratis) agar semua teman bisa login & berbagi data
1. Buat project di https://supabase.com
2. Buka **SQL Editor** → tempel isi `supabase.sql` → **Run**
3. **Authentication → Providers → Email** → matikan **Confirm email** (supaya teman bisa langsung masuk)
4. **Project Settings → API** → salin **Project URL** dan **anon public key** ke `config.js`
5. Buka website, daftar akun kamu, lalu jadikan admin lewat SQL Editor:
   ```sql
   update profiles set role = 'admin'
   where id = (select id from auth.users where email = 'EMAIL_KAMU@gmail.com');
   ```
6. Login ulang. Menu **ADMIN** muncul di navbar.

## 3. Isi website lewat menu Admin
- **Info Website**: deskripsi kelas, kalimat halaman depan, jumlah laki-laki/perempuan, link IG / TikTok / YouTube,
  foto latar halaman depan, dan foto kelas (bagian Tentang).
- **Daftar Anggota**: tempel 32 nama sekaligus (1 nama per baris), lalu isi username tiap anak.
- **Struktur**: buka bagian Struktur, ketuk kotak jabatan, ketik nama (pilih dari daftar anggota agar terhubung ke profilnya).
- **Pengguna**: jadikan teman sebagai admin.

Foto latar bisa juga ditaruh sebagai file `assets/hero.jpg` dan `assets/about.jpg` di dalam folder ini.

## 4. Deploy ke Vercel
- Upload folder ini ke GitHub, lalu di vercel.com pilih **Add New → Project → Import**. Framework: *Other*. Tanpa build command.
- Atau lewat CLI: `npm i -g vercel` lalu jalankan `vercel` di dalam folder ini.

## Hak akses
- **Anggota**: unggah foto & prestasi; hanya bisa menghapus miliknya sendiri.
- **Admin**: bisa menghapus apa pun, edit profil anggota, atur struktur, link sosmed, dan peran pengguna.
