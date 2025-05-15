# tutorial9-subscriber

a. AMQP adalah sebuah protokol yang digunakan untuk pengiriman pesan yang mendukung autentikasi enkripsi dan berinteraksi lewat TCP

b. `guest` pertama adalah username untuk autentikasi ke server AMQP dan `guest` kedua adalah password untuk autentikasi ke server AMQP. localhost:5672 adalah lokasi lokal dengan port 5672 yang akan menjadi tempat berjalannya aplikasi.

![Simulating slow subscriber](./static/image/Spamming%20publisher%20simulate%20slow%20subscriber.png)
Pada gambar terlihat bahwa terdapat 25 queue yang masih perlu dijalankan. Hal ini dikarenakan subscriber hanya bisa menerima pesan baru setelah setiap 10 mili detik, dikarenakan oleh adanya `thread::sleep(ten_millis);`. Sehingga queue harus menunggu subscriber siap kembali untuk mengirimkan pesan berikutnya.