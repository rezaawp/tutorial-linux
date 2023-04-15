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


```
sudo dpkg -i ./namafile.deb
```

Perintah diatas, untuk install aplikasi
