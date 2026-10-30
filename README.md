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


