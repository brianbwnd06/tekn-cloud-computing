## Koneksi dan Membaca data dari mongodb menggunakan Go


1. Data pada mongoDB

    <img src="https://github.com/brianbwnd06/tekn-cloud-computing/blob/master/minggu-06/gambar/mysql7.png" width='600' />

2. Source Code ```Go``` untuk mengkoneksi dan membaca data dari mongoDB

```go
package main

import (
	"context"
	"fmt"
	"log"
	"time"

	"go.mongodb.org/mongo-driver/bson"
	"go.mongodb.org/mongo-driver/mongo"
	"go.mongodb.org/mongo-driver/mongo/options"
)

func main() {
	// 1. Buat koneksi ke server MongoDB
	client, err := mongo.NewClient(options.Client().ApplyURI("mongodb://localhost:27017"))
	if err != nil {
		log.Fatal(err)
	}

	ctx, cancel := context.WithTimeout(context.Background(), 10*time.Second)
	defer cancel()

	err = client.Connect(ctx)
	if err != nil {
		log.Fatal(err)
	}

	// 2. Akses database dan koleksi
	database := client.Database("dbtugas")
	collection := database.Collection("barang")

	// 3. Membaca data dari MongoDB
	cursor, err := collection.Find(ctx, bson.M{})
	if err != nil {
		log.Fatal(err)
	}
	defer cursor.Close(ctx)

	// 4. Menampilkan data
	for cursor.Next(ctx) {
		var result bson.M
		err := cursor.Decode(&result)
		if err != nil {
			log.Fatal(err)
		}
		printDocument(result)
	}

	if err := cursor.Err(); err != nil {
		log.Fatal(err)
	}

	// 5. Menutup koneksi
	err = client.Disconnect(ctx)
	if err != nil {
		log.Fatal(err)
	}
}

// Fungsi untuk mencetak dokumen
func printDocument(doc bson.M) {
	for key, value := range doc {
		fmt.Printf("%s: %v\n", key, value)
	}
	fmt.Println()
}

```

3. Hasil

    <img src="https://github.com/brianbwnd06/tekn-cloud-computing/blob/master/minggu-06/gambar/mysql7.png" width='600' />


