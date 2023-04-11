## INSTALASI DEVSTACK PADA UBUNTU
langkah-langkah untuk menginstal DevStack pada Ubuntu 20.04

1. Buka  ```terminal Ubuntu```
2. Pastikan semua paket sistem terbaru dengan menjalankan perintah berikut:  
     ```sh
     sudo apt-get update
     sudo apt-get upgrade 
     ```

3. Instal git dengan menjalankan perintah berikut  
   ```sh
    sudo apt-get install git
    ```
4. Unduh script DevStack dari repositori GitHub dengan menjalankan perintah berikut:  
    ```sh
    git clone https://github.com/openstack-dev/devstack.git 
    ```
    
5. Masuk ke direktori DevStack dengan menjalankan perintah berikut:  
    ```sh
    cd devstack 
    ```
    

6. Buat local.conffile dengan empat kata sandi yang telah ditetapkan di root repo devstack git.
    ```sh
    [[local|localrc]]
    ADMIN_PASSWORD=secret
    DATABASE_PASSWORD=$ADMIN_PASSWORD
    RABBIT_PASSWORD=$ADMIN_PASSWORD
    SERVICE_PASSWORD=$ADMIN_PASSWORD
    SERVICE_TOKEN=secret
    ```
    
    Konfigurasi ini akan mengatur kata sandi default ke "secret" dan token layanan ke "secret".

7. Simpan dan tutup file local.conf dengan menggunakan shortcut ```CTR+O``` untuk menyimpan dan ```CTR+X``` untuk menutup/keluar dari nano

8. Jalankan skrip stack dengan menjalankan perintah berikut:
    ```sh
    ./stack.sh
    ```
9. Tunggu proses instalasi hingga selesai.

#### Proses Instalasi menggunakan Terminal Pada UBUNTU

<img src="https://github.com/brianbwnd06/tekn-cloud-computing/blob/master/minggu-04/gambar/instalasi%20devstack.png" width='500' />


#### File local.conf
<img src="https://github.com/brianbwnd06/tekn-cloud-computing/blob/master/minggu-04/gambar/file%20local.conf.png" width='500' />