## ELGG
<img src="https://github.com/dwikaayunovianti/ELGG/blob/master/image/1200px-Elgg.jpg"></img>

[Sekilas Tentang](#sekilas-tentang) | [Instalasi](#instalasi) | [Konfigurasi](#konfigurasi) | [Otomatisasi](#otomatisasi) | [Cara Pemakaian](#cara-pemakaian) | [Pembahasan](#pembahasan) | [Referensi](#referensi)
:---:|:---:|:---:|:---:|:---:|:---:|:---:

<h1>Sekilas Tentang</h1>
<p> Elgg adalah sebuah social networking framework dan merupakan varian jenis CMS. CMS (Content Management System) sendiri merupakan aplikasi dari kumpulan bahasa pemrograman yang terhimpun menjadi satu dengan tujuan untuk mempermudah dalam mengelola dan memanajemen suatu website. CMS memiliki jenis yang beragam, misalnya saja, wordpress untuk blog, joomla untuk blog ataupun forum, lokomedia untuk toko online, dan Elgg sebagai situs jejaring sosial. <p>

<p> Elgg ini tergolong freeware dan untuk lisensinya sendiri termasuk open source dan kita bebas untuk mengembangkannya. Elgg memungkin kita untuk menjalankan jejaring sosialnya sendiri yang digunakan didalam jaringan internal/local dengan bantuan web server tentunya bisa berbasis linux server maupun windows. Tidak hanya itu Elgg juga bisa kita gunakan di shared hosting maupun di vps. Elgg beroperasi pada lingkungan LAMP (Linux, Apache, MySql dan Php) dan mudah untuk diinstal dan dikonfigurasi. </p>

<p> Meskipun tidak sepowerfull facebook namun elgg memiliki banyak fitur yang mumpuni untuk kita coba diantaranya : melakukan update status, tambah pertemanan, membuat group, upload file/foto, ganti foto profil, social  networking, weblog, bookmark, instant messaging, file repository, access control, tagging, customization, dan community building. </p>

<h1>Instalasi</h1>
<h3>Kebutuhan Sistem : </h3>
<p> -Unix, Linux atau Windows<br>
-MariaDb<br>
-Apache Web server 2<br>
-PHP 7 </p>

<h3>Proses Instalasi :</h3>

1. Jalankan agar Virtual Machine bisa diakses dari luar melalui alamat IP host (localhost) <br>
  ```
  ssh dwikaayu@localhost -p 2222 
  ```

2. Kemudian update sistem dengan menginstal Apache2 HTTP di server Ubuntu
```
  Install Apache
  sudo apt update
  sudo apt install apache2
```

<i> Berikut ini perintah untuk memberhentikan, memulai dan mengaktifkan Apache2 di server boots </i>
```
  sudo systemctl stop apache2.service
  sudo systemctl start apache2.service
  sudo systemctl enable apache2.service
```

Selanjutnya lakukan testing Apache2 dengan cara buka browser lalu masukan alamat IP address untuk mengetahui apakah halaman Apache2 bisa berjalan dengan baik atau tidak, jika berhasil akan muncul tampilan seperti ini :  

<img src ="https://github.com/dwikaayunovianti/ELGG/blob/master/image/apache2_ubuntu_install.png"> </img>

3. Langkah selanjutnya install MariaDB Database server
```
  $sudo apt-get install mariadb-server mariadb-client

```
<i> Perintah untuk memberhentikan, memulai dan mengaktifkan MariaDB di server boot. Jalankan ini di Ubuntu 17.10 dan 18.04 LTS
</i>
```
  $sudo systemctl stop mariadb.service
  $sudo systemctl start mariadb.service
  $sudo systemctl enable mariadb.service
```

4. Selanjutnya jalankan perintah dibawah ini untuk mengamankan server MariaDB dengan membuat root password dan disallowing remote root access.
```
  $sudo mysql_secure_installation
```

Setelah itu akan muncul pertanyaan, maka jawab seperti ini 
```
<ul> -Enter current password for root (enter for none): Tekan Enter </ul>
<ul> -Set root password? [Y/n]: Y </ul> 
<ul> -New password: Masukkan Password</ul>
<ul> -Re-enter new password: Ulangi Password</ul>
<ul> -Remove anonymous users? [Y/n]: Y</ul>
<ul> -Disallow root login remotely? [Y/n]: Y</ul>
<ul> -Remove test database and access to it? [Y/n]:  Y</ul> 
<ul> -Reload privilege tables now? [Y/n]:  Y</ul> 
```
Kemudian restart MariaDB server

Untuk menguji apakah MariaDB diinstal, ketik perintah di bawah ini untuk masuk ke server MariaDB
```
$ sudo mysql -u root -p	
```

Jika berhasil maka akan muncul <i> MariaDB welcome message </i> 

5. Jalankan perintah di bawah ini menginstal PHP 7.2 dan modul terkait.
```
  $ sudo apt-get install software-properties-common  
  $ sudo add-apt-repository ppa:ondrej/php 
  $ sudo apt update sudo apt install php7.2 libapache2-mod-php7.2 php7.2-common php7.2-sqlite3 php7.2-curl php7.2-intl php7.2-mbstring       php7.2-xmlrpc php7.2-mysql php7.2-gd php7.2-xml php7.2-cli php7.2-zip
  $ sudo nano /etc/php/7.2/apache2/php.ini
```
Kemudian ubah pengaturan seperti di bawah ini lalu simpan
```
<ul> file_uploads = On</ul>
<ul> allow_url_fopen = On</ul>
<ul> short_open_tag = On</ul>
<ul> memory_limit = 256M</ul>
<ul> upload_max_filesize = 100M </ul>
<ul>max_execution_time = 360</ul><br>
```

6. Setelah menlakukan instal PHP dan modul terkait, restart Apache2 untuk memuat ulang konfigurasi PHP 
Untuk me-restart Apache2, jalankan perintah di bawah ini : 
```
  $ sudo systemctl restart apache2.service
```

7. Selanjutnya kita buat Database Magento.<br>
<ul> Untuk masuk ke server database MariaDB, jalankan perintah di bawah ini. </ul>
```
  $sudo mysql -u root -p
```
<ul> Buat database dengan nama *elgg* </ul>
```
    CREATE DATABASE elgg;
```
<ul> Buat pengguna yang disebut elgguser dengan kata sandi baru </ul>
```
  CREATE USER 'elgguser'@'localhost' IDENTIFIED BY 'new_password_here';
```
<ul>Kemudian beri pengguna akses penuh ke database.</ul>
```
  GRANT ALL ON elgg.* TO 'elgguser'@'localhost' IDENTIFIED BY 'user_password_here' WITH GRANT OPTION;
```
<ul>Setelah semua nya diubah, simpan lalu keluar</ul>
 ```
  FLUSH PRIVILEGES;
  
  EXIT;
 ```
 
 8. Lakukan download dan install Elgg
 
Jalankan perintah di bawah ini untuk mengunduh konten terbaru Elgg CMS, kemudian unzip file unduhan dan pindahkan konten ke direktori   root default Apache2
```
  cd /tmp && wget https://elgg.org/download/elgg-2.3.7.zip  
  unzip elgg-2.3.7.zip
  sudo mv elgg-2.3.7 /var/www/html/elgg
```
Selanjutnya, buat direktori data Elgg untuk menyimpan konten data 
```
  $ sudo mkdir -p /var/www/html/elgg/data
```
Selanjutnya ubah permission folder root
```
  $sudo chown -R www-data:www-data /var/www/html/elgg/
  $sudo chmod -R 755 /var/www/html/elgg/
```

9. Selanjutnya konfigurasi Situs Apache2 Elgg. 
<p>Konfigurasikan file Apache2 untuk Elgg CMS. File ini akan mengontrol bagaimana pengguna mengakses konten Elgg CMS. Jalankan perintah di bawah ini untuk membuat file konfigurasi baru bernama elgg.conf</p>
```
  $sudo nano /etc/apache2/sites-available/elgg.conf
```

Kemudian ***copy*** dan ***paste*** konten di bawah ini ke dalam file dan simpan. Ganti baris dengan nama domain dan lokasi root direktori sendiri. 
```
<VirtualHost *:80>
     ServerAdmin admin@example.com
     DocumentRoot /var/www/html/elgg
     ServerName localhost:8888

     <Directory /var/www/html/elgg/>
          Options FollowSymlinks
          AllowOverride All
          Require all granted
     </Directory>

     ErrorLog ${APACHE_LOG_DIR}/error.log
     CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
```

10. Aktifkan Situs Elgg CMS dan Modul Tulis Ulang

Setelah mengkonfigurasi VirtualHost di atas, aktifkan dengan menjalankan perintah di bawah ini, kemudian mulai ulang server Apache2\
```
  $sudo a2ensite elgg.conf
  $sudo a2enmod rewrite
  $sudo systemctl restart apache2.service
```

11. Selanjutnya, buka brwoser dan buka URL, setelah itu lanjutkan dengan instalasi<br>
Ketikan *localhost:8888* di browser 

<i> Halaman Elgg installation wizard, klik next</i><br>

<img src="https://github.com/dwikaayunovianti/ELGG/blob/master/image/elgg_ubuntu_install.png"></img> 

<i> Selanjutnya isi data  database pada kolom  sesuai dengan yang sudah ditentukan sebelumnya, klik next</i>

    <ul> Pada bagian database username dan password sesuaikan dengan nama yang kalian buat sebelumnya </ul>

        <img src="https://github.com/dwikaayunovianti/ELGG/blob/master/image/elgg_ubuntu_install_1.png"></img>

<i> Selanjutnya isi  kolom untuk konfigurasi situs, klik next </i> <br>

<img src="https://github.com/dwikaayunovianti/ELGG/blob/master/image/elgg_ubuntu_install_2.png"></img>

<i> Lalu isi kolom untuk membuat akun admin, klik next</i>

<img src="https://github.com/dwikaayunovianti/ELGG/blob/master/image/elgg_ubuntu_install_3.png"></img>

<i> Setelah berhasil, maka akan masuk ke halaman utama sebagai admin </i>

<img src="https://github.com/dwikaayunovianti/ELGG/blob/master/image/1.png"></img
 
#Konfigurasi
<ul> <b>Upgrade</b> : dapat meningkatkan instalasi dengan up to date </ul>
<img src="https://github.com/dwikaayunovianti/ELGG/blob/master/image/3.png"></img>
<ul> <b>Appearance </b> <br>
  <ul> <i>Menu items </i>: memilih menu yang ingin ditampilkan sebagai link dan juga dapat mengatur secara custom, dengan mengisi URL dan nama yang tampil.</ul>
<img src="https://github.com/dwikaayunovianti/ELGG/blob/master/image/4.png"></img>

<ul> <i>Edit Profile Fields</i> : dapat mengedit profil, dengan memasukkan label dan memilih tipe profile. </ul><>
<img src="https://github.com/dwikaayunovianti/ELGG/blob/master/image/5.png"></img>

<ul> <i>Default Widgets</i></ul>
<img src="https://github.com/dwikaayunovianti/ELGG/blob/master/image/6.png"></img> <br>

<ul> <b>Plugins</b></ul>
<img src="https://github.com/dwikaayunovianti/ELGG/blob/master/image/7.png"></img>
