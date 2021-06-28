---
wts:
    title: '08 - Menerapkan Azure Functions (5 mnt)'
    module: 'Modul 03: Menjelaskan solusi inti dan alat manajemen'
---
# 08 - Menerapkan Azure Functions

Dalam panduan ini, kita akan membuat Aplikasi Fungsi untuk menampilkan pesan Hello ketika ada permintaan HTTP. 

# Tugas 1: Membuat aplikasi Fungsi (5 mnt)

Dalam tugas ini, kita akan membuat aplikasi Fungsi.

1. Masuk ke [portal Microsoft Azure](https://portal.azure.com).

1. Di kotak teks **Search resources, services, and docs** di bagian atas portal, cari dan pilih **Function App**, lalu dari bilah **Function App**, klik **+ Add, + Create, atau + New**.

1. Pada tab **Basic** bilah **Function App**, tentukan pengaturan berikut (ganti **xxxx** dalam nama fungsi dengan huruf dan angka sehingga namanya unik secara global dan biarkan semua pengaturan lain dengan nilai default): 

    | Settings | Value |
    | -- | --|
    | Subscription | nama langganan Azure Anda |
    | Resource group | nama grup sumber daya baru **myRGFunction** |
    | Function App name | **fungsi-xxxx** |
    | Publish | **Code** |
    | Runtime stack | **NET** |
    | Version | **3,1** |
    | Region | **East US** |
    | | |

    **Catatan** - Ingatlah untuk mengubah **xxxx** agar **Nama Aplikasi Fungsi** menjadi unik.

1. Klik **Review + Create.** dan, setelah validasi berhasil, klik **Create** untuk mulai memprovisi dan menyebarkan Aplikasi Fungsi Azure yang baru.

1. Tunggu pemberitahuan bahwa sumber daya telah dibuat.

1. Kembali ke bilah **Function App**, klik **Refresh** dan verifikasi bahwa aplikasi fungsi yang baru dibuat memiliki status **Running**. 

    ![Cuplikan layar halaman Aplikasi Fungsi dengan aplikasi Fungsi baru.](../images/0701.png)

# Tugas 2: Membuat fungsi dan pengujian yang dipicu HTTP

Dalam tugas ini, kita akan menggunakan fungsi Webhook + API untuk menampilkan pesan saat ada permintaan HTTP. 

1. Pada bilah **Function App**, klik aplikasi fungsi yang baru dibuat. 

1. Di bilah aplikasi fungsi, di bagian **Functions**, klik **Functions**, lalu klik **+ Add**.

    ![Cuplikan layar langkah memilih lingkungan pengembangan di azure functions untuk panel memulai dot net di dalam portal Microsoft Azure. Elemen tampilan untuk membuat fungsi dalam portal baru disorot. Elemen yang disorot adalah memperluas aplikasi fungsi, menambahkan fungsi baru, dalam portal, dan tombol continue.](../images/0702.png)

1. Di bagian **Select a template** dari bilah **Add function**, klik **HTTP trigger**. Di bawah bagian **Template details**, terima nilai default, lalu klik **Add**.

1. Pada bilah **HttpTrigger1**, di bagian **Developer**, klik **Code + Test**. 

1. Di **HttpTrigger1 \| **Bilah **Code + Test**, tinjau kode yang dibuat secara otomatis dan perhatikan bahwa kode tersebut dirancang untuk menjalankan permintaan HTTP dan informasi log. Selain itu, perhatikan fungsi menampilkan pesan Hello dengan sebuah nama. 

    ![Cuplikan layar kode fungsi. Pesan Hello disorot.](../images/0704.png)

1. Klik **Get function URL** dari bagian atas editor fungsi. 

1. Pastikan nilai dalam daftar menurun **Key** diatur ke **default** dan klik **Copy** untuk menyalin fungsi URL. 

    ![Cuplikan layar panel dapatkan URL fungsi di dalam editor fungsi di portal Microsoft Azure. Elemen tampilan tombol dapatkan URL fungsi, set kunci menurun, dan tombol copy URL disorot untuk menunjukkan cara mendapatkan dan menyalin URL fungsi dari editor fungsi.](../images/0705.png)

1. Buka tab browser baru dan tempel URL fungsi yang disalin ke bilah alamat browser web Anda. Ketika halaman diminta, fungsi akan berjalan. Perhatikan pesan yang dikembalikan yang menyatakan bahwa fungsi tersebut memerlukan nama di isi permintaan.

    ![Cuplikan layar pesan harap berikan nama.](../images/0706.png)

1. Tambahkan **&name=*yourname*** di akhir URL.

    **Catatan**: Ganti ***yourname*** dengan nama depan Anda. Misalnya, jika nama Anda Cindy, URL final akan menyerupai `https://azfuncxxx.azurewebsites.net/api/HttpTrigger1?code=X9xx9999xXXXXX9x9xxxXX==&name=cindy`

    ![Cuplikan layar URL fungsi yang disorot dan contoh nama pengguna yang ditambahkan di bilah alamat browser web. Pesan hello dan nama pengguna juga disorot untuk mengilustrasikan output dari fungsi di jendela browser utama.](../images/0707.png)

1. Saat fungsi berjalan, setiap pemanggilan dilacak. Untuk melihat jejak di portal Microsoft Azure, kembali ke **HttpTrigger1 \| **Bilah **Code + Test** dan klik **Monitor**.

    ![Cuplikan layar log informasi jejak yang dihasilkan dari menjalankan fungsi di dalam editor fungsi di portal Microsoft Azure.](../images/0709.png) 

Selamat! Anda telah membuat Aplikasi Fungsi untuk menampilkan pesan Halo ketika ada permintaan HTTP. 

**Catatan**: Untuk menghindari biaya tambahan, Anda dapat menghapus grup sumber daya ini. Telusuri grup sumber daya, klik grup sumber daya, lalu klik **Delete resource group**. Pastikan nama grup sumber daya lalu klik **Delete**. Pantau **Notifications** untuk melihat bagaimana proses penghapusan.
