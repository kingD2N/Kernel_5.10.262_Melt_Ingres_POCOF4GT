<div align="center">


<img width="1380" height="752" alt="1000339818" src="https://github.com/user-attachments/assets/9c288842-4114-44fd-841f-7ee013dd8094" />

#     ✧ Kernel Melt Rebase ✧

#   ✧ For POCO F4 GT (ingres) ✧

[![Build](https://img.shields.io/badge/GitHub_Actions-CI_Builder-2088FF?logo=githubactions&logoColor=white)](https://github.com/kingD2N/Kernel_5.10.261_Melt_Ingres_POCOF4GT/actions)
[![KernelSU](https://img.shields.io/badge/KernelSU-Supported-4CAF50?logo=linux&logoColor=white)](https://github.com/tiann/KernelSU)
[![KernelSU-Next](https://img.shields.io/badge/KernelSU--Next-Supported-4CAF50?logo=linux&logoColor=white)](https://github.com/KernelSU-Next/KernelSU-Next)
[![SukiSU Ultra](https://img.shields.io/badge/SukiSU_Ultra-Supported-4CAF50?logo=linux&logoColor=white)](https://github.com/SukiSU-Ultra/SukiSU-Ultra)
[![ReSukiSU](https://img.shields.io/badge/ReSukiSU-Supported-4CAF50?logo=linux&logoColor=white)](https://github.com/ReSukiSU/ReSukiSU)
[![SUSFS](https://img.shields.io/badge/SUSFS-v2.2.0-FF6D00?logo=gitlab&logoColor=white)](https://gitlab.com/simonpunk/susfs4ksu)
[![Device](https://img.shields.io/badge/Device-POCO_F4_GT_%2F_Redmi_K50G-EF5350)](https://github.com/mohdakil2426/android_kernel_xiaomi_marble)
[![ROM](https://img.shields.io/badge/ROM-AOSP_&_HyperOS-FF6900)](https://www.mi.com/global/hyperos/)

## 📖 Apa Itu Kernel Custom?

Kernel adalah lapisan inti (core) sistem operasi Android yang menjadi jembatan komunikasi antara hardware perangkat (CPU, GPU, RAM, sensor, modem, dll) dengan software di atasnya (Android framework dan aplikasi). Kernel Android merupakan turunan Linux kernel yang dimodifikasi oleh Google (AOSP) dan vendor SoC seperti Qualcomm.

**Kernel custom** adalah kernel hasil modifikasi dari kernel stock/bawaan pabrikan (dalam hal ini Xiaomi/POCO), yang dikembangkan ulang oleh developer independen untuk menambah fitur, melakukan optimasi, atau menutupi kekurangan kernel bawaan.

### Fitur Umum yang Dibawa Kernel Custom

- **Root solution** — dukungan KernelSU, KernelSU-Next, SukiSU Ultra, ReSukiSU untuk akses root tanpa mem-patch partisi system
- **SUSFS** — menyamarkan status root dari deteksi aplikasi (Play Integrity, aplikasi perbankan, dll)
- **CPU Governor tambahan** — skema pengaturan clock speed processor (schedutil, performance, powersave, walt, dll)
- **I/O Scheduler tambahan** — mengatur antrian baca/tulis storage (cfq, bfq, kyber, mq-deadline dll.)
- **TCP congestion control** — misalnya BBR untuk optimasi throughput jaringan
- **Tuning thermal & baterai** — kontrol suhu dan penghematan daya yang lebih agresif atau longgar
- **Mode performa gaming** — tweak tambahan seperti penyesuaian refresh rate/FPS
- Patch keamanan tambahan dan perbaikan bug driver

### Kelebihan

- Kontrol lebih besar atas performa dan efisiensi baterai
- Dukungan root modern yang lebih tersembunyi dari deteksi aplikasi
- Fitur networking dan tweak yang tidak tersedia di kernel stock

### Risiko

- Berpotensi bootloop bila kernel tidak cocok dengan base ROM
- Dapat menghilangkan garansi resmi (unlock bootloader umumnya membatalkan garansi)
- Berisiko kehilangan data bila proses flashing gagal tanpa backup
- Kestabilan bergantung pada kualitas kerja developer komunitas, bukan QC pabrikan

---

## ⚠️ Hal yang Wajib Diperhatikan Sebelum Flash Kernel Custom

1. **Cocokkan versi ROM dan base kernel** — pastikan ROM (AOSP/HyperOS/MIUI) memakai base kernel yang sama dengan kernel yang akan di-flash (misalnya Linux 5.10.262 pada project ini). Base yang berbeda berisiko bootloop.
2. **Bootloader harus sudah unlock** — flashing kernel custom mengharuskan bootloader dalam kondisi unlocked.
3. **Backup partisi penting** — backup `boot`, (via TWRP atau fastboot) sebelum flashing, serta backup data pribadi karena tetap ada risiko.
4. **Cek kompatibilitas solusi root** — jangan memasang Magisk dan KernelSU manager berbarengan tanpa memahami cara kerja masing-masing; pilih salah satu yang sesuai dengan varian kernel.
5. **Baca changelog & requirement rilis** — setiap rilis kernel custom biasanya mencantumkan requirement (versi ROM minimum, perlu format data atau tidak) di halaman release GitHub.
6. **Siapkan jalur recovery** — pastikan tahu cara kembali ke kernel/boot image stock bila terjadi bootloop, misalnya `fastboot flash boot boot.img` dengan file original atau reflash ROM penuh.
7. **Baterai minimal 50%** — hindari flashing saat baterai rendah agar device tidak mati mendadak selama proses.
8. **Gunakan tool sesuai format rilis** — via fastboot (`fastboot flash boot boot.img`) untuk image, atau via AnyKernel3 zip lewat custom recovery (TWRP) sesuai format rilis kernel.
9. **Pahami tanggung jawab pengguna** — kernel custom dibuat oleh developer komunitas, bukan resmi Xiaomi/POCO, sehingga risiko sepenuhnya ditanggung pengguna sendiri.

---

## 📱 Tentang Perangkat: POCO F4 GT (ingres)

| Spesifikasi | Detail |
|---|---|
| Nama global | POCO F4 GT |
| Nama China | Redmi K50 Gaming Edition (K50G) |
| Codename | **ingres** |
| Chipset | Qualcomm Snapdragon 8 Gen 1 (SM8450), fabrikasi 4nm |
| CPU | 1× Cortex-X2 (3.0GHz) + 3× Cortex-A710 (2.5GHz) + 4× Cortex-A510 (1.8GHz) |
| GPU | Adreno 730 |
| Layar | AMOLED 6.67", 120Hz |
| Baterai | 4700 mAh, fast charging 120W |
| Android rilis awal | Android 12 (MIUI 13) |
| Basis kernel | Linux 5.10.x (GKI 2.0 compliant) |

### Kenapa Codename "ingres" Penting?

Codename **ingres** adalah identitas internal perangkat yang membedakan source code, driver, dan device tree POCO F4 GT/Redmi K50G dari device Snapdragon 8 Gen 1 lain (misalnya "diting" untuk Redmi K50 Pro+). Saat memilih kernel custom, ROM, atau TWRP, kecocokan dengan codename **ingres** wajib dipastikan — kernel/ROM dengan chipset sama tapi codename berbeda tetap berisiko tidak kompatibel karena perbedaan driver kamera, layar, fingerprint, dan tata letak partisi.

### Karakteristik Kernel pada ingres

- Menggunakan **GKI (Generic Kernel Image)** sejak rilis dengan Android 12, sehingga kernel image terpisah dari modul vendor (`vendor_boot`, `vendor_dlkm`)
- Base kernel **Linux 5.10.262**, sesuai penamaan repository project ini
- Modul vendor harus cocok `vermagic` dan versi symbol-nya agar dapat dimuat oleh kernel custom
- Chipset SM8450 dikenal memiliki karakteristik thermal yang cukup panas, sehingga tuning CPU governor dan thermal pada kernel custom sangat berpengaruh terhadap pengalaman gaming di perangkat ini

</div>
<div align="center">

#  ✧ Credits ✧

 **Pzqqt** — upstream Marble kernel source and maintenance
 
 **osm0sis** — AnyKernel3 flashing framework
 
 **tiann** — KernelSU
 
**KernelSU-Next team** — KernelSU-Next

 **SukiSU Ultra team** — SukiSU Ultra
 
 **ReSukiSU team** — ReSukiSU
 
 **simonpunk** — susfs4ksu patches
 
 **WildKernels** — reference CI and release patterns
 
 Xiaomi/MIUI kernel source maintainers

---

<div align="center">

•Special thanks to @Pzqqt, @Yudharn @Mahdi_48111 @itzParsaYC @n08i40k, @Rafaelgh, @Gurinbone01, @ArianK16a, Ingres-Centre team, AOSP-Lineage Team & community

</div>

---
