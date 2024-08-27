
## sudo chmod -R 777
```
sudo chmod -R 777
```

Perintah sudo chmod -R 777 digunakan untuk memberikan hak akses penuh (full permissions) pada semua file dan direktori yang ada di dalam direktori yang ditunjuk.

Penjelasan:
- sudo digunakan untuk menjalankan perintah sebagai superuser atau administrator. 
- chmod adalah perintah untuk mengubah hak akses (permissions) pada file atau direktori. 
- -R digunakan untuk mengubah hak akses secara rekursif pada semua file dan direktori yang ada di dalam direktori yang ditunjuk.
- 777 adalah nilai yang menentukan jenis hak akses yang akan diberikan. Angka 7 digunakan untuk memberikan akses penuh atau full permissions pada tiga jenis pengguna: owner (pemilik), group (kelompok), dan others (lainnya). Angka 7 ini sebenarnya merupakan gabungan dari nilai 4 (read), nilai 2 (write), dan nilai 1 (execute). Jadi, 7 = 4 + 2 + 1, yang artinya akses read, write, dan execute semuanya diizinkan.

Namun, perlu diingat bahwa memberikan hak akses penuh (777) pada semua file dan direktori bisa membuka celah keamanan yang dapat dimanfaatkan oleh pihak yang tidak bertanggung jawab, sehingga perlu dilakukan dengan hati-hati. Sebaiknya, gunakan nilai hak akses yang lebih terbatas dan hanya berikan akses tertentu pada pengguna atau grup yang membutuhkan.

## kebalikan dari perintah sudo chmod -R 777
Kebalikan dari perintah chmod -R 777 adalah : 
```
chmod -R o-rwx.
```

Perintah chmod digunakan untuk mengatur hak akses (permission) pada file dan direktori di sistem operasi Unix dan Linux.

Pada perintah chmod -R 777, 777 adalah kombinasi dari tiga mode akses, yaitu read (4), write (2), dan execute (1), yang diberikan kepada pengguna (user), grup (group), dan lainnya (others) secara berurutan, sehingga semua orang mempunyai hak akses penuh (read, write, dan execute) pada file dan direktori tersebut.

Untuk membatasi hak akses kembali, maka perintah chmod -R o-rwx akan menghapus hak akses (read, write, dan execute) dari semua orang (others) pada seluruh file dan direktori yang ada di dalam folder tersebut. Perintah o digunakan untuk menunjukkan hak akses pada others (lainnya), sedangkan r, w, dan x menunjukkan read, write, dan execute.


## install aplikasi yang file ekstensi nya .deb
```
sudo dpkg -i ./namafile.deb
```

Perintah diatas, untuk install aplikasi

## error : `Wrong permissions on configuration file, should not be world writable!` di phpmyadmin

This error message indicates that the configuration file for your local phpMyAdmin installation has incorrect permissions. Specifically, the file has permissions that allow anyone on the system to write to it, which can be a security risk.

To resolve this issue, you should change the permissions on the configuration file to ensure that it is not world-writable. You can do this by running the following command in the terminal:

```
chmod 644 /path/to/phpmyadmin/config.inc.php
```
This will set the permissions on the configuration file to be readable and writable by the owner of the file, and readable by everyone else. This is a common set of permissions for configuration files on a Linux system.

Once you have changed the permissions on the configuration file, you should try accessing phpMyAdmin again to ensure that the error message no longer appears. If you continue to experience issues, you may need to check other file permissions or configuration settings to ensure that your phpMyAdmin installation is properly configured.

## GPG ENCRYPT FILE OR FOLDER
Encrypting a directory using a symmetric key involves using a single key to both encrypt and decrypt the data. This key is known as the "symmetric key" and should be kept secret as anyone who has access to it can decrypt the data.

One way to encrypt a directory using a symmetric key in Linux is by using the "tar" and "gpg" utilities together.

### ENC
First, use the "tar" command to create an archive of the directory you want to encrypt. For example
```
tar -cvf directory.tar /path/to/directory
```
Then, use the "gpg" command to encrypt the tar archive using a symmetric key. For example
```
gpg --symmetric --cipher-algo AES256 directory.tar
```


### DEC
This will prompt you to enter and verify a passphrase, which will be used as the symmetric key.

To decrypt the directory, you would first use the "gpg" command to decrypt the archive using the symmetric key
```
gpg --decrypt directory.tar.gpg > directory.tar
```
Then, use the "tar" command to extract the files from the decrypted archive
```
tar -xvf directory.tar
```

atau bisa baca dokumentasi : https://www.gnupg.org/gph/en/manual/x110.html

### Passphrase
Passphrase adalah kata sandi yang digunakan dalam kriptografi untuk melindungi akses terhadap data yang dienkripsi atau kunci privat yang digunakan dalam proses enkripsi. Ini adalah kata atau frasa rahasia yang harus dimasukkan oleh pengguna untuk mengakses atau mendekripsi data yang terlindungi.

Perbedaan utama antara passphrase dan kata sandi (password) biasa terletak pada panjang dan kompleksitasnya. Passphrase biasanya lebih panjang, terdiri dari beberapa kata yang digabungkan menjadi satu frasa. Ini bertujuan untuk meningkatkan keamanan dengan menciptakan kombinasi karakter yang lebih kompleks.

Passphrase sering digunakan dalam kriptografi untuk mengamankan berbagai hal, seperti enkripsi file, enkripsi email, kunci privat dalam sistem keamanan, atau akses ke jaringan yang terlindungi.

Penting untuk memilih passphrase yang kuat dan sulit ditebak oleh orang lain. Rekomendasi umum adalah menggunakan kombinasi kata-kata yang tidak terkait secara logis, termasuk huruf besar dan kecil, angka, dan karakter khusus. Hal ini akan membuat passphrase lebih sulit ditebak dengan serangan pencobaan kata sandi (brute-force) atau serangan kamus (dictionary attack).

Ingatlah untuk menjaga kerahasiaan passphrase Anda dan tidak membagikannya dengan orang lain. Passphrase yang kuat dan dirahasiakan dengan baik adalah komponen kunci dalam menjaga keamanan data yang terenkripsi.

#### Menghapus Cache GPG supaya diminta untuk memasukan password ketika mau decrypt
```
gpgconf --reload gpg-agent
```

## Kill running port 
```
sudo kill -9 `sudo lsof -t -i:9001`
```

## Show current directory
```
pwd
```

## melihat detail memeory
```
cat /proc/meminfo
```

## melihat detail storage
```
df -h
```

- df -h – shows the result in a human-readable format.
- df -m – displays file system usage information in MB.
- df -k – tells users the file system usage in KB.
- df -T – specifies the file system type in a new column.
- df /home – allows you to view information about a specific file system in a readable format. In this example, it’s the /home file system.

src : https://www.hostinger.com/tutorials/vps/how-to-check-and-manage-disk-space-via-terminal

## reverse proxy dan membuat service :
- https://www.atlantic.net/dedicated-server-hosting/how-to-configure-reverse-proxy-for-node-js-application-using-apache-on-ubuntu/
- ``` client -> server -> nginx -> apache ```
- tujuan reverse proxy diatas : intinya webserver utama tetap apache
fungsi nginx hanya menerima request dari public // alasan reverse ada di kecepatan load sih
kalo make apache doang agak lambet // kenapa di reverse proxy?
apache ga sekuat nginx di spam request

## PPA php
Perintah ```sudo add-apt-repository ppa:ondrej/php``` digunakan untuk menambahkan Personal Package Archive (PPA) yang dikelola oleh Ondřej Surý ke dalam sistem Anda. Ondřej Surý adalah pengelola PPA yang menyediakan berbagai versi PHP dan ekstensi terkait untuk distribusi Linux berbasis Debian dan Ubuntu.
- ```sudo add-apt-repository ppa:ondrej/php```
- ```sudo apt update```

## install extension php sesuai dengan versi php
contohnya gue mau install extension untuk `xml` di versi php 8.3 berarti gini :
``` sudo apt install php8.3-xml ```
- 8.3 diatas disesuikan dengan versi php
- directory php ada di `/usr/` atau di `/etc/`
- ```php -m | grep fileinfo``` mengecek fileinfo extension apakah sudah terinstall atau belum
- curl, xml, gd, mbstring, xml


## Compress video
- https://gist.github.com/lukehedger/277d136f68b028e22bed

## Deploy pakai nginx
- directory default ada di ```/etc/nginx/```
- ```sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/```
- ```sudo systemctl restart nginx```

## Reverse proxy
```
server {
  server_name   api-larch.tataruka.id;

  location / {
    proxy_pass             http://127.0.0.1:8000;
    proxy_read_timeout     60;
    proxy_connect_timeout  60;
    proxy_redirect         off;

    # Allow the use of websockets
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
  }

  location /public/upload {
       add_header Cache-Control "public, max-age=3600, immutable";
       proxy_pass http://127.0.0.1:8000/public/upload;
  }

}
```

## nginx config untuk deploy PHP
```
server {
    server_name domain_kamu;
    root /var/www/projects;

    add_header X-Frame-Options "SAMEORIGIN";
    add_header X-XSS-Protection "1; mode=block";
    add_header X-Content-Type-Options "nosniff";

    index index.php;
    charset utf-8;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location = /favicon.ico { access_log off; log_not_found off; }
    location = /robots.txt  { access_log off; log_not_found off; }

    error_page 404 /index.php;

    location ~ \.php$ {
        fastcgi_pass unix:/var/run/php/php8.2-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        include fastcgi_params;
    }

    location ~ /\.(?!well-known).* {
        deny all;
    }
}
```
- Setiap client yang mengakses file .php ke server harus membutuhkan FPM PHP !
- SSL Gratis bisa menggunakan `certbot`
- Jangan lupa pakai FPM

## ipv6 dan ipv4
Website yang di-deploy dengan hanya menggunakan IPv6 tidak dapat diakses langsung oleh pengguna yang hanya memiliki konektivitas IPv4. Ini disebabkan oleh perbedaan protokol antara IPv4 dan IPv6, di mana keduanya tidak saling kompatibel secara langsung.

### **Penjelasan:**

- **IPv4 dan IPv6**: IPv4 dan IPv6 adalah dua protokol yang berbeda untuk alamat IP. IPv4 menggunakan alamat 32-bit (misalnya, 192.0.2.1), sedangkan IPv6 menggunakan alamat 128-bit (misalnya, 2001:0db8:85a3:0000:0000:8a2e:0370:7334).
- **Kompatibilitas**: Pengguna yang hanya memiliki koneksi IPv4 tidak dapat mengakses situs yang hanya memiliki alamat IPv6, dan sebaliknya, tanpa mekanisme tambahan.

### **Solusi untuk Mengatasi Keterbatasan:**

1. **Dual-Stack**: Cara yang paling umum adalah dengan mengaktifkan **dual-stack** pada server web Anda. Dengan dual-stack, server Anda akan memiliki alamat IPv4 dan IPv6, sehingga bisa diakses oleh pengguna yang menggunakan kedua protokol ini.
   
   - **Cara Kerja**: Ketika pengguna mengakses website Anda, DNS akan memberikan alamat IPv4 (A record) atau IPv6 (AAAA record) tergantung pada protokol yang didukung oleh perangkat pengguna. Ini memastikan bahwa semua pengguna dapat mengakses website Anda, terlepas dari apakah mereka menggunakan IPv4 atau IPv6.

2. **IPv6-to-IPv4 Gateway**: Jika Anda hanya memiliki alamat IPv6 tetapi ingin melayani pengguna IPv4, Anda dapat menggunakan gateway atau proxy yang melakukan translasi antara IPv6 dan IPv4. Layanan seperti ini disediakan oleh beberapa CDN (Content Delivery Network) atau bisa diimplementasikan di infrastruktur Anda sendiri.

3. **Tunneling**: Beberapa teknologi tunneling dapat digunakan untuk mengizinkan lalu lintas IPv4 mengakses sumber daya IPv6 atau sebaliknya, namun ini lebih rumit dan biasanya tidak digunakan sebagai solusi utama.

### **Kesimpulan:**
Untuk memastikan website Anda dapat diakses oleh pengguna yang menggunakan IPv4 dan IPv6, Anda sebaiknya menggunakan konfigurasi dual-stack di server Anda. Ini akan memungkinkan pengguna dari kedua protokol untuk mengakses situs Anda tanpa masalah kompatibilitas.

## Keluar TTY Linux
Distribusi Berbeda, TTY Berbeda: Beberapa distribusi Linux mungkin menggunakan TTY yang berbeda untuk sesi GUI. Misalnya, beberapa distribusi modern mungkin menjalankan sesi GUI di TTY1, TTY2, atau TTY3. Dalam kasus tersebut, Anda mungkin perlu mencoba Ctrl + Alt + F1, Ctrl + Alt + F2, atau Ctrl + Alt + F3

## NGINX PHP
```
server
{
    listen 8080;
    listen [::]:8080;
    server_name 123.456.7.8;
    index index.php index.html index.htm default.php default.htm default.html;
    root /var/www/tes;

    #SSL-START SSL related configuration, do NOT delete or modify the next line of commented-out 404 rules
    #error_page 404/404.html;
    #SSL-END

    #ERROR-PAGE-START  Error page configuration, allowed to be commented, deleted or modified
    error_page 404 /404.html;
    error_page 502 /502.html;
    #ERROR-PAGE-END

    #PHP-INFO-START  PHP reference configuration, allowed to be commented, deleted or modified
    # include enable-php-82.conf;
    location ~ \.php$ {
        fastcgi_pass unix:/var/run/php/php8.2-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        include fastcgi_params;
    }
    #PHP-INFO-END

    #REWRITE-START URL rewrite rule reference, any modification will invalidate the rewrite rules set by the panel
    # include /www/server/panel/vhost/rewrite/tes.com.conf;
    #REWRITE-END

    # Forbidden files or directories
    location ~ ^/(\.user.ini|\.htaccess|\.git|\.env|\.svn|\.project|LICENSE|README.md)
    {
        return 404;
    }

    # Directory verification related settings for one-click application for SSL certificate
    location ~ \.well-known{
        allow all;
    }

    #Prohibit putting sensitive files in certificate verification directory
    if ( $uri ~ "^/\.well-known/.*\.(php|jsp|py|js|css|lua|ts|go|zip|tar\.gz|rar|7z|sql|bak)$" ) {
        return 403;
    }

    location ~ .*\.(gif|jpg|jpeg|png|bmp|swf)$
    {
        expires      30d;
        error_log /dev/null;
        access_log /dev/null;
    }

    location ~ .*\.(js|css)?$
    {
        expires      12h;
        error_log /dev/null;
        access_log /dev/null; 
    }
    access_log  /www/wwwlogs/koperasi.com.log;
    error_log  /www/wwwlogs/koperasi.com.error.log;
}
```

## Reverse Proxy
```
server {
  listen 8080;
  listen [::]:8080;
  server_name 123.4.5.6;

  location / {
    proxy_pass             http://localhost:8080;
      # proxy_set_header Host $host;
      #   proxy_set_header X-Real-IP $remote_addr;
      #   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      #   proxy_set_header X-Forwarded-Proto $scheme;
      
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header REMOTE-HOST $remote_addr;
    add_header X-Cache $upstream_cache_status;
    
    proxy_connect_timeout 30s;
    proxy_read_timeout     60;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    # proxy_cache_bypass $http_upgrade;
  
    # location /api/tps_images/ {
    #     alias /www/wwwroot/bot/wa_bot_polling_tps;
    # }
    # proxy_connect_timeout  60;
    # proxy_redirect         off;

    # Allow the use of websockets
  }
  
}
```

## Rewrite template
- https://github.com/aaPanel/aaPanel/tree/master/rewrite/nginx

## Virtualisasi

### Proxmox

Ya, Proxmox adalah platform virtualisasi open-source yang memungkinkan Anda untuk mengelola mesin virtual dan container. Ini adalah distribusi Linux berbasis Debian yang menyediakan antarmuka web untuk mengelola virtualisasi KVM (Kernel-based Virtual Machine) untuk mesin virtual, serta LXC (Linux Containers) untuk container.

Berikut adalah beberapa fitur utama Proxmox:

1. **Virtualisasi dan Container**: Proxmox mendukung KVM untuk virtualisasi penuh dan LXC untuk container ringan, memungkinkan Anda untuk menjalankan berbagai jenis sistem operasi dan aplikasi dalam satu host fisik.

2. **Manajemen Berbasis Web**: Proxmox menyediakan antarmuka pengguna berbasis web yang memungkinkan Anda mengelola seluruh infrastruktur virtual Anda dari satu tempat, termasuk penciptaan, penghapusan, dan pengelolaan mesin virtual serta container.

3. **Cluster dan Replikasi**: Proxmox mendukung clustering, yang memungkinkan beberapa server fisik dikelola sebagai satu kesatuan. Ini juga menyediakan fitur replikasi data untuk redundansi dan pemulihan bencana.

4. **Penyimpanan Terpadu**: Proxmox mendukung berbagai opsi penyimpanan seperti ZFS, Ceph, NFS, iSCSI, dan lainnya, memungkinkan integrasi mudah dengan sistem penyimpanan yang ada.

5. **Backup dan Pemulihan**: Proxmox menawarkan alat untuk backup dan pemulihan, termasuk snapshot dan backup berbasis jadwal.

6. **Jaringan Virtual**: Anda dapat mengkonfigurasi jaringan virtual, VLAN, dan mengelola routing jaringan untuk mesin virtual dan container.

Proxmox banyak digunakan dalam lingkungan data center, server rumah, dan aplikasi pengujian karena fleksibilitas, skalabilitas, dan biaya operasional yang rendah.

### Qemu
QEMU (Quick Emulator) adalah sebuah perangkat lunak open-source yang menyediakan emulasi dan virtualisasi hardware. Di Linux, QEMU digunakan untuk menjalankan sistem operasi dan aplikasi dalam lingkungan virtual yang diisolasi. Berikut beberapa poin penting mengenai QEMU:

### 1. **Fungsi Utama QEMU**:
   - **Emulasi**: QEMU dapat mengemulasi berbagai arsitektur CPU (seperti x86, ARM, SPARC, dan lainnya), memungkinkan Anda menjalankan sistem operasi yang berbeda dari arsitektur fisik yang digunakan oleh host. Ini berarti Anda bisa menjalankan sistem operasi ARM pada host x86, misalnya.
   - **Virtualisasi**: Dengan menggunakan teknologi virtualisasi seperti KVM (Kernel-based Virtual Machine), QEMU dapat menjalankan mesin virtual dengan performa hampir mendekati perangkat keras asli, karena instruksi dijalankan langsung pada CPU host jika memungkinkan.

### 2. **Mode Kerja QEMU**:
   - **Full Emulation Mode**: Semua perangkat keras (CPU, memori, perangkat I/O) diemulasi oleh QEMU. Ini berguna untuk tujuan pengembangan dan pengujian, terutama saat mengembangkan software untuk arsitektur yang berbeda.
   - **User-mode Emulation**: QEMU dapat menjalankan program Linux yang dikompilasi untuk arsitektur lain, dengan mengemulasi panggilan sistem dan instruksi CPU tertentu.
   - **Virtualization (KVM)**: QEMU bekerja bersama dengan KVM untuk memberikan virtualisasi yang hampir native. Ini hanya bisa digunakan pada prosesor yang mendukung virtualisasi hardware (seperti Intel VT atau AMD-V).

### 3. **Fitur QEMU**:
   - **Snapshot**: Kemampuan untuk mengambil snapshot dari keadaan sistem virtual, sehingga Anda bisa kembali ke titik waktu sebelumnya jika diperlukan.
   - **Disk Image Formats**: Mendukung berbagai format gambar disk, seperti QCOW2, RAW, VMDK, dan lainnya.
   - **Network Emulation**: QEMU menyediakan berbagai opsi jaringan virtual, seperti bridging, NAT, dan lainnya, untuk menghubungkan mesin virtual dengan jaringan eksternal.
   - **Live Migration**: Memungkinkan migrasi mesin virtual dari satu host ke host lain tanpa downtime, yang sangat berguna dalam lingkungan produksi.

### 4. **Penggunaan Umum QEMU**:
   - **Pengembangan dan Pengujian**: Pengembang dapat menggunakan QEMU untuk menguji aplikasi pada berbagai sistem operasi dan arsitektur tanpa memerlukan perangkat keras fisik untuk setiap platform.
   - **Server Virtualisasi**: Digunakan dalam lingkungan server untuk menjalankan beberapa sistem operasi secara simultan pada satu perangkat keras fisik, mengoptimalkan penggunaan sumber daya.
   - **Emulasi Hardware Lama**: Dapat digunakan untuk menjalankan software lama yang memerlukan arsitektur yang tidak lagi didukung oleh perangkat keras modern.

QEMU sering digunakan bersama dengan proyek open-source lainnya seperti Libvirt (untuk manajemen virtualisasi), KVM (untuk akselerasi virtualisasi), dan Proxmox (seperti yang disebutkan sebelumnya) untuk membangun solusi virtualisasi yang kuat dan fleksibel.
