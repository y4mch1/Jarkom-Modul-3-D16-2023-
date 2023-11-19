# Jarkom-Modul-3-D16-2023

**Praktikum Jaringan Komputer Modul 3 Tahun 2023**

## Author

| Nama                  | NRP        | 
| --------------------- | ---------- | 
| Dicky Indra Kuncahyo| 5025201250|
| Widian Sasi Disertasiani | 5025211024| 

# Laporan Resmi

## Daftar Isi

- [Laporan Resmi](#laporan-resmi)
  - [Daftar Isi](#daftar-isi)
  - [Topologi](#topologi)
  - [Network Configuration](#network-configuration)
- [Soal 1](#soal-1)
- [Soal 2](#soal-2)
- [Soal 3](#soal-3)
- [Soal 4](#soal-4)
- [Soal 5](#soal-5)
- [Soal 6](#soal-6)
- [Soal 7](#soal-7)
- [Soal 8](#soal-8)
- [Soal 9](#soal-9)
- [Soal 10](#soal-10)
- [Soal 11](#soal-11)
- [Soal 12](#soal-12)
- [Soal 13](#soal-13)
- [Soal 14](#soal-14)
- [Soal 15](#soal-15)
- [Soal 16](#soal-16)
- [Soal 17](#soal-17)
- [Soal 18](#soal-18)
- [Soal 19](#soal-19)
- [Soal 20](#soal-20)

## Topologi

![topologi](https://media.discordapp.net/attachments/1170650328950124618/1175662307993464872/image.png?ex=656c0bd8&is=655996d8&hm=381d89863d4c811fe349454440130ebbac4aff98f0f26099b035ff0b3de8c643&=)

## Network Configuration

- **Aura**


```
auto eth0
iface eth0 inet dhcp


auto eth1
iface eth1 inet static
        address 192.199.1.8
        netmask 255.255.255.0


auto eth2
iface eth2 inet static
        address 192.199.2.8
        netmask 255.255.255.0


auto eth3
iface eth3 inet static
        address 192.199.3.8
        netmask 255.255.255.0


auto eth4
iface eth4 inet static
        address 192.199.4.8
        netmask 255.255.255.0

```

- **Himmel**

```
auto eth0
iface eth0 inet static
        address 192.199.1.1
        netmask 255.255.255.0
        gateway 192.199.1.8


```

- **Heiter**

```
auto eth0
iface eth0 inet static
        address 192.199.1.2
        netmask 255.255.255.0
        gateway 192.199.1.8

```

- **Denken**

```
auto eth0
iface eth0 inet static
        address 192.199.2.1
        netmask 255.255.255.0
        gateway 192.199.2.8

```

- **Eisen**

```
auto eth0
iface eth0 inet static
        address 192.199.2.2
        netmask 255.255.255.0
        gateway 192.199.2.8

```

- **Lugner**

```
auto eth0
iface eth0 inet static
        address 192.199.3.1
        netmask 255.255.255.0
        gateway 192.199.3.8

```

- **Linie**

```
auto eth0
iface eth0 inet static
        address 192.199.3.2
        netmask 255.255.255.0
        gateway 192.199.3.8

```

- **Lawine**

```
auto eth0
iface eth0 inet static
        address 192.199.3.3
        netmask 255.255.255.0
        gateway 192.199.3.8

```

- **Fieren**

```
auto eth0
iface eth0 inet static
        address 192.199.4.1
        netmask 255.255.255.0
        gateway 192.199.4.8

```

- **Flamme**

```
auto eth0
iface eth0 inet static
        address 192.199.4.2
        netmask 255.255.255.0
        gateway 192.199.4.8

```

- **Fern**

```
auto eth0
iface eth0 inet static
        address 192.199.4.3
        netmask 255.255.255.0
        gateway 192.199.4.8

```

- **Client**

```
auto eth0
iface eth0 inet dhcp

```


## Soal 1-5

Setelah mengalahkan Demon King, perjalanan berlanjut. Kali ini, kalian diminta untuk melakukan register domain berupa riegel.canyon.yyy.com untuk worker Laravel dan granz.channel.yyy.com untuk worker PHP (0) mengarah pada worker yang memiliki IP [prefix IP].x.1.

Lakukan konfigurasi sesuai dengan peta yang sudah diberikan.

Kemudian, karena masih banyak spell yang harus dikumpulkan, bantulah para petualang untuk memenuhi kriteria berikut.:

- Semua CLIENT harus menggunakan konfigurasi dari DHCP Server.

- Client yang melalui Switch3 mendapatkan range IP dari [prefix IP].3.16 - [prefix IP].3.32 dan [prefix IP].3.64 - [prefix IP].3.80 (2)

- Client yang melalui Switch4 mendapatkan range IP dari [prefix IP].4.12 - [prefix IP].4.20 dan [prefix IP].4.160 - [prefix IP].4.168 (3)

- Client mendapatkan DNS dari Heiter dan dapat terhubung dengan internet melalui DNS tersebut (4)

- Lama waktu DHCP server meminjamkan alamat IP kepada Client yang melalui Switch3 selama 3 menit sedangkan pada client yang melalui Switch4 selama 12 menit. Dengan waktu maksimal dialokasikan untuk peminjaman alamat IP selama 96 menit (5)


### Penyeleseaian

**Heiter**

```
apt-get update
apt-get install bind9 -y
echo 'zone "riegel.canyon.d16.com" {
type master;
file "/etc/bind/jarkom/riegel.canyon.d16.com";
};
zone "granz.channel.d16.com" {
type master;
file "/etc/bind/jarkom/granz.channel.d16.com";
};' > /etc/bind/named.conf.local
mkdir /etc/bind/jarkom
echo ';
; BIND data file for local loopback interface
;
$TTL 604800
@ IN SOA riegel.canyon.d16.com.
root.riegel.canyon.d16.com. (
2023111301 ; Serial
604800 ; Refresh
86400 ; Retry
2419200 ; Expire
604800 ) ; Negative Cache TTL
;
@ IN NS riegel.canyon.d16.com.
@ IN A 192.199.4.1 ; IP Laravel Worker' >
/etc/bind/jarkom/riegel.canyon.d16.com
echo ';
; BIND data file for local loopback interface
;
$TTL 604800
@ IN SOA granz.channel.d16.com.
root.granz.channel.d16.com. (
2023111301 ; Serial
604800 ; Refresh
86400 ; Retry
2419200 ; Expire
604800 ) ; Negative Cache TTL
;
@ IN NS granz.channel.d16.com.
@ IN A 192.199.2.2 ; IP Load Balancer' >
/etc/bind/jarkom/granz.channel.d16.com
echo 'options {
directory "/var/cache/bind";
forwarders {
192.168.122.1;
};
// dnssec-validation auto;
allow-query{any;};
auth-nxdomain no; # conform to RFC1035
listen-on-v6 { any; };
}; ' >/etc/bind/named.conf.options
service bind9 restart
```

**Himmel**

```
apt-get update
apt-get install isc-dhcp-server -y
dhcpd --version
echo '
# Defaults for isc-dhcp-server (sourced by /etc/init.d/isc-dhcp-server)
# Path to dhcpd'\''s config file (default: /etc/dhcp/dhcpd.conf).
#DHCPDv4_CONF=/etc/dhcp/dhcpd.conf
#DHCPDv6_CONF=/etc/dhcp/dhcpd6.conf
# Path to dhcpd'\''s PID file (default: /var/run/dhcpd.pid).
#DHCPDv4_PID=/var/run/dhcpd.pid
#DHCPDv6_PID=/var/run/dhcpd6.pid
# Additional options to start dhcpd with.
# Don'\''t use options -cf or -pf here; use DHCPD_CONF/ DHCPD_PID
instead
#OPTIONS=""
# On what interfaces should the DHCP server (dhcpd) serve DHCP
requests?
# Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"' > /etc/default/isc-dhcp-server
echo 'subnet 192.199.1.0 netmask 255.255.255.0 {
}
subnet 192.199.2.0 netmask 255.255.255.0 {
}
subnet 192.199.3.0 netmask 255.255.255.0 {
range 192.199.3.16 192.199.3.32;
range 192.199.3.64 192.199.3.80;
option routers 192.199.3.8;
option broadcast-address 192.199.3.255;
option domain-name-servers 192.199.1.2;
default-lease-time 180;
max-lease-time 5760;
}
subnet 192.199.4.0 netmask 255.255.255.0 {
range 192.199.4.12 192.199.4.20;
range 192.199.4.160 192.199.4.168;
option routers 192.199.4.8;
option broadcast-address 192.199.4.255;
option domain-name-servers 192.199.1.2;
default-lease-time 720;
max-lease-time 5760;
}' > /etc/dhcp/dhcpd.conf
service isc-dhcp-server restart
service isc-dhcp-server status
```

**Aura**

```
apt-get update
apt-get install isc-dhcp-relay -y
service isc-dhcp-relay start
echo '
SERVERS="192.199.1.1"
INTERFACES="eth1 eth2 eth3 eth4"
OPTIONS=""' > /etc/default/isc-dhcp-relay
echo 'net.ipv4.ip_forward=1' > /etc/sysctl.conf
service isc-dhcp-relay restart
```
### Bukti


![soal2-1](https://media.discordapp.net/attachments/1170650328950124618/1175662421671694426/image.png?ex=656c0bf4&is=655996f4&hm=9033f012773ac81067ce8ae167375311dfe17f2e3116da011df2c514d2f8991e&=)


## Soal 6

Pada masing-masing worker PHP, lakukan konfigurasi virtual host untuk website berikut dengan menggunakan php 7.3. (6)

### Penyelesaian

**Eisen**

```
apt-get update
apt-get install bind9 nginx


echo '
 upstream myweb  {
        server 192.199.3.1; #IP Lugner
        server 192.199.3.2; #IP Linie
        server 192.199.3.3; #IP Lawine
 }


 server {
        listen 80;
        server_name granz.channel.d16.com;


        location / {
        proxy_pass http://myweb;
        }
 }' > /etc/nginx/sites-available/lb-jarkom


ln -s /etc/nginx/sites-available/lb-jarkom /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default


service nginx restart
nginx -t



```

**PHP Woorker**

```
apt-get update
apt-get install lynx -y
apt-get install wget -y
apt-get install unzip -y
apt-get install nginx -y
apt-get install php7.3 -y
apt-get install php7.3-fpm -y


mkdir -p /var/www/granz.channel.d16


wget --no-check-certificate 'https://drive.google.com/uc?export=download&id=1ViSkRq7SmwZgdK64eRbr5Fm1EGCTPrU1' -O /var/www/granz.channel.d16.zip
unzip /var/www/granz.channel.d16.zip -d /var/www/granz.channel.d16
mv /var/www/granz.channel.d16/modul-3 /var/www/granz.channel.d16
rm -rf /var/www/granz.channel.d16.zip


echo nameserver 192.199.1.2 > /etc/resolv.conf


echo '
server {


        listen 80;


        root /var/www/granz.channel.d16;


        index index.php index.html index.htm;
        server_name _;


        location / {
                        try_files $uri $uri/ /index.php?$query_string;
        }


        # pass PHP scripts to FastCGI server
        location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.3-fpm.sock;
        }


location ~ /\.ht {
                        deny all;
        }


        error_log /var/log/nginx/jarkom_error.log;
        access_log /var/log/nginx/jarkom_access.log;
 }' > /etc/nginx/sites-available/granz.channel.d16


echo '<!DOCTYPE html>
<html>
<head>
    <title>Granz Channel Map</title>
    <link rel="stylesheet" type="text/css" href="css/styles.css">
</head>
<body>
    <div class="container">
        <h1>Welcome to Granz Channel</h1>
        <p><?php
            $hostname = gethostname();
            echo "Request ini dihandle oleh: $hostname<br>"; ?> </p>
        <p>Enter your name to validate:</p>
        <form method="POST" action="index.php">
            <input type="text" name="name" id="nameInput">
            <button type="submit" id="submitButton">Submit</button>
        </form>
        <p id="greeting"><?php
            if(isset($_POST['name'])) {
                $name = $_POST['name'];
                echo "Hello, $name!";
            }
        ?></p>
    </div>


    <script src="js/script.js"></script>
</body>' > /var/www/granz.channel.d16/index.php


ln -s /etc/nginx/sites-available/granz.channel.d16 /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default


service php7.3-fpm start
service php7.3-fpm restart
service nginx restart
nginx -t

```

### Bukti

**Client**

```
lynx granz.channel.d16.com
```

![soal6](https://media.discordapp.net/attachments/1170650328950124618/1175662490948997234/image.png?ex=656c0c04&is=65599704&hm=a332e1605c394a317253d4aa3e4a3a127081897c58b928c574fe2e3310efca9e&=)

# Soal 7

Kepala suku dari Bredt Region memberikan resource server sebagai berikut:
- Lawine, 4GB, 2vCPU, dan 80 GB SSD.
- Linie, 2GB, 2vCPU, dan 50 GB SSD.
- Lugner 1GB, 1vCPU, dan 25 GB SSD.
aturlah agar Eisen dapat bekerja dengan maksimal, lalu lakukan testing dengan 1000 request dan 100 request/second. (7)

### Penyelesaian 

**Revolte**

```
apt-get update
apt-get install apache2-utils -y
ab -V


echo nameserver 192.168.122.1 > /etc/resolv.conf
ab -n 1000 -c 100 http://192.199.2.2/
```
**PHP Worker**

```
cat /var/log/nginx/jarkom_access.log| grep "GET" | wc -l
```

### Bukti

![soal7-1](https://media.discordapp.net/attachments/1170650328950124618/1175662589833920604/image.png?ex=656c0c1c&is=6559971c&hm=b6ca90bd0da26a7dbdb0a54633633564100d5f1c54f0d5aa43d4c0e40631900a&=&width=614&height=701)

![soal7-2](https://media.discordapp.net/attachments/1170650328950124618/1175662647627219044/image.png?ex=656c0c29&is=65599729&hm=239a9e69abf64ddbd67816970119d5a3fd7727e82e8c93debd2a90de52b657e4&=)

![soal7-3](https://media.discordapp.net/attachments/1170650328950124618/1175662686831398922/image.png?ex=656c0c33&is=65599733&hm=ecfb1a8ab3a74db5721cd987fe69e127ba8ffc7acac92fe449dc8ff2e96a92fe&=)

![soal7-4](https://media.discordapp.net/attachments/1170650328950124618/1175662733979570227/image.png?ex=656c0c3e&is=6559973e&hm=3118272622cdfc5804132d7d69df92f3091e3dfd4c4326b48dbb2f1eacc68e2d&=)

# Soal 8

Karena diminta untuk menuliskan grimoire, buatlah analisis hasil testing dengan 200 request dan 10 request/second masing-masing algoritma Load Balancer dengan ketentuan sebagai berikut:
Nama Algoritma Load Balancer
Report hasil testing pada Apache Benchmark
Grafik request per second untuk masing masing algoritma. 
Analisis (8)

### Penyelesaian
```
Client (Revolte):
ab -n 200 -c 10 http://192.199.2.2/


Worker (3 PHP Worker):
cat /var/log/nginx/jarkom_access.log| grep "GET" | wc -l
truncate -s 0 /var/log/nginx/jarkom_access.log
htop


(Algo masukin ke Load Balancer Eisen)
Round Robin (default)
apt-get update
apt-get install bind9 nginx


echo '
 upstream myweb  {
        server 192.199.3.1; #IP Lugner
        server 192.199.3.2; #IP Linie
        server 192.199.3.3; #IP Lawine
 }


 server {
        listen 80;
        server_name granz.channel.d16.com;


        location / {
        proxy_pass http://myweb/;
        }
 }' > /etc/nginx/sites-available/lb-jarkom


ln -s /etc/nginx/sites-available/lb-jarkom /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default


service nginx restart
nginx -t




Weighted Round Robin
echo '
 upstream myweb  {
        server 192.199.3.1 weight=4; #IP Lugner
        server 192.199.3.2 weight=2; #IP Linie
        server 192.199.3.3 weight=1; #IP Lawine
 }


 server {
        listen 80;
        server_name granz.channel.d16.com;


        location / {
        proxy_pass http://myweb/;
        }
 }' > /etc/nginx/sites-available/lb-jarkom


unlink /etc/nginx/sites-enabled/lb-jarkom
ln -s /etc/nginx/sites-available/lb-jarkom /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default


service nginx restart
nginx -t




Least Connection
echo '
 upstream myweb  {
        least_conn;
        server 192.199.3.1; #IP Lugner
        server 192.199.3.2; #IP Linie
        server 192.199.3.3; #IP Lawine
 }


 server {
        listen 80;
        server_name granz.channel.d16.com;


        location / {
        proxy_pass http://myweb/;
        proxy_set_header    X-Real-IP $remote_addr;
        proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header    Host $http_host;
        }
 }' > /etc/nginx/sites-available/lb-jarkom


ln -s /etc/nginx/sites-available/lb-jarkom /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default


service nginx restart
nginx -t


IP Hash
echo '
 upstream myweb  {
        ip_hash;
        server 192.199.3.1; #IP Lugner
        server 192.199.3.2; #IP Linie
        server 192.199.3.3; #IP Lawine
 }


 server {
        listen 80;
        server_name granz.channel.d16.com;


        location / {
        proxy_pass http://myweb/;
        proxy_set_header    X-Real-IP $remote_addr;
        proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header    Host $http_host;
        }
 }' > /etc/nginx/sites-available/lb-jarkom


ln -s /etc/nginx/sites-available/lb-jarkom /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default


service nginx restart
nginx -t
```

### Bukti



## Soal 9
Dengan menggunakan algoritma Round Robin, lakukan testing dengan menggunakan 3 worker, 2 worker, dan 1 worker sebanyak 100 request dengan 10 request/second, kemudian tambahkan grafiknya pada grimoire. (9)

### Penyelesaian
Dengan Penyelesaian yang sama di nomor 8, namun setiap percobaan 1 worker, maka 3 worker distop, 2 wroker maka 1 qorker distop, dan seterusnya.

## Soal 10

Selanjutnya coba tambahkan konfigurasi autentikasi di LB dengan dengan kombinasi username: “netics” dan password: “ajkyyy”, dengan yyy merupakan kode kelompok. Terakhir simpan file “htpasswd” nya di /etc/nginx/rahasisakita/ (10)

### Penyelesaian

**Eisen**
```
echo '
 upstream myweb  {
        server 192.199.3.1; #IP Lugner
        server 192.199.3.2; #IP Linie
        server 192.199.3.3; #IP Lawine
 }


 server {
        listen 80;
        server_name granz.channel.d16.com;


        location / {
        proxy_pass http://myweb;
        auth_basic "Restricted Access";
        auth_basic_user_file /etc/nginx/rahasisakita/.htpasswd;
        }
 }' > /etc/nginx/sites-available/lb-jarkom


unlink /etc/nginx/sites-enabled/lb-jarkom
ln -s /etc/nginx/sites-available/lb-jarkom /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default


mkdir /etc/nginx/rahasisakita/
htpasswd -c -b /etc/nginx/rahasisakita/.htpasswd netics ajkd16


service nginx restart
nginx -t

```

### Bukti

**Client**

```
lynx granz.channel.d16.com
```
![soal10-1](https://media.discordapp.net/attachments/1170650328950124618/1175662808407482468/image.png?ex=656c0c50&is=65599750&hm=57d61c89748ec709bd64b991e4ad43aa49367151b862ef3f65a6d14d82f8218d&=)


## Soal 11

Lalu buat untuk setiap request yang mengandung /its akan di proxy passing menuju halaman https://www.its.ac.id. (11) hint: (proxy_pass)

**Eisen**
```
echo '
 upstream myweb  {
        server 192.199.3.1; #IP Lugner
        server 192.199.3.2; #IP Linie
        server 192.199.3.3; #IP Lawine
 }


 server {
        listen 80;
        server_name granz.channel.d16.com;


        location / {
                proxy_pass http://myweb;
                auth_basic "Restricted Access";
                auth_basic_user_file /etc/nginx/rahasisakita/.htpasswd;
        }


        location ~* /its {
                proxy_pass https://www.its.ac.id;
        }


 }' > /etc/nginx/sites-available/lb-jarkom


unlink /etc/nginx/sites-enabled/lb-jarkom
ln -s /etc/nginx/sites-available/lb-jarkom /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default


mkdir -p /etc/nginx/rahasisakita/
htpasswd -c -b /etc/nginx/rahasisakita/.htpasswd netics ajkd16


service nginx restart
nginx -t


```

### Bukti

**Client**

```
lynx granz.channel.d16.com/its
```
![soal11-1](https://media.discordapp.net/attachments/1170650328950124618/1175662866943201290/image.png?ex=656c0c5e&is=6559975e&hm=ec6fbb05b9b79f6223752f7a00ff4ac37d7ce1ce259fbcdb61adde6a7a83bdd5&=)

## Soal 12

Selanjutnya LB ini hanya boleh diakses oleh client dengan IP [Prefix IP].3.69, [Prefix IP].3.70, [Prefix IP].4.167, dan [Prefix IP].4.168. (12) hint: (fixed in dulu clinetnya)

**Eisen**
```
echo '
 upstream myweb  {
        server 192.199.3.1; #IP Lugner
        server 192.199.3.2; #IP Linie
        server 192.199.3.3; #IP Lawine
 }


 server {
        listen 80;
        server_name granz.channel.d16.com;


        location / {
                proxy_pass http://myweb;
                auth_basic "Restricted Access";
                auth_basic_user_file /etc/nginx/rahasisakita/.htpasswd;


                allow 192.199.3.69;
                allow 192.199.3.70;
                allow 192.199.4.167;
                allow 192.199.4.168;
                deny all;
        }


        location ~* /its {
                proxy_pass https://www.its.ac.id;
        }


 }' > /etc/nginx/sites-available/lb-jarkom


unlink /etc/nginx/sites-enabled/lb-jarkom
ln -s /etc/nginx/sites-available/lb-jarkom /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default


mkdir -p /etc/nginx/rahasisakita/
htpasswd -c -b /etc/nginx/rahasisakita/.htpasswd netics ajkd16


service nginx restart
nginx -t




```

### Bukti

**Client**

```
lynx granz.channel.d16.com/its
```
![soal11-1](https://media.discordapp.net/attachments/1170650328950124618/1175662866943201290/image.png?ex=656c0c5e&is=6559975e&hm=ec6fbb05b9b79f6223752f7a00ff4ac37d7ce1ce259fbcdb61adde6a7a83bdd5&=)
