---
wts:
    title: '04 - Membuat jaringan virtual (20 menit)'
    module: 'Modul 02 – Layanan Core Azure (Beban Kerja)'
---
# 04 - Membuat jaringan virtual (20 menit)

Dalam panduan ini, kita akan membuat jaringan virtual, menyebarkan dua komputer virtual ke jaringan virtual tersebut, lalu mengonfigurasinya untuk mengizinkan satu komputer virtual melakukan ping ke komputer virtual lain di dalam jaringan virtual tersebut.

# Tugas 1: Menciptakan jaringan virtual 

Dalam tugas ini, kita akan membuat jaringan virtual. 

Catatan: Sebelum lab dimulai, nonaktifkan firewall publik maupun privat di komputer virtual dengan membuka menu Start > Pengaturan > Jaringan dan Internet > Cari Windows Firewall

1. Masuk ke portal Microsoft Azure di <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. Dari bilah **All services**, cari dan pilih **Virtual networks**, lalu klik **+ Add, + Create, + New**. 

3. Pada tab **Basics**, isi informasi berikut (biarkan default untuk yang lainnya):

    | Setting | Value | 
    | --- | --- |
    | Subscription | **Biarkan default yang tersedia** |
    | Resource Group | **Buat nama grup sumber daya baru** |
    | Name | **vnet1** |
    | Region | **(US) East US** |
    
   
4. Klik tombol **Review + create**. Pastikan validasi lolos. Lalu tekan buat untuk menyebarkan sumber daya.


# Tugas 2: Membuat dua komputer virtual

Dalam tugas ini, kita akan membuat dua komputer virtual di jaringan virtual. 

1. Dari bilah **All services**, cari dan pilih **Virtual machines.**, lalu klik **+ Add, + Create, + New**, dari menu tarik turun pilih **Virtual Machine**. 

2. Pada tab **Basics**, isi informasi berikut (biarkan default untuk yang lainnya):

   | Setting | Value | 
   | --- | --- |
   | Subscription | **Gunakan default yang ada** |
   | Resource group |  **Pilih default di menu tarik turun** |
   | Virtual machine name | **vm1**|
   | Region | **(US) East US** |
   | Image | **Windows Server 2019 Datacenter - Gen2** |
   | Username| **azureuser** |
   | Password| **Pa$$w0rd1234** |
   | Public inbound ports| Pilih **Allow selected ports**  |
   | Selected inbound ports| **RDP (3389)** |
   

3. Pilih tab **Networking**. Pastikan komputer virtual ditempatkan di jaringan virtual **vnet1**. Tinjau pengaturan default, tetapi jangan lakukan perubahan apa pun. 

4. Klik **Review + create**. Setelah Validasi lolos, klik **Create**. Waktu penyebaran dapat berbeda-beda, tetapi biasanya perlu waktu antara tiga hingga enam menit untuk disebarkan.

5. Pantau penyebaran Anda, tetapi lanjutkan ke langkah berikutnya. 

6. Buat komputer virtual kedua dengan mengulangi langkah **2 hingga 4** di atas. Pastikan Anda menggunakan nama komputer virtual yang berbeda, komputer virtual tersebut berada dalam jaringan virtual yang sama, dan menggunakan alamat IP publik yang baru:

    | Setting | Value |
    | --- | --- |
    | Resource group | **pilih default di menu tarik-turun (sama seperti Tugas 1-3 & Tugas 2-2)** |
    | Virtual machine name |  **vm2** |
    | Virtual network | **vnet1** |
    | Public IP | **vm2-ip** |

7. Tunggu semua komputer virtual menerapkan dan statusnya menjadi *berjalan*.

# Tugas 3: Menguji koneksi 

Pada tugas ini, kita akan coba menguji apakah komputer virtual dapat berkomunikasi (ping) dengan satu sama lain. Jika tidak, kita akan menginstal aturan untuk memungkinkan koneksi ICMP. Biasanya koneksi ICMP otomatis diblokir.

1. Dari bilah **All resource**, cari **vm1**, buka bilah **Overview**, dan pastikan **Status** adalah **Running**. Anda mungkin perlu melakukan **Refresh** halamannya.

2. Di bilah **Overview**, pilih **Connect**, lalu pilih **RDP** dari menu tarik turun.

    **Catatan**: Petunjuk berikut memberi tahu Anda cara menyambungkan ke komputer virtual dari komputer Windows. 

3. Di bilah **Connect RDP**, biarkan opsi default untuk terhubung dengan alamat IP melalui port 3389 dan klik **Download RDP File**.

4. Buka file RDP yang diunduh (ada di sebelah kiri bawah VM Anda) dan klik **Connect** bila diminta. 

5. Di jendela **Windows Security**, ketik nama pengguna **azureuser** dan kata sandi **Pa$$w0rd1234**, lalu klik **OK**.

6. Anda mungkin menerima peringatan sertifikat selama proses masuk. Klik **Yes** untuk membuat koneksi dan menghubungkan ke komputer virtual yang disebarkan. Anda akan berhasil tersambung. Tutup Windows Server dan jendela Dasbor yang muncul. Anda akan melihat latar belakang Windows Biru. Kini Anda berada di komputer virtual.

7. Di komputer virtual yang baru dibuat, nonaktifkan firewall publik maupun privat dengan membuka menu Start > Pengaturan > Jaringan dan Internet > Cari Windows Firewall

8. Buka PowerShell di komputer virtual dengan mengklik tombol **Start**, dan di Pencarian, ketikkan **PowerShell**, klik kanan **Windows PowerShell**, lalu **Run as administrator**

9. Di Powershell, coba lakukan ping ke vm2 dengan mengetikkan:

   ```PowerShell
   ping vm2
   ```

 10. Anda akan berhasil. Anda telah melakukan ping ke VM2 dari VM1.


**Selamat!** Anda telah mengonfigurasi dan menyebarkan dua komputer virtual di sebuah jaringan virtual, lalu Anda telah dapat menghubungkan keduanya.

**Catatan**: Untuk menghindari biaya tambahan, Anda dapat secara opsional menghapus grup sumber daya ini. Telusuri grup sumber daya, klik grup sumber daya, lalu klik **Delete resource group**. Verifikasi nama grup sumber daya, lalu klik **Delete**. Pantau **Notifications** untuk melihat bagaimana proses penghapusan.
