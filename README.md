# Troubleshooting-Keamanan-jariringan-Pada-Jaringan-WAN

## Langkah-Langkah Konfigurasi

### 1. Jaringan Internet & DHCP Client
* **Pengerjaan Soal No 4**: IP Address disesuaikan dengan Network yang diberikan ISP.
* **Pengerjaan Soal No 5**: Gateway disesuaikan dengan IP yang diberikan oleh ISP.
* **Langkah 1**: Buka Winbox, arahkan ke menu **IP > DHCP Client**, lalu klik tombol tambah (`+`), pilih `Interface: ether1`, dan klik Apply/OK.
* <img width="672" height="275" alt="SEMINAR proposal (1)" src="https://github.com/user-attachments/assets/2a1427b4-950f-42e4-a278-3de72e8563c1" />
* **Langkah 2**: Pastikan status DHCP Client berubah menjadi **bound** dan mendapatkan IP dari ISP.
* <img width="672" height="166" alt="SEMINAR proposal (2)" src="https://github.com/user-attachments/assets/3bb636a7-f874-469c-a21d-b171006b2c0b" />

---

### 2. Jaringan Lokal & Wireless (DNS & NTP)
* **Pengerjaan Soal No 1 (DNS)**: 
  * Atur IP Dynamic Servers sesuai DNS dari ISP.
  * Beri centang pada opsi **Allow Remote Requests**.
  * <img width="602" height="414" alt="SEMINAR proposal (3)" src="https://github.com/user-attachments/assets/64b40ab7-459b-475e-8b07-ebfdd13138e8" />

* **Pengerjaan Soal No 2 (NTP)**: 
  * Masuk ke menu **System > SNTP Client**.
  * Ubah status menjadi **Enabled**.
  * Masukkan Primary dan Secondary NTP Server (misal: `id.pool.ntp.org` dan `asia.pool.ntp.org`).
  * <img width="633" height="400" alt="SEMINAR proposal (4)" src="https://github.com/user-attachments/assets/8386678d-88ae-45c0-a759-5e193edff8de" />

