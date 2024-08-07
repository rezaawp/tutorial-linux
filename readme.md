
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

## Keluar TTY Linux
Distribusi Berbeda, TTY Berbeda: Beberapa distribusi Linux mungkin menggunakan TTY yang berbeda untuk sesi GUI. Misalnya, beberapa distribusi modern mungkin menjalankan sesi GUI di TTY1, TTY2, atau TTY3. Dalam kasus tersebut, Anda mungkin perlu mencoba Ctrl + Alt + F1, Ctrl + Alt + F2, atau Ctrl + Alt + F3
