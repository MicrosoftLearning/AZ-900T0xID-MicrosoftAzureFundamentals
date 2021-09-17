---
wts:
    title: '20 - Menggunakan Kalkulator Azure TCO (10 mnt)'
    module: 'Modul 06: Menjelaskan manajemen biaya dan persetujuan tingkat layanan Azure'
---
# 20 - Menggunakan Kalkulator Azure TCO (10 mnt)


Dalam panduan ini, Anda akan menggunakan Kalkulator Total Biaya Kepemilikan (TCO) guna menghasilkan laporan perbandingan biaya untuk lingkungan lokal.

**Catatan**: Panduan ini memberikan contoh definisi infrastruktur lokal dan beban kerja untuk pusat data yang khas. Untuk membuat laporan Kalkulator TCO, gunakan definisi contoh atau berikan detail infrastruktur dan beban kerja lokal Anda *yang sebenarnya*.

# Tugas 1: Mengonfigurasi kalkulator TCO

Dalam tugas ini, kami akan menambahkan informasi infrastruktur ke kalkulator. 

1. Di browser, buka halaman [Kalkulator Total Biaya Kepemilikan (TCO)](https://azure.microsoft.com/id-id/pricing/tco/calculator/).

2. Untuk menambahkan detail infrastruktur lokal Anda, klik **+ Add server workload** di panel **Define your workloads**.

    | Settings | Value |
    | -- | -- |
    | Name | **Server: Windows VMs** |
    | Workload | **Windows/Linux server** |
    | Environment | **Virtual Machines** |
    | Operating system | **Windows** |  
    | VMs | **50** |
    | Virtualization | **Hyper-V** |
    | Core(s) | **8**|
    | RAM (GB) | **16** |
    | Optimize by | **CPU** |
    | Windows Server 2008/2008 R2 | **Off** |

3. Pilih **+ Add server workload** untuk membuat baris definisi beban kerja server yang baru. 

    | Settings | Value |
    | -- | -- |
    | Name | **Server: Linux VMs** |
    | Workload | **Windows/Linux server** |
    | Environment | **Virtual Machines** |
    | Operating system | **Linux** |  
    | VMs | **50** |
    | Virtualization | **VMware** |
    | Core(s) | **8**|
    | RAM (GB) | **16** |
    | Optimize by | **CPU** |
    | Windows Server 2008/2008 R2 | **Off** |

4. Di panel **Storage**, klik **Add storage**.

    | Settings | Value |
    | -- | -- |
    | Name | **Server Storage** |
    | Storage type | **Local Disk/SAN** |
    | Disk type | **HDD** |
    | Capacity | **60 TB** |  
    | Backup | **120 TB** |
    | Archive | **0 TB** |

5. Di panel **Networking**, tambahkan bandwidth. 

    | Settings | Value |
    | -- | -- |
    | Outbound bandwidth | 15 TB|

6. Klik **Next**.

7. Jelajahi opsi dan buat penyesuaian yang Anda butuhkan. 

    | Settings | Value |
    | -- | -- |
    | Currency | **Euro** |

8. Klik **Next**.

# Tugas 2: Meninjau hasil dan menyimpan salinannya

Dalam tugas ini, kami akan meninjau rekomendasi penghematan biaya dan mengunduh laporan. 

1. Tinjau rekomendasi dan visualisasi penghematan biaya Azure.

    | Settings | Value |
    | -- | -- |
    | Timeframe| **3 years** |
    | Region | **North Europe** |

2. Untuk mengubah informasi yang Anda berikan, pergi ke bagian bawah halaman, dan klik **Back**. 

3. Untuk menyimpan atau mencetak salinan PDF laporan, klik **Download**.

    ![Cuplikan layar dari panel laporan kalkulator tco di Azure. Kolom masukan yang disorot dan diisi menunjukkan cara mengatur jangka waktu kalkulator tco menjadi tiga tahun dan kawasan ke eropa utara. Grafik memperlihatkan biaya infrastruktur lokal dan beban kerja yang disesuaikan dengan pengurangan biaya penggunaan Azure.](../images/2001.png)

Selamat! Anda telah menggunakan Kalkulator TCO guna membuat laporan perbandingan biaya untuk lingkungan lokal.
