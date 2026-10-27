# LAPORAN PRAKTIKUM DESAIN WEB A
## Pertemuan 7: HTML Form Dasar dan Landing Page Responsif
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![Status](https://img.shields.io/badge/Status-Selesai-success)

---

## 📋 Identitas Praktikan

| | |
|---|---|
| **Nama** | Ilham Baihaqi |
| **NIM** | 4525210029 |
| **Program Studi** | Teknik Informatika |
| **Fakultas** | Teknik |
| **Universitas** | Universitas Pancasila |
| **Mata Kuliah** | Praktikum Desain Web A |
| **Pertemuan** | 7 |

---

## 1. Tujuan Praktikum

1. Memahami fungsi *form* sebagai antarmuka input dan cara kerja atribut `action` serta `method`.
2. Menggunakan tipe input dasar: `text`, `email`, `password`, `number`, `date`, beserta `select` dan `textarea`.
3. Menghubungkan `<label>` dengan kontrol input melalui atribut `for` dan `id`.
4. Membedakan tiga jenis *button*: `submit`, `reset`, dan `button`.
5. Membangun ulang halaman profil Arunika Studio menjadi dua *file* (`index.html` dan `style.css`) dengan *box model*, *class* reusable, dan *media query*.
6. Mendokumentasikan hasil tampilan desktop dan mobile.

---

## 2. Dasar Teori

### 2.1 Form, Action, dan Method
Elemen `<form>` membungkus kontrol input dan menentukan tujuan pengiriman data. Walaupun data belum diproses di *server*, struktur *form* harus disiapkan dengan benar agar mudah diintegrasikan dengan *backend*.

| Atribut | Keterangan |
|---|---|
| `action` | Menentukan URL tujuan pengiriman data |
| `method="get"` | Menaruh data pada URL, cocok untuk pencarian atau data non-sensitif |
| `method="post"` | Mengirim data pada *body request*, lazim untuk data pendaftaran |

> Pemilihan *method* tidak otomatis membuat data aman. Keamanan tetap memerlukan HTTPS dan validasi di *server*.

### 2.2 Tipe Input Dasar

| Tipe | Fungsi |
|---|---|
| `text` | Menerima teks umum |
| `email` | Memberi bantuan validasi format email |
| `password` | Menyamarkan karakter di layar |
| `number` | Menerima angka (bisa dibatasi `min` dan `max`) |
| `date` | Menampilkan kontrol tanggal sesuai browser |

Atribut `name` penting karena menjadi nama *key* saat data dikirim.

### 2.3 Label dan Aksesibilitas
`<label>` dikaitkan dengan input memakai `for` yang sama dengan `id`. Cara ini memperluas area klik dan membantu pembaca layar memahami hubungan label dan kontrol.

### 2.4 Jenis Button

| Jenis | Fungsi |
|---|---|
| `type="submit"` | Mengirim *form* |
| `type="reset"` | Mengosongkan seluruh isian (hati-hati, bisa menghapus input tanpa sengaja) |
| `type="button"` | Tidak mengirim apa pun kecuali diberi perilaku JavaScript |

### 2.5 Box Model dan Media Query (untuk Tugas)
*Box model* menggambarkan setiap elemen sebagai kotak berlapis: *content*, *padding*, *border*, dan *margin*. Dengan `box-sizing: border-box`, lebar elemen sudah termasuk *padding* dan *border*. *Media query* adalah aturan CSS yang hanya aktif pada kondisi tertentu, misalnya lebar layar.

```css
@media (max-width: 767px) {
  /* aturan khusus layar di bawah 768px */
}
```

---

## 3. Alat dan Bahan

| Kategori | Keterangan |
|---|---|
| **Bahasa** | HTML5 dan CSS3 |
| **Text Editor** | Visual Studio Code |
| **Browser** | Google Chrome / Microsoft Edge _(sesuaikan)_ |
| **Version Control** | Git dan GitHub |

---

## 4. Struktur Proyek

```
Prak_DW_A-Pertemuan-7/
├── Contoh 1/                       # Form Pencarian Mahasiswa
│   ├── index.html
│   ├── css/
│   │   └── style.css
├── Contoh 2/                       # Form Pendaftaran Mahasiswa
│   ├── index.html
│   ├── css/
│   │   └── style.css
├── Tugas/                          # Landing page Arunika Studio
│   ├── index.html
│   ├── css/
│   │   └── style.css
│   └── screenshot/
├── Materi/                         # Modul pertemuan 7
└── README.md                       # Laporan praktikum
```

---

## 5. Pembahasan dan Hasil

### 5.1 Contoh 1: Form Pencarian Mahasiswa

Form untuk mencari data mahasiswa berdasarkan nama, NIM, angkatan, atau tanggal masuk. *Method* yang dipakai adalah **GET** karena form ini untuk pencarian.

#### Struktur HTML

```html
<main class="container">
  <section class="form-card">
    <h1>Pencarian Data Mahasiswa</h1>
    <p class="description">...</p>
    <form action="hasilpencarian.html" method="get">
      <div class="form-group">   <!-- label + input, diulang 4 kali -->
      <div class="button-group"> <!-- 3 button -->
    </form>
  </section>
</main>
```

| Field | Tipe Input | Keterangan |
|---|---|---|
| Nama Mahasiswa | `text` | Menerima nama untuk pencarian |
| NIM | `text` | Menerima NIM, contoh `20260001` |
| Tahun Angkatan | `number` | Dibatasi `min="2020"` dan `max="2030"` |
| Tanggal Masuk | `date` | Menampilkan pemilih tanggal bawaan browser |

| Button | Type | Keterangan |
|---|---|---|
| Cari Data | `submit` | Mengirim form pencarian |
| Reset | `reset` | Mengosongkan semua isian |
| Bantuan | `button` | Tombol biasa tanpa aksi pengiriman |

#### Penerapan CSS

Class `.form-card` memakai *padding*, `border-radius`, dan `box-shadow` untuk membuat kartu putih di tengah halaman. Tombol disusun dengan Flexbox dan diberi warna lewat tiga varian class.

```css
.container   { width: 90%; max-width: 700px; margin: 60px auto; }
.form-card   { background-color: white; padding: 35px; border-radius: 12px; }
.button-group { display: flex; gap: 10px; }
```

#### Media Query

```css
@media (max-width: 600px) {
    .button-group { flex-direction: column; }
    .btn          { width: 100%; }
}
```

Pada layar kecil, ketiga tombol tersusun ke bawah dan lebarnya penuh.

#### Hasil Tampilan Contoh 1

<img width="702" height="627" alt="Screenshot 2026-10-27 211451" src="https://github.com/user-attachments/assets/40d3e599-6264-4cda-8f8b-2b6be1a29726" />

### 5.2 Contoh 2: Form Pendaftaran Mahasiswa

Form pendaftaran dengan lebih banyak jenis kontrol. *Method* yang dipakai adalah **POST** karena data pendaftaran dikirim lewat *body request*.

#### Struktur Field

| Field | Kontrol | Keterangan |
|---|---|---|
| Nama Lengkap | `input text` | Wajib diisi (`required`) |
| Email | `input email` | Wajib diisi dengan validasi format email |
| Password | `input password` | Wajib diisi, disertai petunjuk minimal 8 karakter |
| Umur | `input number` | Dibatasi `min="16"` dan `max="80"` |
| Tanggal Lahir | `input date` | Wajib diisi |
| Program Studi | `select` | Memilih satu dari empat program studi |
| Alamat | `textarea` | Menerima alamat lengkap dengan 5 baris |

Setiap field memiliki `label` yang terhubung lewat `for` dan `id`, serta atribut `name` sebagai *key* data.

#### Penerapan CSS

Warna dan sudut dikelola lewat **variabel CSS** pada `:root` supaya mudah diganti dari satu tempat.

```css
:root {
    --primary: #235789;
    --background: #f5f7fa;
    --border: #d9dee5;
    --radius: 8px;
}

input, select, textarea {
    width: 100%;
    padding: 12px 14px;
    border: 1px solid var(--border);
    border-radius: var(--radius);
}
```

Selector `input, select, textarea` dikelompokkan agar ketiga kontrol memakai gaya yang sama. Tombol memakai tiga varian: `.btn-primary`, `.btn-reset`, dan `.btn-secondary`.

#### Media Query

```css
@media (max-width: 600px) {
    .registration-card { padding: 24px; }
    .button-group      { flex-direction: column; }
    .btn               { width: 100%; }
}
```

#### Hasil Tampilan Contoh 2

<img width="647" height="890" alt="Screenshot 2026-10-27 211551" src="https://github.com/user-attachments/assets/a8652077-84ed-4e68-956f-4498cf3b61a8" />

---

### 5.3 Tugas: Landing Page Arunika Studio

#### Studi Kasus
Arunika Studio membutuhkan landing page sederhana yang nyaman di desktop dan ponsel. Konten terdiri dari *header*, *hero*, tiga layanan, dan *footer*. Masalah utamanya adalah kode CSS tidak boleh tersebar dan tiga *card* harus berubah menjadi satu kolom pada layar kecil.

#### Struktur HTML

```html
<header class="site-header">
  <div class="container header-inner">   <!-- brand + menu -->
<main>
  <section class="hero">                 <!-- judul, deskripsi, 2 tombol -->
  <section class="section" id="layanan">
    <div class="services">               <!-- tiga card -->
<footer class="site-footer">
```

| Bagian | Fungsi |
|---|---|
| `header` | Menampilkan nama studio dan menu navigasi menggunakan Flexbox |
| `hero` | Menampilkan judul, deskripsi, dan dua tombol menggunakan latar biru tua |
| `services` | Menampilkan tiga card layanan menggunakan CSS Grid |
| `footer` | Menampilkan hak cipta dan email menggunakan Flexbox |

#### Penerapan CSS

Seluruh CSS berada di satu *file* `css/style.css`, tanpa *inline style* maupun tag `<style>`. Warna disimpan sebagai variabel di `:root`.

**Class reusable:**

| Class | Fungsi |
|---|---|
| `.container` | Membatasi lebar konten dan menengahkannya, dipakai di header, hero, layanan, dan footer |
| `.btn` | Menjadi dasar tombol, dengan varian `.btn-primary` dan `.btn-outline` |
| `.card` | Menjadi kotak layanan yang dipakai tiga kali |

**Box model** diterapkan pada `.card`, yaitu `margin`, `padding`, `border`, dan `border-radius`:

```css
* { box-sizing: border-box; }

.card {
    margin: 0;
    padding: 28px;
    border: 1px solid var(--border);
    border-top: 5px solid var(--sun);
    border-radius: 12px;
}
```

Tiga *card* disusun dengan CSS Grid:

```css
.services {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 24px;
}
```

#### Media Query (satu breakpoint)

```css
@media (max-width: 767px) {
    .services { grid-template-columns: 1fr; }
    /* header, hero, dan footer juga disesuaikan */
}
```

Pada layar di bawah 768px, tiga *card* menjadi satu kolom, *header* dan *footer* ditumpuk, dan ukuran judul diperkecil.

#### Hasil Tampilan Tugas

**Desktop:**

<img width="1366" height="1011" alt="desktop" src="https://github.com/user-attachments/assets/7cf9bf2c-1828-40de-8728-6f9e932d69f5" />


**Mobile:**

<img width="390" height="1371" alt="mobile" src="https://github.com/user-attachments/assets/fc58f6dd-b91b-4705-ba18-d81e0dfbc778" />


#### Ringkasan Perubahan, Masalah, dan Solusi

Pada tugas ini saya membangun ulang halaman profil Arunika Studio menjadi dua file, yaitu index.html untuk struktur dan style.css untuk seluruh tampilan. Halaman terdiri dari header, hero, tiga kartu layanan, dan footer. Perubahan utamanya adalah memindahkan semua gaya ke satu file CSS dan menerapkan box model dengan box-sizing: border-box agar lebar elemen sudah mencakup padding dan border. Saya membuat tiga class reusable, yaitu .container untuk membatasi lebar konten, .btn untuk tombol, dan .card untuk kotak layanan.

Masalah pertama adalah kode CSS yang mudah tersebar. Solusinya, saya tidak memakai inline style maupun tag style, dan warna disimpan sebagai variabel di :root sehingga perubahan cukup dilakukan di satu tempat. Masalah kedua adalah tiga card harus menjadi satu kolom pada layar kecil. Saya memakai CSS Grid dengan tiga kolom pada desktop, lalu satu media query max-width 767px mengubahnya menjadi satu kolom. Media query yang sama juga merapikan header, ukuran judul, dan footer agar nyaman di ponsel. Hasilnya diuji pada lebar 1366px dan 390px, dan tidak ada scroll horizontal di keduanya.

#### Catatan Pembagian Peran
Tugas ini dikerjakan secara individu, sehingga tidak ada pembagian peran.

---

## 6. Perbandingan Contoh 1 dan Contoh 2

| Aspek | Contoh 1 | Contoh 2 |
|---|---|---|
| **Judul halaman** | Form Pencarian Mahasiswa | Form Pendaftaran Mahasiswa |
| **Method** | GET | POST |
| **Jumlah field** | 4 (text, text, number, date) | 7 (text, email, password, number, date, select, textarea) |
| **Validasi** | Batas `min` dan `max` pada angkatan | `required`, tipe `email`, `min` dan `max` pada umur |
| **Button** | Cari Data, Reset, Bantuan | Daftar, Reset, Kembali |
| **Pengelolaan warna** | Kode warna langsung | Variabel CSS (`:root`) |
| **Breakpoint** | 600px | 600px |

---

<p align="center">
  <sub>© 2026 Ilham Baihaqi (4525210029) · Teknik Informatika · Universitas Pancasila</sub>
</p>
