# Minggu 4

Pada minggu ke-empat ini, kita akan administrasi jaringan pada topologi kemarin. Pada minggu ini kita akan melakukan instalasi server yang ada pada masing-masing kelompok. Berikut adalah [backlog](#backlog-minggu-4) dari minggu ke-empat.

### Backlog Minggu 4

- [Konfigurasi Internet Client](#konfigurasi-internet-client)
- [Instalasi Debian Server](#instalasi-debian-server)
- [Instalasi NTP Server Debian](#instalasi-ntp-server-debian)
- [Konfigurasi NTP Client Mikrotik ke Server Debian](#konfigurasi-ntp-client-mikrotik-ke-server-debian)
  - [Membuka file konfigurasi ntp server](#membuka-file-konfigurasi-ntp-server)
  - [Menjalankan ntp](#menjalankan-ntp)
  - [ntp client](#ntp-client)
- [Hasil](#hasil)

<br>

# Konfigurasi Internet Client

Pertama kita harus melakukan konfigurasi internet untuk client yang memiliki jaringan dibawah router kita. Sebelumnya kita sudah melakukan konfigurasi dhcp untuk alokasi _IP Address_ secara otomatis, lalu _default route_ untuk melakukan routing ke jaringan internet. Sekarang kita hanya tinggal menambahkan konfigurasi NAT untuk meng-translasikan _IP Address_ lokal kita agar bisa dikenali jaringan _public_. Konfigurasinya adalah sebagai berikut

```console
/ip firewall nat
add action=masquerade chain=srcnat out-interface=ether1
```

Konfigurasi diatas menunjukkan metode translasi yaitu masquerade srcnat dengan jalur keluar yaitu _ether1_

# Instalasi Debian Server

Selanjutnya yang harus yang dilakukan adalah instalasi OS yang digunakan pada server, kali ini saya menggunakan Debian server. Untuk tutorial lengkap instalasi, sudah banyak tersebar di google.

[Cara instalasi Debian Server di virtualbox](https://virgiawan.id/tutorial-install-debian-server-di-virtualbox/)

[Cara instal Debian Server](https://idelinux.com/tutorial-install-debian-11-minimal-server-di-virtualbox)

setelah instalasi, pastikan bahwa OS bisa dijalankan.

![debian.jpeg](asset/debian.jpeg)

# Instalasi NTP Server Debian

Selanjutnya adalah instalasi ntp servernya, masukkan perintah dibawah untuk melakukan instalasi

```console
sudo apt install ntp
```

Kemudian tunggu proses instalasi sampai berhasil, dan ntp berhasil ter-_install_ di perangkat.

![ntp_instalation.png](asset/1.%20instalasi%20ntp%20server.png)

# Konfigurasi NTP Client Mikrotik ke Server Debian

## Membuka file konfigurasi ntp server

Untuk membuka file konfigurasi ntp, gunakan perintah

```console
sudo vim /etc/ntp.conf
```

kemudian masukkan konfigurasi berikut kedalam file nya

```console
pool 0.debian.pool.ntp.org iburst
pool 1.debian.pool.ntp.org iburst
pool 2.debian.pool.ntp.org iburst
pool 3.debian.pool.ntp.org iburst
```

kemudian simpan konfigurasi.

## Menjalankan ntp

Selanjutnya pastikan bahwa ntp sudah dijalankan menggunakan perintah `sudo service ntp status`. Jika ntp sudah berjalan maka akan tampil seerti berikut

![status_ntp_server.png](asset/4.%20status%20ntp%20server.png)

kita bisa mengecek ntp server berjalan atau tidak pada terminal kita menggunakan perintah `netstat -nlptu`.

![status_ntp_server.png](asset/5.%20status%20ntp%20server.png)

Pada gambar tersebut terlihat bahwa daemon dari ntp berjalan pada port 123 dengan protokol UDP.

Kita bisa mengecek tanggal pada terminal kita menggunakan perintah `date`.

![status_date.png](asset/6.%20status%20date.png)

## ntp client

selanjutnya kita akan mengkonfigurasi ntp client pada mikrotik kita bisa mengaturnya seperti berikut pada bagian `System -> SNTP Client`, kemudian simpan.

![ntp_client.png](asset/7.%20ntp%20client.png)

Konfigurasi yang perlu disesuaikan adalah primary NTP Server dan status enable dari ntp client itu sendiri.

# Hasil

Setelah semua konfigurasi dilakukan, kita bisa mengecek waktu pada mikrotik, jika berhasil maka waktu di mikrotik dan server akan sama.

![hasil.png](asset/8.%20hasil%20konfigurasi%20ntp%20client.png)

[def]: #backlog-minggu-4
