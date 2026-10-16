# Troubleshooting Keamanan Jaringan pada Jaringan WAN

---

## Topologi

<img width="1230" height="687" alt="SEMINAR proposal (26)" src="https://github.com/user-attachments/assets/1d833cf8-4381-462a-9f65-8f2c125e1468" />

---

## Alat dan Bahan

1. Internet (Sumber internet dari ISP)
2. 1 pcs Routerboard MikroTik
3. 2 pcs Kabel UTP
4. 1 pcs Smartphone
5. 1 pcs Laptop
6. App Winbox

---

## Setup

1. Hubungkan kabel dari sumber Internet (ISP) ke Ether 1 pada Routerboard MikroTik.
2. Hubungkan kabel UTP pertama dari Ether 2 MikroTik ke port LAN Laptop untuk proses konfigurasi menggunakan aplikasi WinBox.
3. Aktifkan dan atur pemancar Wlan 1 pada MikroTik sebagai titik akses Wi-Fi (SSID).
4. Gunakan Smartphone untuk menghubungkan diri (connect) ke sinyal Wi-Fi tersebut guna menguji kelayakan jaringan hotspot.

---

## Daftar & Ketentuan

### Konfigurasi Wifi Router

| No | Parameter | Ketentuan |
|----|-----------|-----------|
| 1 | **DNS** | Sesuai dengan DNS yang diberikan ISP |
| 2 | **NTP** | Yes |
| 3 | **Web Proxy dengan Cache Administrator** | `nama_peserta@sekolah.sch.id` *(sesuaikan dengan nama dan sekolah kamu)* |

### Jaringan Internet

| No | Parameter | Ketentuan |
|----|-----------|-----------|
| 4 | **IP Address** | Sesuai dengan Network yang diberikan ISP |
| 5 | **Gateway** | Sesuai dengan IP yang diberikan oleh ISP |

### Jaringan Lokal

| No | Parameter | Ketentuan |
|----|-----------|-----------|
| 6 | **IP Address** | `192.168.100.1/25` |
| 7 | **DHCP Pool** | Sebanyak 99 Client |
| 8 | **Firewall** | IP `192.168.100.2 - 192.168.100.50` tidak dapat ping ke router |
| 9 | **Firewall** | IP `192.168.100.51 - 192.168.100.100` tidak dapat ping ke client wireless |
| 10 | **Logging** | Setiap akses ke router tercatat di logging dan tersimpan di disk |

### Jaringan Wireless

| No | Parameter | Ketentuan |
|----|-----------|-----------|
| 11 | **IP Address** | `192.168.200.1/24` |
| 12 | **SSID** | `nama_peserta@ProxyUKK` *(sesuaikan dengan nama kamu)* |
| 13 | **DHCP Pool** | Sebanyak 99 client |
| 14 | **Account Hotspot** | Membuat 20 account hotspot secara random di RADIUS |
| 15 | **Jam Akses** | Account hotspot hanya bisa menggunakan internet pada pukul 07.00 - 16.00 |

### Blocking (Firewall)

| No | Parameter | Ketentuan |
|----|-----------|-----------|
| 16 | **Blocking Site** | `https://www.linux.org` |
| 17 | **Blocking File** | `.mp3, .mkv` |

---

## Langkah-Langkah Konfigurasi

### Soal No 4 & 5: IP Address dan Gateway

- **Pengerjaan Soal No 4:** IP Address disesuaikan dengan Network yang diberikan ISP.
- **Pengerjaan Soal No 5:** Gateway disesuaikan dengan IP yang diberikan oleh ISP.

**Langkah 1:** Buka Winbox, arahkan ke menu **IP > DHCP Client**, lalu klik tombol tambah (`+`), pilih `Interface: ether1`, dan klik Apply/OK.

<img width="672" height="275" alt="SEMINAR proposal (1)" src="https://github.com/user-attachments/assets/2a1427b4-950f-42e4-a278-3de72e8563c1" />

**Langkah 2:** Pastikan status DHCP Client berubah menjadi **bound** dan mendapatkan IP dari ISP.

<img width="672" height="166" alt="SEMINAR proposal (2)" src="https://github.com/user-attachments/assets/3bb636a7-f874-469c-a21d-b171006b2c0b" />

---

### Soal No 1: DNS

- Atur IP Dynamic Servers sesuai DNS dari ISP.
- Beri centang pada opsi **Allow Remote Requests**.

<img width="602" height="414" alt="SEMINAR proposal (3)" src="https://github.com/user-attachments/assets/64b40ab7-459b-475e-8b07-ebfdd13138e8" />

---

### Soal No 2: NTP

1. Masuk ke menu **System > SNTP Client**.
2. Ubah status menjadi **Enabled**.

   <img width="629" height="297" alt="SEMINAR proposal (12)" src="https://github.com/user-attachments/assets/8fe4a168-6775-43e4-9817-3b1cdb7b0326" />

3. Masukkan Primary dan Secondary NTP Server (misal: `id.pool.ntp.org` dan `asia.pool.ntp.org`).

   <img width="633" height="400" alt="SEMINAR proposal (4)" src="https://github.com/user-attachments/assets/8386678d-88ae-45c0-a759-5e193edff8de" />

4. Selanjutnya pastikan jam nya sudah sesuai dengan format jam di indonesia.

   <img width="704" height="210" alt="SEMINAR proposal (5)" src="https://github.com/user-attachments/assets/b99cf133-8d39-43f0-9c31-15f84213ff60" />

---

### Soal No 3: Web Proxy

Web Proxy dengan Cache Administrator = `nama_peserta@sekolah.sch.id`.

<img width="689" height="595" alt="SEMINAR proposal (6)" src="https://github.com/user-attachments/assets/a1620d91-add4-4eba-b333-de9bb0621a07" />

---

### Soal No 6 & 11: IP Address Jaringan Lokal dan Wireless

- **Pengerjaan Soal No 6:** Ether 2 IP nya: `192.168.100.1/25`.
- **Pengerjaan Soal No 11:** wlan 1 IP nya: `192.168.200.1/24`.

**Langkah 1:** Memasukkan IP jaringan lokal sesuai ketentuan.

<img width="648" height="345" alt="SEMINAR proposal (7)" src="https://github.com/user-attachments/assets/5ffc8b1b-2c20-4860-9259-c85adfd8fd09" />

<img width="740" height="348" alt="SEMINAR proposal (8)" src="https://github.com/user-attachments/assets/ef20498c-d5a0-44f2-80ec-7a6689c5b5ef" />

**Langkah 2:** Buat firewall NAT untuk menghubungkan internet ke port ether 1 agar terhubung internet.

<img width="658" height="256" alt="SEMINAR proposal (9)" src="https://github.com/user-attachments/assets/18742d4f-6dea-4baa-901c-baede4fe905f" />

---

### Soal No 7: DHCP Pool Jaringan Lokal

Membuat 99 client di jaringan lokal ether 2.

<img width="874" height="387" alt="SEMINAR proposal (10)" src="https://github.com/user-attachments/assets/14aa2e12-f102-48b9-9325-cb1337915046" />

---

### Soal No 8: Firewall Blokir Ping ke Router

Buat firewall agar IP `192.168.100.2 - 192.168.100.50` tidak dapat ping ke router.

<img width="611" height="288" alt="SEMINAR proposal (11)" src="https://github.com/user-attachments/assets/31b8940e-7ab0-452c-bc9a-de1f02a4029f" />

---

### Soal No 9: Firewall Blokir Ping ke Client Wireless

Buat firewall agar IP `192.168.100.51 - 192.168.100.100` tidak dapat ping ke client wireless.

<img width="629" height="297" alt="SEMINAR proposal (12)" src="https://github.com/user-attachments/assets/e1eef138-8eeb-4b4a-bd03-d20957b9abba" />

---

### Soal No 10: Logging Akses Router

Buat rule agar setiap akses ke router tercatat di logging dan tersimpan di disk.

<img width="781" height="419" alt="SEMINAR proposal (13)" src="https://github.com/user-attachments/assets/1830ba5e-48d1-40b8-8589-af2c87491f72" />

---

### Soal No 12: SSID

Ubah SSID menjadi `NamaPeserta@ProxyUKK`. Klik **Wireless** lalu double klik pada **wlan1**.

<img width="845" height="213" alt="SEMINAR proposal (14)" src="https://github.com/user-attachments/assets/3bf2698d-e0d3-40e4-ac48-2bc47c4bad50" />

---

### Soal No 13: DHCP Pool Wireless

DHCP Pool sebanyak 99 client di Wlan.

<img width="632" height="807" alt="SEMINAR proposal (15)" src="https://github.com/user-attachments/assets/3ff4ee1e-434f-440b-9de9-666a772485cc" />

---

### Soal No 14: Account Hotspot di RADIUS

Membuat 20 account hotspot secara random di RADIUS.

<img width="822" height="651" alt="SEMINAR proposal (16)" src="https://github.com/user-attachments/assets/b18e67ea-f524-44bc-b065-001540d0d071" />

Konfigurasi pada sisi server RADIUS melalui webconfig, dengan cara masuk ke `ip route/userman` di Chrome.

<img width="787" height="581" alt="SEMINAR proposal (17)" src="https://github.com/user-attachments/assets/10cea1a1-3dff-415c-8c19-75b016a7c23d" />

---

### Soal No 15: Batas Jam Akses Hotspot

Account hotspot hanya bisa menggunakan internet pada pukul 07.00 - 16.00.

<img width="803" height="858" alt="SEMINAR proposal (18)" src="https://github.com/user-attachments/assets/cd9156fc-ed49-468f-ac59-a139590812cb" />

---

### Soal No 16: Blocking Site

Blocking Site = `https://www.linux.org`.

<img width="838" height="698" alt="SEMINAR proposal (19)" src="https://github.com/user-attachments/assets/4d4f05a5-4990-4999-a244-7c48a911ba17" />

---

### Soal No 17: Blocking File

Blocking File = `.mp3, .mkv`.

<img width="502" height="800" alt="SEMINAR proposal (20)" src="https://github.com/user-attachments/assets/becee5dd-8ff3-44e6-b5cf-d5843dc6416e" />

---

## Pengujian

### 1. Jaringan Lokal Ether 2

<img width="801" height="255" alt="SEMINAR proposal (21)" src="https://github.com/user-attachments/assets/8e992728-6158-40c4-8340-5366c3d1d609" />

### 2. Pengujian Blocking IP

Pengujian blocking IP dari `192.168.100.2` – `192.168.100.50` tidak dapat ping ke IP Router.

<img width="793" height="270" alt="SEMINAR proposal (22)" src="https://github.com/user-attachments/assets/22168f68-a331-4460-8dbc-aba898504c1d" />

### 3. Pengujian Blocking Site dan File

Pengujian dilakukan dengan cara mencari site `www.linux.org` di Google dan file mp3 di Google, lalu pilih salah satu file mp3.

<img width="838" height="629" alt="SEMINAR proposal (23)" src="https://github.com/user-attachments/assets/cf724859-0802-4522-b001-c39260a4efa1" />

### 4. Pengujian Logging Disk

<img width="473" height="255" alt="SEMINAR proposal (24)" src="https://github.com/user-attachments/assets/0caa8cd4-1423-4a87-b93f-42163a816d73" />

### 5. Pengujian Akun RADIUS

<img width="427" height="529" alt="SEMINAR proposal (25)" src="https://github.com/user-attachments/assets/0afb9e23-d0a6-4296-9d65-4df2fd8fa8af" />
