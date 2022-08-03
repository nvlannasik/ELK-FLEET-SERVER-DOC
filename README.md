# Configuration FLEET Server & Agent ELK

Repository ini berisi tentang tutorial konfigurasi FLEET Server & Agent ELK

# Spesification

**OS** : Ubuntu Server 20.04

**Machine type** : e2-medium

**Memory** : 8 GB

**Disk** : 50 GB

**Docker version** : 20.10.17, build 100c701

**Kibana Version** : 8.3.0

# Config Fleet Server

Untuk melakukan konfigurasi Fleet Server, silahkan ke dashboard kibana dan menuju

```bash
Home Page Kibana -> Add Integration -> Elastic Stack -> Fleet Server
```

Akan banyak pilihan integration yang tersedia, kita akan memilih **Fleet Server**.

![App Screenshot](/images/1.JPG)

Setelah memilih **Fleet Server**, akan muncul tampilan seperti ini:

![App Screenshot](/images/2.JPG)

Klik tombol **Add Fleet Server**, akan muncul tampilan seperti ini:

![App Screenshot](/images/3.JPG)

Masukan **Integration Name** sesuai dengan yang diinginkan, misal **fleet-server-1**.
Dan buat **Agent Policy** sesuai dengan yang diinginkan, misal **Fleet Agent Policy 1**.
Setelah selesai, klik tombol save lalu akan muncul tampilan seperti ini:

![App Screenshot](/images/4.JPG)

Klik tombol **Add Elastic Agent to your Host**, setelah itu akan muncul tampilan seperti ini:

![App Screenshot](/images/5.JPG)

Disini sebelum kita menambahkan fleet agent, kita harus menambahkan **fleet server host** terlebih dahulu. Klik tombol **Add Fleet Server**, maka akan muncul tampilan seperti ini:

![App Screenshot](/images/6.JPG)

Masukan Hostname untuk fleet server host dengan menggunakan protocol `HTTPS` dan Port `8220`, misal `https://annasik.site:8220`. Setelah selesai, klik tombol **Generate Fleet Server Policy** lalu setelah selesai akan muncul tampilan seperti ini:

![App Screenshot](/images/8.JPG)

Terlihat fleet server melakukan generate token untuk fleet agent, kita bisa mengikuti syntaxnya sesuai dengan environment yang ingin kita monitoring.

# Konfigurasi Fleet Agent

Setelah mendapatkan token untuk fleet agent & mendownload package elastic agent, kita akan mengkonfigurasi fleet agent dengan cara sebagai berikut:

![App Screenshot](/images/9.JPG)

masukkan perintah yang sudah didefinisikan sebelumnya ke dalam terminal. Ganti `http://localhost:9200` dengan `http://<hostname elastic server kita>:9200`. misal `http://annasik.site:9200`

Jika sukses, maka akan muncul tampilan seperti ini:

![App Screenshot](/images/10.JPG)

# Back to Dashboard Kibana

Selanjutnya kembali lagi ke dashboard Kibana, check fleet server yang sudah kita buat dengan menuju menu:

```bash
Management -> Fleet
```

maka akan muncul tampilan seperti ini:

![App Screenshot](/images/12.JPG)

terlihat bahwa environment fleet agent sudah terhubung dengan fleet server. Selanjutnya kita akan mengintegrasikan elastic agent dengan fleet server. Menuju menu:

```bash
Home Page Kibana -> Add Integration -> Elastic Stack -> Elastic Agent
```

![App Screenshot](/images/14.JPG)

Pilih **Elastic Agent**, maka akan muncul tampilan seperti ini:

![App Screenshot](/images/13.JPG)

klik tombol **Add Elastic Agent**, setelah itu akan muncul tampilan seperti ini:

![App Screenshot](/images/15.JPG)

Masukan **Integration Name** sesuai dengan yang diinginkan, misal **elastic_agent-1**. Lalu pilih integrationnya dengan existing integration dari fleet server policy yang sudah kita buat sebelumnya yaitu **Fleet Server Policy**.
Setelah selesai, klik tombol save lalu kita akan menuju menu:

```bash
Observability -> Metric -> Inventory
```

Maka akan muncul environment dari fleet agent yang sudah kita buat. Dan sudah bisa kita monitoring resourcenya

![App Screenshot](/images/16.JPG)

## Authors

- [Ahmad Naoval Annasik](https://www.github.com/octokatherine)
