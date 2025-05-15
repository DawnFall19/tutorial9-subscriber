# tutorial9-subscriber

a. AMQP adalah sebuah protokol yang digunakan untuk pengiriman pesan yang mendukung autentikasi enkripsi dan berinteraksi lewat TCP

b. `guest` pertama adalah username untuk autentikasi ke server AMQP dan `guest` kedua adalah password untuk autentikasi ke server AMQP. localhost:5672 adalah lokasi lokal dengan port 5672 yang akan menjadi tempat berjalannya aplikasi.

## Simulating slow subscriber
![Simulating slow subscriber](./static/image/Spamming%20publisher%20simulate%20slow%20subscriber.png)
Pada gambar terlihat bahwa terdapat 25 queue yang masih perlu dijalankan. Hal ini dikarenakan subscriber hanya bisa menerima pesan baru setelah setiap 10 mili detik, dikarenakan oleh adanya `thread::sleep(ten_millis);`. Sehingga queue harus menunggu subscriber siap kembali untuk mengirimkan pesan berikutnya.

## Using 3 slow subscribers
![console of 3 slow subscribers](./static/image/Console%20with%203%20slow%20subscribers.png)
![3 slow subscribers graph](./static/image/Spamming%20but%20with%203%20slow%20subscribers.png)
Pada gambar pertama terlihat bahwa pesan yang dikirim menjadi terpecah-pecah diantara masing-masing subscriber. Hal ini menyebabkan beban yang harus ditanggung oleh setiap subscriber berkurang sehingga durasi menunggu dan jumlah queue yang terjadi menurun drastis. Sehingga terlihat pada grafik pada gambar kedua jauh lebih kecil dan lebih cepat turun dibandingkan dengan grafik yang ditunjukkan dengan hanya satu subscriber saja.