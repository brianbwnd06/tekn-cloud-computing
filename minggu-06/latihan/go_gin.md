## Menggunakan Gin Untuk membuat RESTful API


1. Sumber Data

    MongoDB

    <img src="https://github.com/brianbwnd06/tekn-cloud-computing/blob/master/minggu-06/gambar/data-mongodb.jpg " width='600' />

    MySQL

    <img src="https://github.com/brianbwnd06/tekn-cloud-computing/blob/master/minggu-06/gambar/data-mysql.jpg" width='600' />

2. Source Code ```Go``` untuk menggunakan Gin untuk membuat RESTful API untuk membaca data dari mysql dan mongoDB

    ```go
    package main

    import (
        "database/sql"
        "context"
        "log"

        "github.com/gin-gonic/gin"
        "go.mongodb.org/mongo-driver/bson"
        "go.mongodb.org/mongo-driver/mongo"
        "go.mongodb.org/mongo-driver/mongo/options"
        _ "github.com/go-sql-driver/mysql"
    )

    // Struktur untuk data dari MySQL
    type MySQLData struct {
        id    int    `json:"id"`
        FirstName  string `json:"firstname"`
    }

    // Struktur untuk data dari MongoDB
    type MongoDBData struct {
        id    int `json:"id"`
        NamaBarang string `json:"NamaBarang"`
        Harga  int `json:"Harga"`
        Qty  int `json:"Qty"`
    }

    func main() {
        // Membuat koneksi ke MySQL
        mysqlDB, err := sql.Open("mysql", "root:@tcp(localhost:3306)/tekweb")
        if err != nil {
            log.Fatal(err)
        }
        defer mysqlDB.Close()

        // Mengecek koneksi MySQL
        err = mysqlDB.Ping()
        if err != nil {
            log.Fatal(err)
        }

        // Membuat koneksi ke MongoDB
        mongoClient, err := mongo.Connect(context.TODO(), options.Client().ApplyURI("mongodb://localhost:27017"))
        if err != nil {
            log.Fatal(err)
        }
        defer mongoClient.Disconnect(context.TODO())

        // Mengecek koneksi MongoDB
        err = mongoClient.Ping(context.TODO(), nil)
        if err != nil {
            log.Fatal(err)
        }

        // Membuat instance Gin
        r := gin.Default()

        // Endpoint untuk membaca data dari MySQL
        r.GET("/mysql-data", func(c *gin.Context) {
            // Query MySQL
            rows, err := mysqlDB.Query("SELECT id, FirstName FROM customers")
            if err != nil {
                c.JSON(500, gin.H{"error": err.Error()})
                return
            }
            defer rows.Close()

            // Mendapatkan hasil query
            var mysqlData []MySQLData
            for rows.Next() {
                var data MySQLData
                err := rows.Scan(&data.id, &data.FirstName)
                if err != nil {
                    c.JSON(500, gin.H{"error": err.Error()})
                    return
                }
                mysqlData = append(mysqlData, data)
            }

            c.JSON(200, mysqlData)
        })

        // Endpoint untuk membaca data dari MongoDB
        r.GET("/mongodb-data", func(c *gin.Context) {
            // Mendapatkan koleksi MongoDB
            collection := mongoClient.Database("dbtugas").Collection("barang")

            // Query MongoDB
            cursor, err := collection.Find(context.TODO(), bson.M{})
            if err != nil {
                c.JSON(500, gin.H{"error": err.Error()})
                return
            }
            defer cursor.Close(context.TODO())

            // Mendapatkan hasil query
            var mongoDBData []MongoDBData
            for cursor.Next(context.TODO()) {
                var data MongoDBData
                err := cursor.Decode(&data)
                if err != nil {
                    c.JSON(500, gin.H{"error": err.Error()})
                    return
                }
                mongoDBData = append(mongoDBData, data)
            }

            c.JSON(200, mongoDBData)
        })

        // Menjalankan server
        if err := r.Run(":8090"); err != nil {
            log.Fatal(err)
        }
    }


    ```
3. Gin Running

    <img src="https://github.com/brianbwnd06/tekn-cloud-computing/blob/master/minggu-06/gambar/gin-runing.jpg" width='600' />

4. Hasil dari mongoDB

    <img src="https://github.com/brianbwnd06/tekn-cloud-computing/blob/master/minggu-06/gambar/gin-mongodb-hasil.jpg" width='600' />

5. Hasil dari mySQL

    <img src="https://github.com/brianbwnd06/tekn-cloud-computing/blob/master/minggu-06/gambar/gin-mysql-hasil.jpg" width='600' />


