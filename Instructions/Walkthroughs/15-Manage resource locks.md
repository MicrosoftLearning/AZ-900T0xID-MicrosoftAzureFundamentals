---
wts:
    title: '15 - Mengelola kunci sumber daya (5 menit)'
    module: 'Modul 05: Mendeskripsikan fitur identitas, tata kelola, privasi, dan kepatuhan'
---
# 15 - Mengelola kunci sumber daya

Dalam panduan ini, kita akan menambahkan kunci ke grup sumber daya dan menguji menghapus grup sumber daya. Kunci dapat diterapkan dalam langganan ke grup sumber daya, atau sumber daya individu untuk mencegah penghapusan atau pengubahan sumber daya penting yang tidak disengaja.  

# Tugas 1: Membuat grup sumber daya (5 menit)

Dalam tugas ini, kita akan membuat grup sumber daya untuk latihan ini. 

1. Masuk ke [portal Microsoft Azure](https://portal.azure.com).

2. Di bilah **Search** di bagian atas portal, cari **Resource group**. 

3. Lalu klik **+Add +New +Create** 

    | Setting | Value |
    | -- | -- |
    | Subscription | **Gunakan langganan Anda** |
    | Name | **myRGLocks** |
    | Region | **(US) East US** |
    

# Tugas 2:  Menambahkan Kunci ke grup sumber daya dan menguji penghapusan

Dalam tugas ini, kita akan menambahkan kunci sumber daya ke grup sumber daya dan menguji menghapus grup sumber daya. 

1. Di portal Microsoft Azure, buka grup sumber daya yang baru dibuat **myRGLocks**.

2. Anda dapat menerapkan kunci ke langganan, grup sumber daya, atau sumber daya individu untuk mencegah penghapusan atau pengubahan sumber daya penting yang tidak disengaja. 

3. Di bagian **Settings**, klik **Locks**, lalu klik **+ Add**. 

    ![Cuplikan layar grup sumber daya myRGLocks dengan panel Kunci yang ditampilkan.](../images/1601.png)

4. Konfigurasikan kunci baru. Setelah selesai, klik **OK**. 

    | Setting | Value |
    | -- | -- |
    | Lock name | **RGLock** |
    | Lock Type | **Delete** |
    | | |

5. Klik **Overview** dan klik **Delete resource group**. Ketik nama grup sumber daya dan klik **OK**. Anda menerima pesan kesalahan yang menyatakan bahwa grup sumber daya terkunci dan tidak dapat dihapus.

    ![Cuplikan layar dari kunci hapus gagal.](../images/1602.png)

# Tugas 3: Menguji menghapus anggota grup sumber daya.

Dalam tugas ini, kita akan menguji apakah kunci sumber daya melindungi akun penyimpanan di grup sumber daya. 

1. Dari bilah **All services**, cari dan pilih **Storage accounts**, lalu klik **+ Add, + Create, atau + New**. 

2. Pada halaman **Storage accounts** bilah **+Add +New +Create**, isi informasi berikut (ganti **xxxx** pada nama akun penyimpanan dengan huruf dan angka sedemikian rupa sehingga namanya unik secara global). Gunakan pengaturan default untuk yang lainnya.

    | Setting | Value | 
    | --- | --- |
    | Subscription | **Pilih langganan Anda** |
    | Resource group | **myRGLocks** |
    | Storage account name | **storageaccountxxxx** |
    | Location | **(US) East US**  |
    | Performance | **Standard** |
    | Account kind | **StorageV2 (general purpose v2)** |
    | Replication | **Locally redundant storage (LRS)** |
    | Access tier (default) | **Hot** |
   

3. Klik **Review + Create** untuk meninjau pengaturan akun penyimpanan Anda dan mengizinkan Azure untuk memvalidasi konfigurasi. 

4. Setelah divalidasi, klik **Create**. Tunggu pemberitahuan bahwa akun berhasil dibuat. 

5.  Tunggu pemberitahuan bahwa akun penyimpanan berhasil dibuat. 

6. Akses akun penyimpanan baru Anda dan dari panel **Overview**, klik **Delete**. Anda menerima pesan kesalahan yang menyatakan sumber daya atau induknya memiliki kunci hapus. 

    ![Cuplikan layar dari kesalahan saat menghapus akun penyimpanan.](../images/1603.png)

    **Catatan**: Meskipun kita tidak membuat kunci khusus untuk akun penyimpanan, kita membuat kunci di tingkat grup sumber daya, yang berisi akun penyimpanan. Dengan demikian, kunci tingkat *induk* ini mencegah kita menghapus sumber daya dan akun penyimpanan mewarisi kunci dari induknya.

# Tugas 4: Menghapus kunci sumber daya.

Dalam tugas ini, kita akan menghapus kunci sumber daya dan mengujinya. 

1. Kembali ke bilah grup sumber daya **myRGLocks-XXXXXXXX** dan, di bagian **Settings**, Klik **Locks**.
    
2. Klik tautan **Delete** di ujung kanan entri **myRGLocks-XXXXXXXX**, di sebelah kanan **Edit**.

    ![Cuplikan layar Kunci dengan tautan Hapus disorot.](../images/1604.png)

3. Kembali ke bilah akun penyimpanan dan konfirmasikan bahwa Anda sekarang dapat menghapus sumber daya.

Selamat! Anda membuat grup sumber daya, menambahkan kunci ke grup sumber daya dan menguji penghapusan, menguji menghapus sumber daya di grup sumber daya, dan menghapus kunci sumber daya. 

**Catatan**: Untuk menghindari biaya tambahan, Anda dapat menghapus grup sumber daya ini. Telusuri grup sumber daya, klik grup sumber daya, lalu klik **Delete resource group**. Pastikan nama grup sumber daya lalu klik **Delete**. Pantau **Notifications** untuk melihat bagaimana proses penghapusan.
