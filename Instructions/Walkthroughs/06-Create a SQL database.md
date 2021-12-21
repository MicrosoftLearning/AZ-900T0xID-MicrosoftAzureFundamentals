---
wts:
    title: '06 - Membuat database SQL (5 menit)'
    module: 'Modul 02 – Core Azure Services (Beban Kerja)'
---

# 06 - Membuat database SQL (5 menit)

Dalam panduan ini, kita akan membuat database SQL di Azure, lalu melakukan kueri data di database tersebut.

# Tugas 1: Membuat database 

Dalam tugas ini, kita akan membuat database SQL berdasarkan database sampel AdventureWorksLT. 

1. Masuk ke portal Microsoft Azure di [**https://portal.azure.com**](https://portal.azure.com).

2. Dari bilah **All services**, cari dan pilih **SQL databases**, lalu klik **+ Add, + Create, + New**. 

3. Pada tab **Basics**, isi informasi ini.  

    | Setting | Value | 
    | --- | --- |
    | Subscription | **Gunakan default yang ada** |
    | Resource group | **Buat nama grup sumber daya baru** |
    | Database name| **db1** | 
    | Server | Pilih **Create new** (Bilah samping baru akan terbuka di sebelah kanan)|
    | Server name | **sqlserverxxxx** (harus unik) | 
    | Location | **(US) East US** |
    | Authentication method | **Use SQL authentication** |
    | Server admin login | **sqluser** |
    | Password | **Pa$$w0rd1234** |
    | Klik  | **OK** |

   ![Cuplikan layar dari panel Server dan panel Server Baru dengan bidang yang diisi sesuai tabel dan tombol Ulas + buat dan OK disorot.](../images/0501.png)

4. Di tab **Networking** dan konfigurasikan pengaturan berikut (biarkan yang lain tetap default) 

    | Setting | Value | 
    | --- | --- |
    | Connectivity method | **Public endpoint** |    
    | Allow Azure services and resources to access this server | **Yes** |
    | Add current client IP address | **No** |
    
   ![Cuplikan layar dari tab Jaringan dari blade Buat SQL Database dengan pengaturan yang dipilih sesuai tabel dan tombol Review + create disorot.](../images/0501b.png)

5. Di tab **Security**. 

    | Setting | Value | 
    | --- | --- |
    | Microsoft Defender for SQL| **Not now** |
    
6. Pindah ke tab **Additional settings**. Kita akan menggunakan database sampel AdventureWorksLT.

    | Setting | Value | 
    | --- | --- |
    | Use existing data | **Sample** |

    ![Cuplikan layar dari tab Additional settings dari bilah Create SQL Database dengan pengaturan yang dipilih sesuai tabel dan tombol Review + create disorot.](../images/0501c.png)

7. Klik **Review + create**, lalu klik **Buat** untuk menyebarkan dan memprovisi grup sumber daya, server, dan database. Ini bisa memakan waktu sekitar 2 hingga 5 menit untuk menyebarkan.


# Tugas 2: Menguji database.

Dalam tugas ini, kita akan mengonfigurasi server SQL dan menjalankan kueri SQL. 

1. Saat penyebaran telah selesai, klik Go to resource dari bilah penyebaran. Atau, dari bilah **All Resources**, cari dan pilih **Databases**, lalu **SQL databases** dan pastikan database baru Anda telah dibuat. Anda mungkin perlu melakukan **Refresh** halamannya.

    ![Cuplikan layar dari database dan server SQL yang baru saja disebarkan.](../images/0502.png)

2. Mengklik entri **db1** akan menyajikan database SQL yang sudah Anda buat. Di bilah db1, klik **Query editor (preview)**.

3. Masuk sebagai **sqluser** dengan kata sandi **Pa$$w0rd1234**.

4. Anda tidak akan bisa masuk. Baca kesalahan dengan cermat dan catat alamat IP yang perlu diizinkan melalui firewall. 

    ![Cuplikan layar halaman masuk Query Editor dengan kesalahan alamat IP.](../images/0503.png)

5. Kembali ke bilah **db1**, klik **Overview**. 

    ![Cuplikan layar dari halaman server SQL.](../images/0504.png)

6. Dari bilah db1 **Overview**, klik **Set server firewall** yang ada di bagian tengah atas layar gambaran.

7. Klik **Add client IP** (bilah menu atas) untuk menambahkan alamat IP yang direferensikan dalam kesalahan. (Mungkin telah diisi otomatis untuk Anda - jika tidak, tempelkan ke bidang alamat IP). Pastikan untuk melakukan **Save** perubahan Anda. 

    ![Cuplikan layar halaman pengaturan firewall server SQL dengan aturan IP baru yang disorot.](../images/0506.png)

8. Kembali ke database SQL Anda (geser bilah di bawah ke arah kiri) dan klik **Query Editor (Preview)**. Coba masuk sebagai **sqluser** dengan kata sandi **Pa$$w0rd1234**. Kali ini Anda akan berhasil. Perhatikan bahwa mungkin perlu beberapa menit untuk menyebarkan aturan firewall baru. 

9. Setelah berhasil masuk, panel kueri akan muncul. Masukkan kueri berikut ke panel editor. 

    ```SQL
    SELECT TOP 20 pc.Name as CategoryName, p.name as ProductName
    FROM SalesLT.ProductCategory pc
    JOIN SalesLT.Product p
    ON pc.productcategoryid = p.productcategoryid;
    ```

    ![Cuplikan layar Editor kueri dengan panel kueri dan perintah yang berhasil dijalankan.](../images/0507.png)

10. Klik **Run**, lalu tinjau hasil kueri di panel **Results**. Kueri akan berjalan dengan sukses.

    ![Cuplikan layar panel Editor Kueri database dengan kode SQL telah berhasil dijalankan dan output terlihat di panel hasil.](../images/0508.png)

Selamat! Anda telah membuat database SQL di Azure dan berhasil membuat kueri data dalam database tersebut.

**Catatan**: Untuk menghindari biaya tambahan, Anda dapat secara opsional menghapus grup sumber daya ini. Telusuri grup sumber daya, klik grup sumber daya, lalu klik **Delete resource group**. Verifikasi nama grup sumber daya, lalu klik **Delete**. Pantau **Notifications** untuk melihat bagaimana proses penghapusan.
