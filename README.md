# Troubleshooting-Keamanan-jariringan-Pada-Jaringan-WAN
## 📋 Daftar & Ketentuan 

### 1. Konfigurasi Wifi Router
1. **DNS** = Sesuai dengan DNS yang diberikan ISP[cite: 6].
2. **NTP** = Yes[cite: 6].
3. **Web Proxy dengan Cache Administrator** = `nama_peserta@sekolah.sch.id`[cite: 6] *(sesuaikan dengan nama dan sekolah kamu)*.

### 2. Jaringan Internet
4. **IP Address** = Sesuai dengan Network yang diberikan ISP[cite: 6].
5. **Gateway** = Sesuai dengan IP yang diberikan oleh ISP[cite: 6].

### 3. Jaringan Lokal
6. **IP Address** = 192.168.100.1/25[cite: 6].
7. **DHCP Pool** = Sebanyak 99 Client[cite: 6].
8. Buat firewall agar IP `192.168.100.2 - 192.168.100.50` tidak dapat ping ke router[cite: 6].
9. Buat firewall agar IP `192.168.100.51 - 192.168.100.100` tidak dapat ping ke client wireless[cite: 6].
10. Buat rule agar setiap akses ke router tercatat di logging dan tersimpan di disk[cite: 6].

### 4. Jaringan Wireless
11. **IP Address** = 192.168.200.1/24[cite: 6].
12. **SSID** = `nama_peserta@ProxyUKK`[cite: 6] *(sesuaikan dengan nama kamu)*.
13. **DHCP Pool** = Sebanyak 99 client[cite: 6].
14. Membuat 20 account hotspot secara random di RADIUS[cite: 6].
15. Account hotspot hanya bisa menggunakan internet pada pukul 07.00 - 16.00[cite: 6].

### 5. Blocking (Firewall)
Buat firewall yang memblokir[cite: 6]:
16. **Blocking Site** = `https://www.linux.org`[cite: 6].
17. **Blocking File** = `.mp3, .mkv`[cite: 6].

---

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

