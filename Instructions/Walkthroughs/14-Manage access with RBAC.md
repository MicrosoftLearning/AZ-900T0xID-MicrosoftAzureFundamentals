---
wts:
    title: '14 - Mengelola akses dengan RBAC (5 menit)'
    module: 'Modul 05: Mendeskripsikan fitur identitas, tata kelola, privasi, dan kepatuhan'
---
# 14 - Mengelola akses dengan RBAC (5 menit)

Dalam panduan ini, kita akan menetapkan peran izin ke sumber daya dan menampilkan log.

# Tugas 1: Menampilkan dan menetapkan peran

Dalam tugas ini, kita akan menetapkan peran Kontributor komputer virtual. 

1. Masuk ke [portal Microsoft Azure](https://portal.azure.com).

2. Dari bilah **All services**, cari dan pilih **Resource groups**, lalu klik **+Add +New +Create**.

3. Buat grup sumber daya baru. Klik **Create** setelah Anda selesai. 

    | Setting | Value |
    | -- | -- |
    | Subscription | **Gunakan default yang tersedia** |
    | Resource group | **myRGRBAC** |
    | Region | **(US) East US** |
   

4. Buat **Review + create**, lalu klk **Create**.

5. **Refresh** halaman grup sumber daya dan klik entri yang mewakili grup sumber daya yang baru dibuat.

6. Klik bilah **Access control (IAM)**, lalu alihkan ke tab **Roles**. Gulir melalui sejumlah besar definisi peran yang tersedia. Gunakan ikon Informasi untuk mendapatkan ide tentang izin setiap peran. Perhatikan juga informasi tentang jumlah pengguna dan grup yang ditetapkan ke setiap peran.
 
![Gambar](https://user-images.githubusercontent.com/89808319/144266949-f19d91ab-31d6-4c8b-af36-c00035925cf0.png)

7. Beralih ke tab **Role assignments** pada bilah **myRGRBAC - Access control (IAM)**, klik **+ Add**, lalu klik **Add role assignment**. Cari peran Kontributor Komputer Virtual dan pilih. Beralih ke tab “Member” dan Tetapkan akses ke: User, group, or service principal. Kemudian, klik + Select members dan ketikkan nama Anda pada fungsi pencarian yang muncul, lalu tekan 'select.' Lalu tekan ‘Review and Assign’

    
    ![Gambar](https://user-images.githubusercontent.com/89808319/144266255-3a0f8574-9358-4c21-8f95-3503747e77c8.png)

 

    **Catatan:** Peran Kontributor komputer virtual memungkinkan Anda mengelola komputer virtual, tetapi tidak mengakses sistem operasinya atau mengelola jaringan virtual dan akun penyimpanan tempat itu tersambung.

  

8. **Refresh** halaman Penetapan peran dan pastikan Anda sekarang terdaftar sebagai Kontributor komputer virtual. 

    **Catatan**: Penugasan ini ini sebenarnya tidak memberikan hak istimewa tambahan apa pun, karena akun Anda sudah memiliki peran Pemilik, yang mencakup semua hak istimewa yang terkait dengan peran Kontributor.

# Tugas 2: Memantau penetapan peran dan menghapus peran

Dalam tugas ini, kita akan menampilkan log aktivitas untuk memverifikasi penetapan peran, lalu menghapus peran tersebut. 

1. Pada bilah grup sumber daya myRGRBAC, klik **Activity log**.

2. Klik **Add filter**, pilih **Operation**, lalu **Create role assignment**.

    ![Cuplikan layar halaman Log aktivitas dengan filter yang dikonfigurasi.](../images/1503.png)

3. Periksa bahwa Log aktivitas menunjukkan penetapan peran Anda. 

    **Catatan**: Dapatkah Anda mengetahui cara menghapus penetapan peran Anda?

Selamat! Anda telah membuat grup sumber daya, menetapkan peran akses kepadanya, dan melihat log aktivitas. 

**Catatan**: Untuk menghindari biaya tambahan, Anda dapat secara opsional menghapus grup sumber daya ini. Telusuri grup sumber daya, klik grup sumber daya, lalu klik **Delete resource group**. Verifikasi nama grup sumber daya, lalu klik **Delete**. Pantau **Notifications** untuk melihat bagaimana proses penghapusan.

