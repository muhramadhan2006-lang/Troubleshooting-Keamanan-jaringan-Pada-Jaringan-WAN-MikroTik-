# Troubleshooting-Keamanan-jariringan-Pada-Jaringan-WAN
## Topologi
<img width="1230" height="687" alt="SEMINAR proposal (26)" src="https://github.com/user-attachments/assets/1d833cf8-4381-462a-9f65-8f2c125e1468" />

## Alat dan Bahan
1. Internet (Sumber internet dari ISP)
2. 1 pcs Routerboard MikroTik
3. 2 pcs Kabel UTP
4. 1 pcs Smartphone
5. 1 pcs laptop
6. App Winbox

## Setup
1. Hubungkan kabel dari sumber Internet (ISP) ke Ether 1 pada Routerboard MikroTik.
2. Hubungkan kabel UTP pertama dari Ether 2 MikroTik ke port LAN Laptop untuk proses konfigurasi menggunakan aplikasi WinBox.
3. Aktifkan dan atur pemancar Wlan 1 pada MikroTik sebagai titik akses Wi-Fi (SSID).
4. Gunakan Smartphone untuk menghubungkan diri (connect) ke sinyal Wi-Fi tersebut guna menguji kelayakan jaringan hotspot.   

## 📋 Daftar & Ketentuan 

### Konfigurasi Wifi Router
1. **DNS** = Sesuai dengan DNS yang diberikan ISP.
2. **NTP** = Yes.
3. **Web Proxy dengan Cache Administrator** = `nama_peserta@sekolah.sch.id`*(sesuaikan dengan nama dan sekolah kamu)*.

### Jaringan Internet
4. **IP Address** = Sesuai dengan Network yang diberikan ISP.
5. **Gateway** = Sesuai dengan IP yang diberikan oleh ISP.

### Jaringan Lokal
6. **IP Address** = 192.168.100.1/25.
7. **DHCP Pool** = Sebanyak 99 Client.
8. Buat firewall agar IP `192.168.100.2 - 192.168.100.50` tidak dapat ping ke router.
9. Buat firewall agar IP `192.168.100.51 - 192.168.100.100` tidak dapat ping ke client wireless.
10. Buat rule agar setiap akses ke router tercatat di logging dan tersimpan di disk.

### Jaringan Wireless
11. **IP Address** = 192.168.200.1/24.
12. **SSID** = `nama_peserta@ProxyUKK`*(sesuaikan dengan nama kamu)*.
13. **DHCP Pool** = Sebanyak 99 client.
14. Membuat 20 account hotspot secara random di RADIUS.
15. Account hotspot hanya bisa menggunakan internet pada pukul 07.00 - 16.00.

### Blocking (Firewall)
Buat firewall yang memblokir:
16. **Blocking Site** = `https://www.linux.org`.
17. **Blocking File** = `.mp3, .mkv`.

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

    <img width="740" height="348" alt="SEMINAR proposal (8)" src="https://github.com/user-attachments/assets/ef20498c-d5a0-44f2-80ec-7a6689c5b5ef" />
  * Langkah 2 , Buat firwall NAT untuk menghubungkan internet ke port ether 1 agar terhubung internet.
    <img width="658" height="256" alt="SEMINAR proposal (9)" src="https://github.com/user-attachments/assets/18742d4f-6dea-4baa-901c-baede4fe905f" />

* **Pengerjaan Soal no 7 : membuat 99 client di jaringan lokal ether 2.**
  <img width="874" height="387" alt="SEMINAR proposal (10)" src="https://github.com/user-attachments/assets/14aa2e12-f102-48b9-9325-cb1337915046" />

* **Pengerjaan soal no 8 : Buat firewall agar IP 192.168.100.2-192.168.100.50 tidak dapat ping ke router**.
  <img width="611" height="288" alt="SEMINAR proposal (11)" src="https://github.com/user-attachments/assets/31b8940e-7ab0-452c-bc9a-de1f02a4029f" />

* **Pengerjaan soal no 9 : Buat firewall agar IP 192.168.100.51-192.168.100.100 tidak dapat ping ke client wireless.**
  <img width="629" height="297" alt="SEMINAR proposal (12)" src="https://github.com/user-attachments/assets/e1eef138-8eeb-4b4a-bd03-d20957b9abba" />

* **Pengerjaan Soal no 10 : Buat rule agar setiap akses ke router tercatat di logging dan tersimpan di disk.**
<img width="781" height="419" alt="SEMINAR proposal (13)" src="https://github.com/user-attachments/assets/1830ba5e-48d1-40b8-8589-af2c87491f72" />

* **Pengerjaan Soal no 12 : Ubah SSID menjadi NamaPeserta@ProxyUKK Klik Wireless lalu Double Klik pada wlan1.**
 <img width="845" height="213" alt="SEMINAR proposal (14)" src="https://github.com/user-attachments/assets/3bf2698d-e0d3-40e4-ac48-2bc47c4bad50" />

* **Pengerjaan Soal No 13 : DHCP Pool sebanyak 99 client di Wlan.**
  <img width="632" height="807" alt="SEMINAR proposal (15)" src="https://github.com/user-attachments/assets/3ff4ee1e-434f-440b-9de9-666a772485cc" />

* **Pengerjaan soal no 14 : Membuat 20 account hotspot secara random di RADIUS.**
  <img width="822" height="651" alt="SEMINAR proposal (16)" src="https://github.com/user-attachments/assets/b18e67ea-f524-44bc-b065-001540d0d071" />
  * Konfigurasi Pada Sisi Server RADIUS pada webconfig denagan cara masuk ke ip route/userman di chrome
    <img width="787" height="581" alt="SEMINAR proposal (17)" src="https://github.com/user-attachments/assets/10cea1a1-3dff-415c-8c19-75b016a7c23d" />

* **Pengerjaan soal no 15 : Account hotspot hanya bisa menggunakan internet pada pukul 07.00 - 16.00.**
   <img width="803" height="858" alt="SEMINAR proposal (18)" src="https://github.com/user-attachments/assets/cd9156fc-ed49-468f-ac59-a139590812cb" />

* **Pengerjaan soal no 16 : Blocking Site = https://www.linux.org.**
   <img width="838" height="698" alt="SEMINAR proposal (19)" src="https://github.com/user-attachments/assets/4d4f05a5-4990-4999-a244-7c48a911ba17" />

* **Pengerjaan soal no 17 : Blocking File = .mp3, .mkv.**
   <img width="502" height="800" alt="SEMINAR proposal (20)" src="https://github.com/user-attachments/assets/becee5dd-8ff3-44e6-b5cf-d5843dc6416e" />

---

## Pengujian
* **1. Jaringan Lokal Ether 2**
<img width="801" height="255" alt="SEMINAR proposal (21)" src="https://github.com/user-attachments/assets/8e992728-6158-40c4-8340-5366c3d1d609" />

* **2.  Pengujian Bloking IP dari 192.168.100.2 – 192.168.100.50 tidak dapat ping ke Ip Router.**
<img width="793" height="270" alt="SEMINAR proposal (22)" src="https://github.com/user-attachments/assets/22168f68-a331-4460-8dbc-aba898504c1d" />

* **3. Pengujian Bloking Site dan File.**
  * Pengujian di lakukan dengan cara mecari site www.linux.org di google dan file mp3 di google lalu pilih salah satu file mp3.
<img width="838" height="629" alt="SEMINAR proposal (23)" src="https://github.com/user-attachments/assets/cf724859-0802-4522-b001-c39260a4efa1" />

* **4. Pengujian Logging Disk.**
<img width="473" height="255" alt="SEMINAR proposal (24)" src="https://github.com/user-attachments/assets/0caa8cd4-1423-4a87-b93f-42163a816d73" />

* **5. Pengujian akun Radius.**
<img width="427" height="529" alt="SEMINAR proposal (25)" src="https://github.com/user-attachments/assets/0afb9e23-d0a6-4296-9d65-4df2fd8fa8af" />



  




 

    
 

