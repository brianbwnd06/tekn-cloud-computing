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

   1. Gunakan ```kubectl create``` perintah untuk membuat Deployment yang mengelola Pod. Pod menjalankan Container berdasarkan gambar Docker yang disediakan. dengan menggunakan perintah ```kubectl create deployment hello-node -- 
     image=registry.k8s.io/e2e-test-images/agnhost:2.39 -- /agnhost netexec --http-port=8080```
     
      <div><img src="gambar/mini-4.png"></div>
      
   2. Lihat Penerapan dengan menggunakan perintah ```kubectl get deployments```

      <div><img src="gambar/mini-5.png"></div>
      
   3. Lihat Pod dengan menggunakan perintah ```kubectl get pods```
  
      <div><img src="gambar/mini-6.png"></div>
     
   4. Lihat peristiwa kluster dengan menggunakan perintah ```kubectl get events```
  
      <div><img src="gambar/mini-7.png"></div>

     
   5. Lihat ```kubectl``` konfigurasi dengan menggunakan perintah ```kubectl config view```
  
      <div><img src="gambar/mini-8.png"></div>

5. Membuat Layanan
   Secara default, Pod hanya dapat diakses melalui alamat IP internalnya di dalam kluster Kubernetes. Agar hello-nodeContainer dapat diakses dari luar jaringan virtual Kubernetes, Anda harus mengekspos Pod sebagai Layanan    Kubernetes

   1. Paparkan Pod ke internet publik menggunakan ```kubectl expose``` perintah: ```kubectl expose deployment hello-node --type=LoadBalancer --port=8080```

      <div><img src="gambar/mini-8.png"></div>

      Bendera ```--type=LoadBalancer``` menunjukkan bahwa Anda ingin mengekspos Layanan Anda di luar cluster.

      Kode aplikasi di dalam gambar uji hanya mendengarkan pada TCP port 8080. Jika Anda menggunakan ```kubectl expose``` port yang berbeda, klien tidak dapat terhubung ke port lain tersebut.

   2. Lihat Layanan yang Anda buat: dengan menggunakan perintah ```kubectl get services```
  
       <div><img src="gambar/mini-8.png"></div>
  
      Pada penyedia cloud yang mendukung penyeimbang muatan, alamat IP eksternal akan disediakan untuk mengakses Layanan. Di minikube, ```LoadBalancer``` tipe tersebut membuat Layanan dapat diakses melalui ```minikube service``` perintah.
      
   3. Jalankan perintah berikut: ```minikube service hello-node```
  
      <div><img src="gambar/mini-8.png"></div>

   
