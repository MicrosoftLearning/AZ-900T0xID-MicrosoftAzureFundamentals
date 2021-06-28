---
wts:
    title: '02 - Membuat Aplikasi Web (10 menit)'
    module: 'Modul 02 – Core Azure Services (Beban Kerja)'
---
# 02 - Membuat Aplikasi Web

Dalam panduan ini, kita akan membuat aplikasi web baru yang menjalankan kontainer Docker. Kontainer menampilkan pesan Selamat Datang. 

# Tugas 1: Membuat Aplikasi Web (10 menit)

Azure App Service sebenarnya adalah kumpulan dari empat layanan, yang semuanya dibuat untuk membantu Anda membuat host  dan menjalankan aplikasi web. Keempat layanan (Web Apps, Mobile Apps, API Apps, dan Logic Apps) terlihat berbeda, tetapi pada akhirnya semuanya beroperasi dengan cara yang sangat mirip. Web Apps adalah yang paling umum digunakan dari empat layanan, dan ini adalah layanan yang akan kita gunakan di lab ini.

Dalam tugas ini, Anda akan membuat Aplikasi Web Azure App Service. 

1. Masuk ke [portal Microsoft Azure](http://portal.azure.com/). 

2. Dari bilah **All service**, cari dan pilih **App Services**, lalu klik **+ Add, + Create, atau + New**

3. Pada tab **Basics** dari bilah **Web App**, tentukan pengaturan berikut (ganti **xxxx** dengan nama aplikasi web dengan huruf dan angka sehingga namanya unik secara global). Biarkan default untuk yang lainnya, termasuk App Service Plan. 

    | Setting | Value |
    | -- | -- |
    | Subscription | **Pilih langganan Anda** |
    | Resource Group | **myRGWebApp1** (buat baru) |
    | Name | **myDockerWebAppxxxx** |
    | Publish | **Docker Container** |
    | Operating System | **Linux** |
    | Region | **East US** (abaikan peringatan ketersediaan paket layanan apa pun) |
    | | |	
    
    **Catatan** - Ingatlah untuk mrngubah **xxxx** agar menjadi **Nama** yang unik

4. Klik **Next > Docker** dan konfigurasikan informasi kontainer. Perintah mulai adalah opsional dan tidak diperlukan dalam latihan ini. 

    **Catatan:** Ini adalah kontainer yang sama yang digunakan dalam panduan Instans Kontainer untuk menampilkan pesan hello world. 

    | Setting | Value |
    | -- | -- |
    | Options | **Single container** |
    | Image Source | **Docker Hub** |
    | Access Type | **Public** |
    | Image and tag | **microsoft/aci-helloworld** |
    | | |	


5. Klik **Review + create**, lalu klk **Create**. 

# Tugas 2: Menguji Aplikasi Web

Dalam tugas ini, kita akan menguji aplikasi web.

1. Tunggu hingga Aplikasi Web disebarkan

2. Dari **Notifications**, klik **Go to resource**. 

3. Di bilah **Overview**, temukan entri **URL**. 

    ![Cuplikan layar dari bilah properti aplikasi web. URL disorot.](../images/0801.png)

4. Klik **URL** untuk membuka tab browser baru dan menampilkan halaman Selamat Datang di Azure Container Instances.

    ![Cuplikan layar halaman Selamat Datang di Azure Container Instance.](../images/0802.png)

5. Beralih kembali ke bilah **Overview** aplikasi web dan perhatikan bahwa itu mencakup beberapa bagan. Jika Anda mengulangi langkah 4 beberapa kali, Anda akan melihat telemetri yang sesuai ditampilkan di bagan. Ini termasuk jumlah permintaan dan waktu respons rata-rata. 

**Catatan**: Untuk menghindari biaya tambahan, Anda dapat menghapus grup sumber daya ini. Telusuri grup sumber daya, klik grup sumber daya, lalu klik **Delete resource group**. Pastikan nama grup sumber daya lalu klik **Delete**. Pantau **Notifications** untuk melihat bagaimana proses penghapusan.

