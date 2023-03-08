## 1. Instalasi Git

1. Double click pada file yang di-download. Akan dimunculkan lisensi. Klik **Next** untuk lanjut.

![01]<img src="https://github.com/brianbwnd06/tekn-cloud-computing/blob/master/minggu-01/gambar/instal-git-1.png" width='500' />

2. pilih lokasi instalasi

![02](gambar/instal-git-2.png)

3. Pilih komponen. Tidak perlu diubah-ubah, sesuai dengan default saja. Klik pada **Next**.

![03](gambar/instal-git-3.png)

4. Mengisi shortcut untuk menu Start. Gunakan default (Git), ganti jika ingin mengganti - misalnya Git VCS.

![04](gambar/instal-git-4.png)

5. Pilih editor yang akan digunakan bersama dengan Git. Pada pilihan ini, digunakan Notepad++.

![05](gambar/instal-git-5.png)

6. Pada saat instalasi, Git menyediakan akses git melalui Bash maupun command prompt. Pilih pilihan kedua supaya bisa menggunakan dari dua antarmuka tersebut. Bash adalah shell di Linux. Dengan menggunakan bash di Windows, pekerjaan di command line Windows bisa dilakukan menggunakan bash - termasuk ekskusi dari Git.

![06](gambar/instal-git-6.png)

7. Pilih OpenSSL untuk HTTPS. Git menggunakan https untuk akes ke repo GitHub atau repo-repo lain (GitLab, Assembla).

![07](gambar/instal-git-7.png)

8. Pilih pilihan pertama untuk konversi akhir baris (CR-LF).

![08](gambar/instal-git-8.png)

9. Pilih PuTTY untuk terminal yang digunakan untuk mengakses Git Bash.

![09](gambar/instal-git-9.png)

10. Untuk opsi ekstra, pilih serta aktifkan 1 dan 2.

![010](gambar/instal-git-10.png)

11. Setelah itu proses instalasi akan dilakukan.

![011](gambar/instal-git-11.png)

12. Jika selesai akan muncul dialog pemberitahuan. Klik pada **Finish**.

![012](gambar/instal-git-12.png)

13. Untuk menjalankan, dari Start menu, ketikkan "Git", akan muncul beberapa pilihan. Pilih "Git Bash" atau "Git GUI".
 
![013](gambar/instal-git-13.png)

14. Tampilan jika akan menggunakan "Git Bash"

![014](gambar/instal-git-14.png)

15. Tampilan jika akan menggunakan "Git GUI"

![015](gambar/instal-git-15.png)

16. Untuk mencoba dari command prompt, masuk ke command prompt, setelah itu eksekusi "git --version" untuk melihat apakah sudah terinstall atau belum. Jika sudah terinstall dengan benar, makan akan muncul hasil berikut:

![016](gambar/instal-git-16.png)
 
17. Untuk mencoba dari command prompt, masuk ke command prompt, setelah itu eksekusi "git --version" untuk melihat apakah sudah terinstall atau belum. Jika sudah terinstall dengan benar, makan akan muncul hasil berikut:

![016](gambar/instal-git-17.png)

18. Untuk mencoba dari command prompt, masuk ke command prompt, setelah itu eksekusi "git --version" untuk melihat apakah sudah terinstall atau belum. Jika sudah terinstall dengan benar, makan akan muncul hasil berikut:

![016](gambar/instal-git-18.png  = 250x250)



## 2. Konfigurasi awal yang harus dilakukan

Ada beberapa konfigurasi yang harus dupersiapakan sebelum mulai menggunakan Git, seperti name dan email.

Silahkan lakukan konfigurasi dengan perintah berikut ini :

```git config --global user.name "brayenbwnd06"
   git config --global user.email bwndbrayen06@gmail.com
```


Kemudian periksa konfigurasinya dengan perintah :

```git config --list```

![Konfigurasi](gambar/konfigurasi-git.png  = 250x250)


## 3. Membuat Repository

![Konfigurasi](gambar/repository-github.png  = 250x250)

