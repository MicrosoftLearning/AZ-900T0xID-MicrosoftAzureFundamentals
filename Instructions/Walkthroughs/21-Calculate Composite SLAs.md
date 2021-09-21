---
wts:
    title: '21 - Menghitung SLA Komposit (5 mnt)'
    module: 'Modul 06: Menjelaskan manajemen biaya dan persetujuan tingkat layanan Azure'
---
# 21 - Menghitung SLA Komposit (5 mnt)

Dalam panduan ini, kami akan menentukan ketersediaan SLA layanan Azure dan kemudian menghitung ketersediaan yang diharapkan berdasarkan SLA komposit aplikasi.

Aplikasi contoh kami terdiri dari layanan Azure ini. Kami tidak akan membahas konfigurasi dan pertimbangan arsitektural secara mendalam, maksudnya di sini adalah untuk memberikan contoh tingkat tinggi.

+ **Layanan aplikasi**: Untuk membuat host aplikasi.
+ **Azure Active Directory B2C**: Untuk mengautentikasi login pengguna dan mengelola profil.
+ **Gateway Aplikasi**: Untuk mengelola akses aplikasi, dan penskalaan. 
+ **Azure SQL Database**: Untuk menyimpan data aplikasi. 

# Tugas 1: Menentukan nilai persentase waktu aktif SLA untuk aplikasi kita

1. Di browser, buka halaman [Ringkasan SLA untuk layanan Azure](https://azure.microsoft.com/id-id/support/legal/sla/summary/).

2. Temukan nilai waktu aktif SLA **App Service**, **99.95%**. Klik **View full details**, dan lalu perluas **SLA details**. Perhatikan **Monthly uptime percentages** dan **Service Credits**.

3. Kembali ke halaman web SLA dan temukan layanan **Azure Active Directory B2C** dan tentukan nilai waktu aktif SLA, **99.9%**. 

4. Temukan nilai waktu aktif SLA **Application Gateway** , **99.95%**. 

5. Azure SQL database menggunakan tingkatan Premium tetapi tidak dikonfigurasi untuk Penyebaran Zona Redundan. Temukan nilai waktu aktif SLA **Azure SQL Database**, **99.99%**. 

    **Catatan**: Ada nilai waktu aktif yang berbeda untuk konfigurasi dan penyebaran Azure SQL Database yang berbeda. Anda harus memahami dengan jelas nilai waktu aktif yang diperlukan saat merencanakan dan menentukan biaya penerapan serta konfigurasi Anda. Perubahan kecil dalam waktu aktif dapat berdampak pada biaya layanan serta berpotensi meningkatkan kompleksitas konfigurasi. Beberapa layanan lain yang mungkin menarik di halaman ringkasan Azure SLA akan mencakup **Komputer Virtual**, **Akun Penyimpanan**, dan **Cosmos DB**.

# Tugas 2: Hitung waktu aktif persentase SLA Komposit Aplikasi

1. Jika salah satu layanan yang terdiri dari aplikasi kami tidak tersedia, aplikasi kita tidak akan tersedia bagi pengguna untuk masuk dan digunakan. Dengan demikian total waktu aktif untuk aplikasi kita terdiri dari berikut ini:

    **% waktu aktif Layanan Aplikasi** X **% waktu aktif Azure AD B2C** X  **% waktu aktif Azure Application Gateway** X **% waktu aktif Azure SQL Database** = **Total % Waktu aktif**

    yang dalam persentase adalah sebagai berikut:

    **99.95%** X **99.9%** X **99.95%** X **99.99%** = **99.79%**

    Ini adalah ketersediaan yang diharapkan berbasis SLA dari aplikasi kita dengan layanan dan arsitektur saat ini.

Selamat! Anda telah menentukan waktu aktif berbasis SLA untuk setiap layanan dalam aplikasi sampel kita dan kemudian menghitung ketersediaan yang diharapkan berbasis SLA gabungan untuk aplikasi tersebut.
