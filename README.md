# Tugas Minggu 2: Website Kedai Kopi (KOPIKU)

## 1. Apa yang muncul di address bar setelah form dikirim, dan mengapa data form tampil di sana?

Setelah form di `pesan.html` saya isi lengkap dan tombol Kirim diklik, alamat di address bar bertambah dengan tanda tanya (`?`) di belakang `pesan.html`, lalu diikuti semua data yang tadi diinput dalam format `name=value` dan dipisahkan tanda `&` (disebut *query string*). Saat saya uji di browser, alamatnya berubah menjadi:

`http://127.0.0.1:5500/pesan.html?nama=yuni&whatsapp=09876545678&menu=Espresso&jumlah=1&cara_ambil=Ambil+di+tempat&catatan=-`

Data tersebut tampil di address bar karena form-nya menggunakan `method="get"`. Seperti yang dibahas di materi HTTP Minggu 1, method `GET` memang mengirim data lewat URL sehingga isinya langsung terlihat terbuka, berbeda dengan `POST` yang menaruh data di dalam *request body*. Karena sifatnya terlihat di URL, `GET` lebih cocok untuk permintaan biasa seperti pencarian atau filter, bukan untuk mengirim data pribadi atau rahasia seperti password.

## 2. Pemilihan elemen semantic dibanding `<div>`

Di halaman KOPIKU, saya memilih memakai `<nav>` di dalam `<header>` untuk membungkus link navigasi (Beranda, Menu, dan Pesan), bukan memakai `<div>`.

Sebenarnya kalau pakai `<div>` pun halaman tetap bisa tampil dan tidak langsung error, hanya saja `<div>` sifatnya terlalu umum karena tidak menjelaskan fungsi bagian tersebut. Kalau hampir semua bagian halaman dibungkus `<div>`, kode jadi penuh dengan tag penutup `</div>` yang bikin bingung saat dibaca ulang atau dicek di tab Elements, dan akhirnya lebih rawan salah *nesting* atau lupa menutup tag. Dengan memakai `<nav>`, langsung terlihat jelas bahwa bagian itu adalah navigasi utama baik buat saya sendiri waktu mengedit kode, maupun buat browser, mesin pencari, dan *screen reader* agar halaman lebih ramah aksesibilitas.