# Tugas Minggu 2: Website Kedai Kopi (KOPIKU)

## 1. Apa yang muncul di address bar setelah form dikirim, dan mengapa data form tampil di sana?

Setelah form di `pesan.html` saya isi lengkap dan tombol Kirim diklik, alamat di address bar bertambah dengan tanda tanya (`?`) di belakang `pesan.html`, lalu diikuti semua data yang tadi diinput dalam format `name=value` dan dipisahkan tanda `&` (disebut *query string*). Saat saya uji di browser, alamatnya berubah menjadi:

`http://127.0.0.1:5500/pesan.html?nama=yuni&whatsapp=09876545678&menu=Espresso&jumlah=1&cara_ambil=Ambil+di+tempat&catatan=-`

Data tersebut tampil di address bar karena form-nya menggunakan `method="get"`. Seperti yang dibahas di materi HTTP Minggu 1, method `GET` memang mengirim data lewat URL sehingga isinya langsung terlihat terbuka, berbeda dengan `POST` yang menaruh data di dalam *request body*. Karena sifatnya terlihat di URL, `GET` lebih cocok untuk permintaan biasa seperti pencarian atau filter, bukan untuk mengirim data pribadi atau rahasia seperti password.

## 2. Pemilihan elemen semantic dibanding `<div>`

Di halaman KOPIKU, saya memilih memakai `<nav>` di dalam `<header>` untuk membungkus link navigasi (Beranda, Menu, dan Pesan), bukan memakai `<div>`.

Sebenarnya kalau pakai `<div>` pun halaman tetap bisa tampil dan tidak langsung error, hanya saja `<div>` sifatnya terlalu umum karena tidak menjelaskan fungsi bagian tersebut. Kalau hampir semua bagian halaman dibungkus `<div>`, kode jadi penuh dengan tag penutup `</div>` yang bikin bingung saat dibaca ulang atau dicek di tab Elements, dan akhirnya lebih rawan salah *nesting* atau lupa menutup tag. Dengan memakai `<nav>`, langsung terlihat jelas bahwa bagian itu adalah navigasi utama baik buat saya sendiri waktu mengedit kode, maupun buat browser, mesin pencari, dan *screen reader* agar halaman lebih ramah aksesibilitas.


link github : https://dyunyunn.github.io/kedai_kopi/

# Tugas Minggu 3: CSS, Layout, dan Responsive Design (KOPIKU)

## a. Bagian yang Memakai Flexbox dan CSS Grid

Di website KOPIKU, saya pakai **Flexbox** untuk bagian header (`.header-inner` dan `.nav-list`) dan **CSS Grid** untuk daftar card menu (`.menu-grid`) di halaman `menu.html`.

Flexbox cocok buat header dan navigasi karena susunannya cuma butuh satu arah. Di layar HP, nama kedai dan link menu ditumpuk ke bawah (`flex-direction: column`). Begitu layar lebih lebar, arahnya tinggal diubah jadi sejajar ke samping (`flex-direction: row`) dengan nama kedai di kiri dan link navigasi di kanan (`justify-content: space-between`).

Kalau untuk daftar menu, CSS Grid jauh lebih pas karena tata letaknya butuh baris sekaligus kolom. Dengan Grid, jumlah card menu gampang diatur supaya menyesuaikan lebar layar: 1 kolom di HP, 2 kolom mulai lebar `600px`, dan 3 kolom mulai lebar `960px`, dengan jarak dan ukuran card yang tetap rapi.

## b. Aturan CSS yang Awalnya Tidak Berlaku

Waktu pertama kali menyambungkan `css/style.css`, tampilan header memang sudah berubah, tapi isi halaman di `<main>` dan `<footer>` masih mepet di pinggir kiri layar. Daftar menu di `menu.html` juga masih jadi list biasa, dan form di `pesan.html` melebar penuh sampai ujung kanan.

Pas saya cek lewat DevTools di panel **Styles**, aturan untuk `.container`, `.menu-grid`, dan `.form-pesan` ternyata tidak muncul sama sekali pada elemen `<main>`, `<ul>`, maupun `<form>`. Yang aktif cuma gaya bawaan browser (*user agent stylesheet*). Dari situ ketahuan kalau `class` yang sudah ditulis di `style.css` ternyata belum ditambahkan ke tag HTML-nya. Setelah saya pasang `class="container"`, `class="menu-grid"`, `class="menu-card"`, dan `class="form-pesan"` di file HTML lalu disimpan, semua aturannya langsung kebaca di panel Styles dan tampilannya rapi.