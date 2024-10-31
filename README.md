# Ionic2_Endini-Nurlaily_H1D022089_ShiftC

Cara kerja login pada aplikasi ini mengikuti alur sebagai berikut:

1. Inisialisasi Komponen dan Modul HTTP:
Pada app.module.ts, provideHttpClient() digunakan agar aplikasi dapat melakukan permintaan HTTP, memungkinkan interaksi dengan API eksternal.
Pada authentication.service.ts, HttpClient di-inject ke dalam AuthenticationService untuk mengelola permintaan ke API.

2. Pengaturan Guard untuk Proteksi Rute:
Di app-routing.module.ts, rute home hanya dapat diakses dengan guard authGuard, yang memeriksa apakah pengguna telah terautentikasi. Jika belum, pengguna dialihkan ke halaman login.
Halaman login juga menggunakan guard autoLoginGuard, yang mengarahkan pengguna langsung ke halaman home jika sudah login.

3. Proses Login pada Halaman Login:
Pengguna memasukkan username dan password pada login.page.html. Ketika tombol login ditekan, fungsi login() di login.page.ts akan dijalankan.
Fungsi login() memverifikasi input, kemudian mengirim data username dan password ke endpoint API (login.php) melalui postMethod() di AuthenticationService.
Respon API akan diperiksa; jika statusnya berhasil (status_login == "berhasil"), maka data token dan username disimpan dengan metode saveData(), yang mengupdate authenticationState menjadi true. Hal ini memungkinkan guard untuk mengenali pengguna sebagai terautentikasi dan mengarahkan mereka ke halaman home.

4. Menyimpan Data dan Status Login:
Data token dan username disimpan menggunakan Capacitor Preferences pada saveData(). Ini membantu agar status login tetap tersimpan saat aplikasi dibuka kembali.
loadData() digunakan untuk memuat ulang data token dan username dari Preferences saat aplikasi dimulai, menjaga status login tetap aktif jika data tersimpan.

5. Logout:
Pada halaman home, pengguna dapat menekan tombol logout yang memanggil fungsi logout() di home.page.ts.
Fungsi ini menghapus data login dari Preferences melalui clearData() di AuthenticationService, mengubah authenticationState menjadi false, dan mengarahkan pengguna kembali ke halaman login.
Melalui alur ini, aplikasi memastikan bahwa data pengguna aman dengan memanfaatkan Guard untuk mengontrol akses halaman dan mengelola sesi login/logout dengan lancar.

# 1. Gambar tampilan Login
![Tampilan login](https://raw.githubusercontent.com/endiniii/Ionic2_Endini-Nurlaily_H1D022089_ShiftC/main/login.png)

# 2. Gambar tampilan Logout
![Tampilan logout](https://raw.githubusercontent.com/endiniii/Ionic2_Endini-Nurlaily_H1D022089_ShiftC/main/logout.png) 
