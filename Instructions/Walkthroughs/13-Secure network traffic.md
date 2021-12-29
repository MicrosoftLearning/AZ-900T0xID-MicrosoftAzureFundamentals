---
wts:
    title: '13 - Mengamankan lalu lintas jaringan (10 menit)'
    module: 'Modul 04: Menjelaskan fitur keamanan umum dan keamanan jaringan'
---
# 13 - Mengamankan lalu lintas jaringan (10 menit)

Dalam panduan ini, kita akan mengonfigurasi kelompok keamanan jaringan.

# Tugas 1: Menciptakan komputer virtual

Dalam tugas ini, kita akan membuat komputer virtual Windows Server 2019 Datacenter. 

1. Masuk ke [portal Microsoft Azure](https://portal.azure.com).

2. Dari bilah **All services**, cari dan pilih **Virtual machines**, lalu klik **+ Add, + Create, + New** Komputer Virtual.

3. Pada tab **Basics**, isi informasi berikut (biarkan default untuk yang lainnya):

    | Settings | Values |
    |  -- | -- |
    | Subscription | **Gunakan default yang tersedia** |
    | Resource group | **Buat nama grup sumber daya baru** |
    | Virtual machine name | **SimpleWinVM** |
    | Region | **(US) East US**|
    | Image | **Windows Server 2019 Datacenter Gen 2**|
    | Size | **Standard D2s v3**|
    | Administrator account username | **azureuser** |
    | Administrator account password | **Pa$$w0rd1234**|
    | Inbound port rules | **None**|

4. Beralih ke tab **Networking**, dan konfigurasikan pengaturan berikut:

    | Settings | Values |
    | -- | -- |
    | NIC network security group | **None**|

5. Beralih ke tab **Management**, dan di bagian **Monitoring**, pilih pengaturan berikut:

    | Settings | Values |
    | -- | -- |
    | Boot diagnostics | **Disable**|

6. Biarkan default yang tersisa lalu klik tombol **Review + create** di bagian bawah halaman.

7. Setelah melewati proses Validasi, klik tombol **Create**. Diperlukan waktu sekitar lima menit untuk menyebarkan komputer virtual.

8. Pantau penyebarannya. Mungkin perlu beberapa menit untuk membuat grup sumber daya dan komputer virtual. 

9. Dari bilah deployment atau dari area Notification, klik **Go to resource**. 

10. Pada bilah komputer virtual **SimpleWinVM**, klik **Networking**, tinjau tab **Inbound port rules**, dan perhatikan bahwa tidak ada kelompok keamanan jaringan yang terkait dengan antarmuka jaringan dari komputer virtual atau subnet tempat antarmuka jaringan dikaitkan.

    **Catatan**: Identifikasi nama antarmuka jaringan. Anda akan membutuhkannya di tugas berikutnya.

# Tugas 2: Membuat kelompok keamanan jaringan

Dalam tugas ini, kami akan membuat kelompok keamanan jaringan dan mengaitkannya dengan antarmuka jaringan.

1. Dari bilah **All services**, cari dan pilih **Network security groups**, lalu klik **+ Add, + Create, + New**

2. Pada tab **Basics** dari bilah **Create network security groups** tentukan pengaturan berikut.

    | Setting | Value |
    | -- | -- |
    | Subscription | **Gunakan langganan default** |
    | Resource group | **Pilih default dari menu tarik-turun** |
    | Name | **myNSGSecure** |
    | Region | **(US) East US**  |

3. Klik **Review + create** lalu setelah validasi, klik **Create**.

4. Setelah NSG dibuat, klik **Go to resource**.

5. Di **Settings**, klik **Network interfaces**, lalu **Associate**.

6. Pilih antarmuka jaringan yang Anda identifikasi di tugas sebelumnya. 

# Tugas 3: Mengonfigurasi aturan port keamanan masuk untuk mengizinkan RDP

Dalam tugas ini, kita akan mengizinkan lalu lintas RDP ke komputer virtual dengan mengonfigurasi aturan port keamanan masuk. 

1. Di portal Microsoft Azure, navigasikan ke bilah komputer virtual **SimpleWinVM**. 

2. Di panel **Overview**, klik **Connect**.

3. Coba hubungkan ke komputer virtual dengan memilih RDP dan mengunduh file RDP yang berjalan. Secara default, kelompok keamanan jaringan tidak mengizinkan RDP. Tutup jendela kesalahan. 


    ![Cuplikan layar dari pesan kesalahan bahwa koneksi komputer virtual telah gagal.](../images/1201.png)

4. Pada bilah komputer virtual, gulir turun ke bagian **Settings**, klik **Networking**, dan perhatikan aturan masuk untuk kelompok keamanan jaringan **myNSGSecure (attached to network interface: myVMNic)** menolak semua lalu lintas masuk kecuali lalu lintas dalam jaringan virtual dan probe penyeimbang beban.

5. Di tab **Inbound port rules**, klik **Add inbound port rules**. Klik **Add** setelah Anda selesai. 

    | Setting | Value |
    | -- | -- |
    | Source | **Any**|
    | Source port ranges | **\*** |
    | Destination | **Any** |
    | Destination port ranges | **3389** |
    | Protocol | **TCP** |
    | Pusat | **Allow** |
    | Priority | **300** |
    | Name | **AllowRDP** |

6. Pilih **Add** dan menunggu aturan untuk ditetapkan, kemudian coba lagi RDP ke komputer virtual dengan kembali ke **Connect**. Kali ini Anda harus berhasil. Ingat bahwa pengguna adalah **azureuser** dan kata sandinya adalah **Pa$$w0rd1234**.

# Tugas 4: Mengonfigurasi aturan port keamanan keluar untuk menolak akses Internet.

Dalam tugas ini, kita akan membuat aturan port keluar NSG yang akan menolak akses Internet, lalu mengujinya untuk memastikan aturan tersebut berfungsi.

1. Lanjutkan di sesi RDP komputer virtual Anda. 

2. Setelah komputer menyala, buka browser **Internet Explorer**. 

3. Pastikan Anda dapat mengakses **https://www.bing.com**, lalu tutup Internet Explorer. Anda perlu bekerja melalui pop-up keamanan yang ditingkatkan IE. 

    **Catatan**: Sekarang kita akan mengonfigurasi aturan untuk menolak akses internet keluar. 

4. Kembali di portal Microsoft Azure, navigasikan kembali ke bilah komputer virtual **SimpleWinVM**. 

5. Di bawah **Settings**, klik **Networking**, lalu **Outbond port rules**.

6. Perhatikan ada aturan, **AllowInternetOutbound**. Ini adalah aturan default dan tidak dapat dihapus. 

7. Klik **Add outbond port rules** di sebelah kanan kelompok keamanan jaringan **myNSGSecure (attached to network interface: myVMNic)** dan konfigurasikan aturan keamanan keluar baru dengan prioritas lebih tinggi yang akan menolak lalu lintas internet. Klik **Add** setelah Anda selesai. 

    | Setting | Value |
    | -- | -- |
    | Source | **Any**|
    | Source port ranges | **\*** |
    | Destination | **Service Tag** |
    | Destination service tag | **Internet** |
    | Destination port ranges | **\*** |
    | Protocol | **TCP** |
    | Pusat | **Deny** |
    | Priority | **4000** |
    | Name | **DenyInternet** |

8. Klik **Add** Kembali ke VM RDP Anda. 

9. Telusuri ke **https://www.microsoft.com**. Halaman semestinya tidak ditampilkan. Anda mungkin perlu bekerja melalui pop-up keamanan tambahan yang ditingkatkan IE.  

**Catatan**: Untuk menghindari biaya tambahan, Anda dapat secara opsional menghapus grup sumber daya ini. Telusuri grup sumber daya, klik grup sumber daya, lalu klik **Delete resource group**. Verifikasi nama grup sumber daya, lalu klik **Delete**. Pantau **Notifications** untuk melihat bagaimana proses penghapusan.
