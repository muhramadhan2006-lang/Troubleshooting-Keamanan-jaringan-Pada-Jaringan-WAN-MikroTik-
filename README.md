# Troubleshooting-Keamanan-jariringan-Pada-Jaringan-WAN
## 📋 Daftar & Ketentuan 

### Konfigurasi Wifi Router
1. **DNS** = Sesuai dengan DNS yang diberikan ISP[cite: 6].
2. **NTP** = Yes[cite: 6].
3. **Web Proxy dengan Cache Administrator** = `nama_peserta@sekolah.sch.id`[cite: 6] *(sesuaikan dengan nama dan sekolah kamu)*.

### Jaringan Internet
4. **IP Address** = Sesuai dengan Network yang diberikan ISP[cite: 6].
5. **Gateway** = Sesuai dengan IP yang diberikan oleh ISP[cite: 6].

### Jaringan Lokal
6. **IP Address** = 192.168.100.1/25[cite: 6].
7. **DHCP Pool** = Sebanyak 99 Client[cite: 6].
8. Buat firewall agar IP `192.168.100.2 - 192.168.100.50` tidak dapat ping ke router[cite: 6].
9. Buat firewall agar IP `192.168.100.51 - 192.168.100.100` tidak dapat ping ke client wireless[cite: 6].
10. Buat rule agar setiap akses ke router tercatat di logging dan tersimpan di disk[cite: 6].

### Jaringan Wireless
11. **IP Address** = 192.168.200.1/24[cite: 6].
12. **SSID** = `nama_peserta@ProxyUKK`[cite: 6] *(sesuaikan dengan nama kamu)*.
13. **DHCP Pool** = Sebanyak 99 client[cite: 6].
14. Membuat 20 account hotspot secara random di RADIUS[cite: 6].
15. Account hotspot hanya bisa menggunakan internet pada pukul 07.00 - 16.00[cite: 6].

### Blocking (Firewall)
Buat firewall yang memblokir[cite: 6]:
16. **Blocking Site** = `https://www.linux.org`[cite: 6].
17. **Blocking File** = `.mp3, .mkv`[cite: 6].

---

## Langkah-Langkah Konfigurasi
* **Pengerjaan Soal No 4**: IP Address disesuaikan dengan Network yang diberikan ISP.
* **Pengerjaan Soal No 5**: Gateway disesuaikan dengan IP yang diberikan oleh ISP.
* **Langkah 1**: Buka Winbox, arahkan ke menu **IP > DHCP Client**, lalu klik tombol tambah (`+`), pilih `Interface: ether1`, dan klik Apply/OK.
  <img width="672" height="275" alt="SEMINAR proposal (1)" src="https://github.com/user-attachments/assets/2a1427b4-950f-42e4-a278-3de72e8563c1" />
* **Langkah 2**: Pastikan status DHCP Client berubah menjadi **bound** dan mendapatkan IP dari ISP.
  <img width="672" height="166" alt="SEMINAR proposal (2)" src="https://github.com/user-attachments/assets/3bb636a7-f874-469c-a21d-b171006b2c0b" />

* **Pengerjaan Soal No 1 (DNS)**: 
  * Atur IP Dynamic Servers sesuai DNS dari ISP.
  * Beri centang pada opsi **Allow Remote Requests**.
    <img width="602" height="414" alt="SEMINAR proposal (3)" src="https://github.com/user-attachments/assets/64b40ab7-459b-475e-8b07-ebfdd13138e8" />

* **Pengerjaan Soal No 2 (NTP)**: 
  * Masuk ke menu **System > SNTP Client**.
  * Ubah status menjadi **Enabled**.<img width="629" height="297" alt="SEMINAR proposal (12)" src="https://github.com/user-attachments/assets/8fe4a168-6775-43e4-9817-3b1cdb7b0326" />

  * Masukkan Primary dan Secondary NTP Server (misal: `id.pool.ntp.org` dan `asia.pool.ntp.org`).
    <img width="633" height="400" alt="SEMINAR proposal (4)" src="https://github.com/user-attachments/assets/8386678d-88ae-45c0-a759-5e193edff8de" />
  * Selanjutnya pastikan jam nya sudah sesuai dengan format jam di indonesia.
    <img width="704" height="210" alt="SEMINAR proposal (5)" src="https://github.com/user-attachments/assets/b99cf133-8d39-43f0-9c31-15f84213ff60" />

* **Pengerjaan Soal No 3 : WebProxy dengan Cache Administrator = nama_peserta@sekolah.sch.id.**
  <img width="689" height="595" alt="SEMINAR proposal (6)" src="https://github.com/user-attachments/assets/a1620d91-add4-4eba-b333-de9bb0621a07" />

* **Pengerjaan Soal No 6 : Ether 2 ip nya : 192.168.100.1/25.**
* **Pengerjaan Soal No 11 : wlan 1 ip nya : 192.168.200.1/24.**
  * Langkah 1 untuk memasukan IP jaringan lokal. Sesuai ketentuan. Pengerjaan Soal
    <img width="648" height="345" alt="SEMINAR proposal (7)" src="https://github.com/user-attachments/assets/5ffc8b1b-2c20-4860-9259-c85adfd8fd09" />
    <img width="740" height="348" alt="SEMINAR proposal (8)" src="https://github.com/user-attachments/assets/ef20498c-d5a0-44f2-80ec-7a6689c5b5ef" 
  * Langkah 2 , Buat firwall NAT untuk menghubungkan internet ke port ether 1 agar terhubung internet.
    <img width="658" height="256" alt="SEMINAR proposal (9)" src="https://github.com/user-attachments/assets/18742d4f-6dea-4baa-901c-baede4fe905f" />

* **Pengerjaan Soal no 7 : membuat 99 client di jaringan lokal ether 2.**
  <img width="874" height="387" alt="SEMINAR proposal (10)" src="https://github.com/user-attachments/assets/14aa2e12-f102-48b9-9325-cb1337915046" />

* **Pengerjaan soal no 8 : Buat firewall agar IP 192.168.100.2-192.168.100.50 tidak dapat ping ke router.**
  <img width="611" height="288" alt="SEMINAR proposal (11)" src="https://github.com/user-attachments/assets/31b8940e-7ab0-452c-bc9a-de1f02a4029f" />

* **Pengerjaan soal no 9 : Buat firewall agar IP 192.168.100.51-192.168.100.100 tidak dapat ping ke client wireless.**
  <img width="629" height="297" alt="SEMINAR proposal (12)" src="https://github.com/user-attachments/assets/e1eef138-8eeb-4b4a-bd03-d20957b9abba" />



 
    
 

