---
wts:
    title: '07 - Menerapkan Azure IoT Hub (10 mnt)'
    module: 'Modul 03: Menjelaskan solusi inti dan alat manajemen'
---
# 07 - Menerapkan Azure IoT Hub

Dalam panduan ini, kita akan mengonfigurasi Azure IoT Hub baru di Portal Microsoft Azure, lalu mengautentikasi koneksi ke perangkat IoT menggunakan simulator perangkat Raspberry Pi online. Data sensor dan pesan diteruskan dari simulator Raspberry Pi ke Azure IoT Hub, dan Anda melihat metrik untuk aktivitas pengiriman pesan di Portal Microsoft Azure.

# Tugas 1: Membuat IoT hub (10 mnt)

Dalam tugas ini, kita akan membuat IoT hub. 

1. Masuk ke [portal Microsoft Azure](https://portal.azure.com).

2. Dari bilah **All services**, cari dan pilih **IoT Hub**, lalu klik **+ Add, + Create, atau + New**.

3. Pada tab **Basics** dari bilah **IoT hub**, isi bidang dengan detail berikut (ganti **xxxx** dalam nama akun penyimpanan dengan huruf dan angka sehingga namanya unik secara global):

    | Settings | Value |
    |--|--|
    | Subscription | **Pilih langganan Anda** |
    | Resource Group |  **myRGIoT** (buat baru)|
    | Region | **East US** |
    | IoT Hub Name | **my-hub-groupxxxx** |
    | | |

    **Catatan** - Ingatlah untuk mengubah **xxxx** sehingga itu membuat **Nama IoT Hub** yang unik.

4. Buka tab **Management**, dan gunakan daftar menurun untuk mengatur **Pricing and scale tier** ke **S1: Standard tier**.

5. Klik tombol **Review + create**.

6. Klik tombol **Create** untuk mulai membuat instans Azure IoT Hub baru.

7. Tunggu hingga instans Azure IoT Hub disebarkan. 

# Tugas 2: Menambahkan perangkat IoT

Dalam tugas ini, kita akan menambahkan perangkat IoT ke IoT hub. 

1. Saat penyebaran telah selesai, klik **Go to resource** dari bilah deployment. Atau, dari bilah **All services**, cari dan pilih **IoT Hub** dan temukan instans IoT Hub baru

	![Cuplikan layar penyebaran sedang berlangsung dan penyebaran berhasil pemberitahuan di portal Microsoft Azure.](../images/0601.png)

2. Untuk menambahkan perangkat IoT baru, gulir ke bawah ke bagian **Explorer** dan klik **IoT Devices**. Lalu, klik **+ New**.

	![Cuplikan layar panel perangkat IoT, yang disorot dalam bilah navigasi hub IoT, di portal Microsoft Azure. Tombol New disorot untuk mengilustrasikan cara menambahkan identitas perangkat IoT baru ke IoT hub.](../images/0602.png)

3. Berikan nama untuk perangkat IoT yang baru, **myRaspberryPi**, dan klik tombol **Save**. Pemberian nama ini akan membuat identitas perangkat IoT baru di Azure IoT Hub.

4. Jika Anda tidak melihat perangkat baru, **Refresh** halaman Perangkat IoT. 

5. Pilih **myRaspberryPi** dan salin nilai **Primary Connection String**. Anda akan menggunakan kunci ini di tugas berikutnya untuk mengautentikasi koneksi ke simulator Raspberry Pi.

	![Cuplikan layar halaman String Koneksi Utama dengan ikon salin disorot.](../images/0603.png)

# Tugas 3: Menguji perangkat menggunakan Simulator Raspberry Pi

Dalam tugas ini, kita akan menguji perangkat menggunakan Simulator Raspberry Pi. 

1. Buka tab baru di browser web dan telusuri ke [simulator Raspberry Pi online](https://azure-samples.github.io/raspberry-pi-web-simulator/#Getstarted). 

2. Baca tentang simulator Raspberry Pi. Jika ada pop-up ringkasan pilih "**X**" untuk menutup jendela.

3. Di area kode, sisi kanan, cari baris dengan 'const connectionString ='. Gantilah dengan string koneksi yang Anda salin dari portal Microsoft Azure. Perhatikan bahwa string koneksi menyertakan entri DeviceId (**myRaspberryPi**) dan SharedAccessKey.

	![Cuplikan layar area pengodean dalam simulator Raspberry Pi.](../images/0604.png)

4. Klik **Run** (di bawah area kode) untuk menjalankan aplikasi. Output konsol harus menampilkan data sensor dan pesan yang dikirim dari simulator Raspberry Pi ke Azure IoT Hub. Data dan pesan dikirim setiap kali LED simulator Raspberry Pi berkedip. 

	![Cuplikan layar konsol simulator Raspberry Pi.  Output konsol menampilkan data sensor dan pesan yang dikirim dari simulator Raspberry Pi ke Azure IoT Hub.](../images/0605.png)

5. Klik **Stop** untuk berhenti mengirim data.

6. Kembali ke portal Microsoft Azure dan IoT Hub.

7. Alihkan bilah **Overview** IoT Hub dan gulir ke bawah ke informasi **IoT Hub Usage**.

	![Cuplikan layar metrik dalam area penggunaan IoT hub portal Microsoft Azure.](../images/0606.png)


Selamat! Anda telah menyiapkan Azure IoT Hub untuk mengumpulkan data sensor dari perangkat IoT.

**Catatan**: Untuk menghindari biaya tambahan, Anda dapat menghapus grup sumber daya ini. Telusuri grup sumber daya, klik grup sumber daya, lalu klik **Delete resource group**. Pastikan nama grup sumber daya lalu klik **Delete**. Pantau **Notifications** untuk melihat bagaimana proses penghapusan.
