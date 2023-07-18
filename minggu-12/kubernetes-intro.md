# Kubernetes Intro - Hello Minikube

## Hello Minikube

Tutorial ini menunjukkan cara menjalankan aplikasi sampel di Kubernetes menggunakan minikube. Tutorial menyediakan image container yang menggunakan NGINX untuk menggemakan kembali semua permintaan.

### Tujuan
 * Men-deploy aplikasi sampel ke minikube
 * Jalankan aplikasi
 * Lihat log aplikasi

1. Sebelum memulai,  pastikan bahwa ```minikube``` dan ```kubectl``` sudah terinstal. Jika belum maka perlu menginstall terlebih dahulu

   <div><img src="gambar/instalasi.png"></div>
   <div><img src="gambar/instalasi-1.png"></div>

2. Langkah awal yaitu membuat ```Kluster Minikube``` dengan menggunakan perintah ```minikube start```

     <div><img src="gambar/mini-1.png"></div>
     
3. Selanjutnya buka terminal baru  dan masukan perintah ```minikube dahsboard``` untuk membuka Dashboard minikube

   <div><img src="gambar/mini-2.png"></div>
   <div><img src="gambar/mini-3.png"></div>
   
4. Membuat Penerapan
   ```Pod``` Kubernetes adalah grup dari satu atau lebih Container, yang diikat menjadi satu untuk tujuan administrasi dan jaringan. Pod dalam tutorial ini hanya memiliki satu Container. Deployment Kubernetes memeriksa 
    kesehatan Pod Anda dan memulai ulang Container Pod jika dihentikan. Deployment adalah cara yang disarankan untuk mengelola pembuatan dan penskalaan Pod.

   * Gunakan kubectl createperintah untuk membuat Deployment yang mengelola Pod. Pod menjalankan Container berdasarkan gambar Docker yang disediakan.
   * Lihat Penerapan:
   * Lihat Pod:
   * Lihat peristiwa kluster:
   * Lihat ```kubectl``` konfigurasi:
