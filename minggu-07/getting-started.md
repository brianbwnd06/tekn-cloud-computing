# Getting Started Docker

1. Langkah pertama yaitu mengkloning repositori awal menggunakan perintah

    ```
        git clone https://github.com/docker/getting-started.git 
    ```

    <img src="https://github.com/brianbwnd06/tekn-cloud-computing/blob/master/minggu-07/gambar/gs1.png" width='400' />

    Hasil dari kloning repositori nya :

    <img src="https://github.com/brianbwnd06/tekn-cloud-computing/blob/master/minggu-07/gambar/gs2.png" width='250' />

2.  Berikutnya yaitu ubah direktori menjadi ```getting-started\app``` dengan menggunakan perintah pada terminal

    ```
        cd getting-started\app
    ```

3.  Membuat Dockerfile menggunakan perintah 
    ```
        type nul > Dockerfile
    ```

4. Setelah file ```Dockerfile``` berhasil dibuat maka tambahkan kode berikut

    ```
        # syntax=docker/dockerfile:1
   
        FROM node:18-alpine
        WORKDIR /app
        COPY . .
        RUN yarn install --production
        CMD ["node", "src/index.js"]
        EXPOSE 3000
    ```

5. Membuat image dengan langkah awal yaitu mengubah direktori menjadi ```getting-started\app``` kemudian masukan perintah berikut

    ```
        docker build -t getting-started .
    ```

     <img src="https://github.com/brianbwnd06/tekn-cloud-computing/blob/master/minggu-07/gambar/gs5.png" width='400' />
