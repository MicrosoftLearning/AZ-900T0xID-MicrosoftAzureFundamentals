---
wts:
    title: '12 - Menerapkan Azure Key Vault (5 mnt)'
    module: 'Modul 04: Menjelaskan fitur keamanan umum dan keamanan jaringan'
---
# 12 - Menerapkan Azure Key Vault (5 mnt)

Dalam panduan ini, kita akan membuat Azure Key vault lalu membuat rahasia kata sandi di dalam key vault itu, menyediakan kata sandi yang disimpan dengan aman dan dikelola secara terpusat untuk digunakan dengan aplikasi.

# Tugas 1: Membuat Azure Key Vault 

1. Masuk ke [portal Microsoft Azure](https://portal.azure.com).

2. Dari bilah **All services**, cari dan pilih **Key vaults**, lalu klik **+Add +New +Create**.

3. Konfigurasikan key vault (ganti **xxxx** dengan nama key vault menggunakan huruf dan angka sehingga namanya unik secara global). Gunakan pengaturan default untuk yang lainnya.

    | Setting | Value | 
    | --- | --- |
    | Subscription | **Gunakan default yang ada** |
    | Resource group | **Buat nama grup sumber daya baru** |
    | Key vault name | **keyvaulttestxxx** |
    | Location | **East US** |
    | Pricing tier | **Standard** |
    
    **Perhatian** ganti **xxxx** untuk menemukan nama yang unik.
4. Klik **Review + create**, lalu klk **Create**. 

5. Setelah key vault baru tersedia, klik **Go to reaource**. Atau Anda dapat menemukan key vault baru dengan mencarinya. 

6. Klik pada tab **Overview** key vault dan catat **Vault URI**. Aplikasi yang menggunakan vault Anda melalui REST API akan membutuhkan URI ini.

7. Luangkan waktu sejenak untuk menelusuri beberapa opsi key vault lainnya. Di bawah **Settings** tinjau **Keys**, **Secrets**, **Certificates**, **Access Policies**, **Firewalls and virtual networks**.

    **Catatan**: Akun Azure Anda adalah satu-satunya yang berwenang untuk melakukan operasi di vault baru ini. Anda dapat mengubah ini jika ingin di bagian **Settings**, lalu di bagian **Access policies**.

# Tugas 2: Menambahkan rahasia ke Key Vault
        
Dalam tugas ini, kita akan menambahkan kata sandi ke key vault. 

1. Di bawah **Settings** klik **Secrets**, lalu klik **+ Generate/Import**.

2. Konfigurasikan rahasianya. Biarkan nilai lainnya pada default. Perhatikan bahwa Anda dapat mengatur tanggal aktivasi dan kedaluwarsa. Perhatikan bahwa Anda juga dapat menonaktifkan rahasia.

    | Setting | Value | 
    | --- | --- |
    | Upload options | **Manual** |
    | Name | **ExamplePassword** |
    | Value | **hVFkk96** |

3. Klik **Create**.

4. Setelah rahasia berhasil dibuat, klik pada **ExamplePassword**, dan perhatikan statusnya **Enabled**

5. Pilih rahasia yang baru Anda buat, catat **Secret Identifier**. Ini adalah nilai url yang sekarang dapat Anda gunakan dengan aplikasi. Ini menyediakan kata sandi yang dikelola secara terpusat dan disimpan dengan aman. 

6. Klik tombol **Show Secret Value**, untuk menampilkan kata sandi yang Anda tentukan sebelumnya.


Selamat! Anda telah membuat Azure Key vault, lalu membuat rahasia kata sandi di brankas kunci tersebut, memberikan key vault yang disimpan dengan aman dan dikelola secara terpusat untuk digunakan dengan aplikasi.

**Catatan**: Untuk menghindari biaya tambahan, Anda dapat secara opsional menghapus grup sumber daya ini. Telusuri grup sumber daya, klik grup sumber daya, lalu klik **Delete resource group**. Verifikasi nama grup sumber daya, lalu klik **Delete**. Pantau **Notifications** untuk melihat bagaimana proses penghapusan.
