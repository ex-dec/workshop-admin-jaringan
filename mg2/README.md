# Minggu 2
## A. Kernel

Kernel adalah inti dari jalannya sebuah sistem komputer dan berfungsi untuk mengatur hubungan antara hardware dengan operasi sistem. Kernel menggunakan sistem keturunan dalam menghasilkan semua versi yang ada sekarang. Beberapa kernel yang cukup terkenal adalah unix, linux, solaris, bsd, dan ms-dos. Linux, Solaris, dan bsd merupakan turunan dari kernel unix. Maka dari itu kernel tersebut sering disebut unix-like (seperti unix). Untuk linux sendiri saat ini sudah memiliki versi 6 dalam perkembangannya, dan pada gambar berikut merupakan versi kernel dari debian 11 saat ini.

![versi kernel linux debian 11](asset/kernel-version.png)

## B. Directory Structure

Struktur direktori dalam sebuah sistem operasi dipengaruhi oleh jenis kernel tersebut. Untuk semua keturunan dari unix memiliki struktur yang hampir sama. Untuk debian 11 memiliki kernel linux dan berikut adalah struktur direktorinya.

![struktur direktori debian 11](asset/directory-structure.png)

1. /bin

    Direktori ini digunakan untuk menyimpan seluruh executable file pada sistem operasi. Executable ini mengacu pada package yang dapat dijalankan pada sistem operasi.

2. /boot

    Pada direktori ini, kita dapat mengkonfigurasi partisi boot yang ada pada sistem operasi kita. Keseluruhan konfigurasi boot sebelum kita masuk ke operasi sistem kita dapat dikonfigurasi pada partisi ini.

3. /dev

    Direktori ini berisi daftar seluruh hardware yang terhubung dengan komputer kita. Hardware tersebut dapat ter-daftar karena kernel yang mengenali hardware tersebut.

4. /etc

    Direktori /etc memiliki fungsi untuk menyimpan konfigurasi seluruh package yang terinstall pada sistem operasi kita. Pada sistem operasi berbasis kernel linux, file package disimpan terpisah dengan file konfigurasi. Jadi seluruh file dapat tersimpan dengan ter-struktur.

5. /home

    Diretori Home merupakan direktori utama dari seluruh user yang ada pada linux. Direktori ini digunakan untuk menyimpan keseluruhan file dan konfigurasi yang dimiliki oleh user.

6. /opt

    Opt atau optional merupakan direktori yang digunakan untuk menyimpan package tambahan yang bukan merupakan bawaan dari sistem operasi. Seperti package tambahan yang diinstall dengan melakukan compile manual terhadap source code.

7. /proc

    Direktori proc berfungsi untuk menyimpan informasi hardware yang merupakan bagian dari sistem inti dari hardware, seperti informasi tentang memori, cpu, dan swap.

8. /root

    Direktori ini sering menjadi kebingungan oleh seseorang yang baru saja menggunakan linux. Karena pada instalasi awal ditunjukkan struktur direktori ada / (root) dan /root. / tetap disebut dengan direktori root, namun untuk /root merupakan direktori user root. Jadi seluruh file konfigurasi unuk user root terletak pada direktori ini. Tidak hanya direktori, melainkan file pribadi dari user root juga disimpan pada direktori ini karena direktori utama user root tidak terletak pada /home

9. /run

    Direktori ini merupakan pecahan dari direktori /tmp. Direktori ini berisi informasi tentang status dari sebuah aplikasi yang berjalan. Direktori ini disimpan terpisah dengan /tmp karena /tmp bersifat sementara dan akan terhapus setelah sistem operasi direstart. Sedangkan informasi tentang status aplikasi harus tetap bisa diakses meskipun sistem operasi telah mengalami reboot.

10. /tmp

    Direktori tmp sesuai dengan kepanjangannya adalah temporary, digunakan untuk menyimpan file yang bersifat sementara dan dibutuhkan hanya ketika sistem tersebut berjalan. Ketika sistem operasi tersebut di-restart, maka semua file pada direktori tersebut akan hilang.

11. /usr

    usr merupakan direktori untuk menyimpan semua package pada sistem operasi. Disini berbeda dengan /etc karena etc bertugas untuk menyimpan konfigurasi saja.

## C. Perbedaan su dan sudo

su dan sudo merupakan dua hal yang berbeda. su adalah kepanjangan dari "substitute user" yang memiliki definisi perpindahan user. Dari definisi tersebut dapat disimpulkan bahwa su digunakan untuk berpindah ke user yang kita tuju. Parameter yang digunakan sebenarnya cukup banyak, namun yang sering digunakan adalah "-". Parameter tersebut merupakan parameter untuk menunjuk user. misal, ketika kita menggunakan perintah "su - user1" , maka kita akan langsung diarahkan ke user1 langsung dengan home directory user tersebut. Jika kita menggunakan parameter tersebut tanpa user yang dituju, maka secara otomatis akan menunjuk user root sebagai tujuannya. 

Sedangkan untuk sudo, merupakan perintah yang digunakan untuk meng eksekusi perintah yang berada dalam satu baris sebagai super user. Jadi meskipun kita tidak masuk sebagai super user, kita tetap bisa mendapatkan privilege sebagai super user.

## D. Jenis Repository

Sebelum kita membahas tentang jenis repository, kita harus mengenal terlebih dahulu apa itu repository.
Repository merupakan sebuah server yang digunakan untuk menyimpan kumpulan package. Kenapa tidak disebut dengan penyimpanan drive online saja? karena repository dikhususkan untuk menyimpan berkas dalam bentuk kode yang amat banyak. Dibutuhkan protokol tertentu untuk melakukan transfer data agar file yang dikirim tidak hilang sebagian di tengah jalan.

Sekarang kita akan fokus terhadap repository package dari sistem operasi debian. Debian menggunakan package manager "apt". Package manager tersebut digunakan untuk men-download, meng-install, serta meng-hapus package dari sistem operasi debian.

Jenis-jenis dari repository debian dapat kita lihat pada detail repository di /etc/apt/sources.list

![Isi file /etc/apt/sources.list](asset/source-lis.png)

Pada salah satu baris yang tidak ter-disable, kita bisa melihat isiannya adalah 

    deb http://kebo.pens.ac.id/debian bullseye main contrib non-free

rincian pada baris tersebut adalah

deb = jenis package yang akan diambil adalah deb

http://kebo.pens.ac.id/debian = tujuan server yang akan dijadikan tempat download package nya

bullseye = Tipe repository yang akan diambil. Pada opsi ini ada beberapa tipe yaitu bullseye yang berisi package utama, bullseye-updates yang berisi package update bullseye-security untuk package security dari sistem operasi, serta bullseye-backport yang berisi package beta. 

main contrib non-free = Keterangan tersebut adalah identifikasi package yang termasuk dalam kategori package utama, package hasil kontribusi komunitas, atau package yang sifatnya non-oss (closed source).

## E. 

identifikasi jenis repository
identifikasi perintah apt