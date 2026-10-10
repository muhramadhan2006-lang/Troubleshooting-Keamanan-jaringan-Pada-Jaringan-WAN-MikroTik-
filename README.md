# Troubleshooting-Keamanan-jariringan-Pada-Jaringan-WAN

## Langkah-Langkah Konfigurasi

### 1. Jaringan Internet & DHCP Client
* **Pengerjaan Soal No 4**: IP Address disesuaikan dengan Network yang diberikan ISP.
* **Pengerjaan Soal No 5**: Gateway disesuaikan dengan IP yang diberikan oleh ISP.
* **Langkah 1**: Buka Winbox, arahkan ke menu **IP > DHCP Client**, lalu klik tombol tambah (`+`), pilih `Interface: ether1`, dan klik Apply/OK.
* C:\Users\ASUS\Downloads\SEMINAR proposal (1).png
* **Langkah 2**: Pastikan status DHCP Client berubah menjadi **bound** dan mendapatkan IP dari ISP.

---

### 2. Jaringan Lokal & Wireless (DNS & NTP)
* **Pengerjaan Soal No 1 (DNS)**: 
  * Atur IP Dynamic Servers sesuai DNS dari ISP.
  * Beri centang pada opsi **Allow Remote Requests**.
* **Pengerjaan Soal No 2 (NTP)**: 
  * Masuk ke menu **System > SNTP Client**.
  * Ubah status menjadi **Enabled**.
  * Masukkan Primary dan Secondary NTP Server (misal: `id.pool.ntp.org` dan `asia.pool.ntp.org`).
