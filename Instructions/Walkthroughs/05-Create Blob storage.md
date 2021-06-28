---
wts:
    title: '05 - Membuat penyimpanan blob (5 menit)'
    module: 'Modul 02 – Layanan Core Azure (Beban Kerja)'
---
# 05 - Membuat penyimpanan blob

Dalam panduan ini, kita akan membuat akun penyimpanan, lalu bekerja dengan file penyimpanan blob.

# Tugas 1: Membuat akun penyimpanan (5 menit)

Dalam tugas ini, kita akan membuat akun penyimpanan baru. 

1. Masuk ke portal Microsoft Azure di <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. Dari bilah **All services**, cari dan pilih **Storage accounts**, lalu klik **+ Add, + Create, atau + New**. 

3. Pada tab **Basics** dari bilah **Create storage account**, isi informasi berikut (ganti **xxxx** pada nama akun penyimpanan dengan huruf dan angka sedemikian rupa sehingga namanya unik secara global). Gunakan pengaturan default untuk yang lainnya.

    | Setting | Value | 
    | --- | --- |
    | Subscription | **Pilih langganan Anda** |
    | Resource group | **myRGStorage** (buat baru) |
    | Storage account name | **storageaccountxxxx** |
    | Location | **(US) East US**  |
    | Performance | **Standard** |
    | Account kind | **StorageV2 (general purpose v2)** |
    | Replication | **Locally redundant storage (LRS)** |
    | | |

    **Catatan** - Ingatlah untuk mengubah **xxxx** agar menjadi **Nama akun penyimpanan** yang unik

5. Klik **Review + Create** untuk meninjau pengaturan akun penyimpanan Anda dan mengizinkan Azure untuk memvalidasi konfigurasi. 

6. Setelah divalidasi, klik **Create**. Tunggu pemberitahuan bahwa akun berhasil dibuat. 

7. Dari halaman Beranda, cari dan pilih **Storage accounts** dan pastikan akun penyimpanan baru Anda terdaftar.

    ![Cuplikan layar dari akun penyimpanan yang baru dibuat di portal Microsoft Azure.](../images/0401.png)

# Tugas 2: Bekerja dengan penyimpanan blob

Dalam tugas ini, kita akan membuat kontainer Blob dan mengunggah file blob. 

1. Klik nama akun penyimpanan baru, gulir ke bagian **Blob service**, lalu klik **Containers**.

2. Klik **+ Container** dan lengkapi informasinya. Gunakan ikon Informasi untuk mempelajari lebih lanjut. Setelah selesai, klik **Create**.


    | Setting | Value |
    | --- | --- |
    | Name | **container1**  |
    | Public access level| **Private (no anonymous access)** |
    | | |

    ![Cuplikan layar dari kontainer blob yang baru dibuat di akun penyimpanan di portal Microsoft Azure.](../images/0402.png)

4. Klik kontainer **container1**, lalu klik **Upload**.

5. Jelajahi file di komputer lokal Anda. 

    **Catatan**: Anda dapat membuat file `.txt` kosong atau menggunakan file yang sudah ada. Pertimbangkan memilih file dengan ukuran kecil untuk meminimalkan waktu pengunggahan.

6. Klik panah **Advanced**, biarkan nilai default tetapi tinjau opsi yang tersedia, lalu klik **Upload**.

    **Catatan**: Anda dapat mengunggah blob sebanyak yang Anda suka dengan cara ini. Blob baru akan dicantumkan di dalam kontainer.

7. Setelah file diunggah, klik kanan pada file dan perhatikan opsi termasuk Tampilkan/edit, Unduh, Properti, dan Hapus. 

8. Jika Anda punya waktu, dari bilah akun penyimpanan, tinjau opsi untuk File, Tables, dan Queues.

# Tugas 3: Memantau akun penyimpanan

1. Jika perlu, kembalilah ke bilah akun penyimpanan dan klik **Diagnose and solve problems**. 

2. Jelajahi beberapa masalah penyimpanan paling umum. Perhatikan bahwa ada beberapa pemecah masalah.

3. Di bilah akun penyimpanan, gulir ke bawah ke bagian **Monitoring** dan klik **Insights**. Perhatikan bahwa ada informasi tentang Kegagalan, Performa, Ketersediaan, dan Kapasitas. Informasi Anda akan berbeda.

    ![Cuplikan layar halaman Wawasan akun penyimpanan.](../images/0403.PNG)

Selamat! Anda telah membuat akun penyimpanan, lalu bekerja dengan blob penyimpanan.

**Catatan**: Untuk menghindari biaya tambahan, Anda dapat menghapus grup sumber daya ini. Telusuri grup sumber daya, klik grup sumber daya, lalu klik **Delete resource group**. Pastikan nama grup sumber daya lalu klik **Delete**. Pantau **Notifications** untuk melihat bagaimana proses penghapusan.
