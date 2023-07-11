# Application Containerization and Microservice Orchestration

### Play with Docker classroom

### Steps:
* Stage Setup
* Step 0: Basic Link Extractor Script
* Step 1: Containerized Link Extractor Script
* Step 2: Link Extractor Module with Full URI and Anchor Text
* Step 3: Link Extractor API Service
* Step 4: Link Extractor API and Web Front End Services
* Step 5: Redis Service for Caching
* Step 6: Swap Python API Service with Ruby
* Conclusions

### Stage Setup

Mari kita mulai dengan terlebih dahulu mengkloning repositori kode demo, mengubah direktori kerja, dan memeriksa cabangnya ```demo```

<div><img src="gambar/Stage-setup.jpg"></div>

### Step 0: Basic Link Extractor Script

Periksa ```step0``` cabang dan daftar file di dalamnya

<div><img src="gambar/step0-1.png"></div>


File tersebut ```linkextractor.py``` adalah yang menarik di sini, jadi mari kita lihat isinya: 

<div><img src="gambar/step0-2.png"></div>


Ini adalah skrip Python sederhana yang mengimpor tiga paket: ```sys``` dari pustaka standar dan dua paket pihak ketiga populer ```requests``` dan ```bs4```. Argumen baris perintah yang disediakan pengguna (yang diharapkan berupa URL ke halaman HTML) digunakan untuk mengambil halaman menggunakan paket ```requests```, kemudian diuraikan menggunakan ```BeautifulSoup```. Objek yang diuraikan kemudian diulang untuk menemukan semua elemen jangkar (yaitu, ```<a>``` tag) dan mencetak nilai atributnya ```href``` yang berisi hyperlink.

Namun, skrip yang tampaknya sederhana ini mungkin bukan yang termudah untuk dijalankan pada mesin yang tidak memenuhi persyaratannya. File ```README.md``` menyarankan cara menjalankannya, jadi mari kita coba:

<div><img src="gambar/step0-3.png"></div>


Saat kami mencoba menjalankannya sebagai skrip, kami mendapatkan kesalahan ```Permission denied```. Mari kita periksa izin saat ini pada file ini:

<div><img src="gambar/step0-4.png"></div>


Izin saat ini ```.-rw-r--r--```. menunjukkan bahwa skrip tidak disetel untuk dapat dieksekusi. Kita dapat mengubahnya dengan menjalankan ```chmod``` ```a+x linkextractor.py``` atau menjalankannya sebagai program Python alih-alih skrip yang mengeksekusi sendiri seperti yang diilustrasikan di bawah ini:

<div><img src="gambar/step0-5.png"></div>


### Step 1: Containerized Link Extractor Script

Periksa step1cabang dan daftar file di dalamnya.

<div><img src="gambar/step1-1.png"></div>

Kami telah menambahkan satu file baru (yaitu, Dockerfile) pada langkah ini. Mari kita lihat isinya:

<div><img src="gambar/step1-2.png"></div>

Dengan menggunakan ini, Dockerfilekita dapat menyiapkan gambar Docker untuk skrip ini. Kita mulai dari image Docker resmi pythonyang berisi lingkungan run-time Python serta alat yang diperlukan untuk menginstal paket dan dependensi Python. Kami kemudian menambahkan beberapa metadata sebagai label (langkah ini tidak penting, tetapi tetap merupakan praktik yang baik). Dua instruksi berikutnya jalankan pip installperintah untuk menginstal dua paket pihak ketiga yang diperlukan agar skrip berfungsi dengan baik. Kami kemudian membuat direktori kerja /app, menyalin linkextractor.pyfile di dalamnya, dan mengubah izinnya untuk menjadikannya skrip yang dapat dieksekusi. Terakhir, kami menetapkan skrip sebagai titik masuk untuk gambar.

Sejauh ini, kami baru saja menjelaskan bagaimana kami ingin image Docker kami, tetapi tidak benar-benar membangunnya. Jadi mari kita lakukan itu:

<div><img src="gambar/step1-3.png"></div>

Kami telah membuat gambar Docker yang diberi nama linkextractor:step1berdasarkan Dockerfileilustrasi di atas. Jika build berhasil, kita seharusnya dapat melihatnya di daftar Image:

<div><img src="gambar/step1-4.jpg"></div>

Image ini harus memiliki semua bahan yang diperlukan yang dikemas di dalamnya untuk menjalankan skrip di mana saja pada mesin yang mendukung Docker. Sekarang, mari jalankan wadah satu kali dengan Image ini dan ekstrak tautan dari beberapa laman web langsung:

<div><img src="gambar/step1-5.png"></div>

Mari kita coba di halaman web dengan lebih banyak tautan di dalamnya:

<div><img src="gambar/step1-6.png"></div>

### Step 2: Link Extractor Module with Full URI and Anchor Text


### Step 3: Link Extractor API Service


### Step 4: Link Extractor API and Web Front End Services


### Step 5: Redis Service for Caching


### Step 6: Swap Python API Service with Ruby

### Kesimpulan 

Kami memulai tutorial ini dengan skrip Python sederhana yang menggores tautan dari URL halaman web tertentu. Kami mendemonstrasikan berbagai kesulitan dalam menjalankan skrip. Kami kemudian mengilustrasikan betapa mudahnya menjalankan dan membuat skrip menjadi portabel setelah dimasukkan ke dalam container. Pada langkah selanjutnya, kami secara bertahap mengembangkan skrip menjadi tumpukan aplikasi multi-layanan. Dalam prosesnya, kami menjelajahi berbagai konsep arsitektur layanan mikro dan bagaimana alat Docker dapat membantu dalam menyusun tumpukan multi-layanan. Terakhir, kami mendemonstrasikan kemudahan pertukaran komponen layanan mikro dan persistensi data.
