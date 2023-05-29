## Koneksi dan Membaca data dari mysql menggunakan Go


1. Data pada mySQL

    <img src="https://github.com/brianbwnd06/tekn-cloud-computing/blob/master/minggu-06/gambar/data-mysql.jpg" width='600' />
    
2. Package yang digunakan

    ```go
       github.com/go-sql-driver/mysql
    ```

3. Source Code ```Go``` untuk mengkoneksi dan membaca data dari mongoDB

    ```go
    package main

    import (
        "database/sql"
        "fmt"

        _ "github.com/go-sql-driver/mysql"
    )

    func main() {
        // Konfigurasi koneksi ke database MySQL
        db, err := sql.Open("mysql", "root:@tcp(localhost:3306)/tekweb")
        if err != nil {
            panic(err.Error())
        }
        defer db.Close()

        // Mengecek koneksi database
        err = db.Ping()
        if err != nil {
            panic(err.Error())
        }

        fmt.Println("Koneksi database berhasil")

        // Membaca data dari tabel
        rows, err := db.Query("SELECT id, FirstName FROM customers")
        if err != nil {
            panic(err.Error())
        }
        defer rows.Close()

        // Mengambil data hasil query
        for rows.Next() {
            var column1 int
            var column2 string
            err = rows.Scan(&column1, &column2)
            if err != nil {
                panic(err.Error())
            }
            fmt.Println(column1, column2)
        }

        // Menangani error di dalam rows.Next()
        err = rows.Err()
        if err != nil {
            panic(err.Error())
        }
    }

    ```

4. Hasil

    <img src="https://github.com/brianbwnd06/tekn-cloud-computing/blob/master/minggu-06/gambar/mysql-hasil.jpg" width='600' />


