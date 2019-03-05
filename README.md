## ELGG
<img src="https://github.com/dwikaayunovianti/ELGG/blob/master/image/1200px-Elgg.jpg"></img>

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
  sudo apt-get install mariadb-server mariadb-client

```

<i> Perintah untuk memberhentikan, memulai dan mengaktifkan MariaDB di server boot </i>
```
  sudo systemctl stop mariadb.service
	sudo systemctl start mariadb.service
	sudo systemctl enable mariadb.service
```

4. Selanjutnya jalankan perintah dibawah ini untuk mengamankan server MariaDB dengan membuat root password dan disallowing remote root access.
```
  sudo mysql_secure_installation
```
