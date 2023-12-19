# Jarkom-Modul-5-D19-2023

Anggota:
| Nama | NRP |
|---------------------------|------------|
|Adrian Ismu Arifianto | 5025211116 |
|Ahmad Rafif Hikmatiar | 5025211247 |

## Persiapan

### Topologi

![image](https://github.com/adrianismu/Jarkom-Modul-5-D19-2023/assets/71255346/ddc63b4c-d205-4fde-b3c5-3a8141de735c)

### Rute

| Subnet | Rute                                           | Jumlah IP | Netmask |
| ------ | ---------------------------------------------- | --------- | ------- |
| A1     | Aura-Heiter                                    | 2         | /30     |
| A2     | Heiter-TurkRegion                               | 1023      | /21     |
| A3     | Heiter-Switch3-Sein-Switch3-GrobeForest         | 514       | /22     |
| A4     | Aura-Frieren                                   | 2         | /30     |
| A5     | Frieren-Stark                                  | 2         | /30     |
| A6     | Frieren-Himmel                                 | 2         | /30     |
| A7     | Himmel-LaubHills                               | 256       | /23     |
| A8     | Himmel-Switch1-SchwerMountain-Switch1-Fern      | 66        | /25     |
| A9     | Fern-Richter                                   | 2         | /30     |
| A10    | Fern-Switch2-Revolte                            | 2         | /30     |
| Total  |                                                | 1871      | /20     |

### Tree


### Pembagian IP

Berikut adalah pembagian IP yang telah kami dapatkan.

| Subnet | Network ID    | Broadcast      | Mask | Dec Mask       |
| ------ | ------------- | -------------- | ---- | -------------- |
| A1     | 10.31.14.128  | 10.31.14.131   | /30  | 255.255.255.252 |
| A2     | 10.31.0.0     | 10.31.7.255    | /21  | 255.255.248.0   |
| A3     | 10.31.8.0     | 10.31.11.255   | /22  | 255.255.252.0   |
| A4     | 10.31.14.132  | 10.31.14.135   | /30  | 255.255.255.252 |
| A5     | 10.31.14.136  | 10.31.14.139   | /30  | 255.255.255.252 |
| A6     | 10.31.14.140  | 10.31.14.143   | /30  | 255.255.255.252 |
| A7     | 10.31.12.0    | 10.31.13.255   | /23  | 255.255.254.0   |
| A8     | 10.31.14.0    | 10.31.14.127   | /25  | 255.255.255.128 |
| A9     | 10.31.14.144  | 10.31.14.147   | /30  | 255.255.255.252 |
| A10    | 10.31.14.148  | 10.31.14.151   | /30  | 255.255.255.252 |

dan berikut adalah IP yang didapatkan setiap node

| Subnet | Node            | IP           |
| ------ | --------------- | ------------ |
| A1     | Aura            | 10.31.14.129 |
|        | Heiter          | 10.31.14.130 |
| A2     | Heiter          | 10.31.0.1    |
|        | TurkRegion      | DHCP         |
| A3     | Heiter          | 10.31.8.1    |
|        | Sein            | 10.31.8.2    |
|        | GrobeForest     | DHCP         |
| A4     | Aura            | 10.31.14.133 |
|        | Frieren         | 10.31.14.134 |
| A5     | Frieren         | 10.31.14.137 |
|        | Stark           | 10.31.14.138 |
| A6     | Frieren         | 10.31.14.141 |
|        | Himmel          | 10.31.14.142 |
| A7     | Himmel          | 10.31.12.1   |
|        | LaubHills       | DHCP         |
| A8     | Himmel          | 10.31.14.1   |
|        | SchwerMountain  | DHCP         |
|        | Fern            | 10.31.14.2   |
| A9     | Fern            | 10.31.14.145 |
|        | Richter         | 10.31.14.146 |
| A10    | Fern            | 10.31.14.149 |
|        | Revolte         | 10.31.14.150 |


### Subnetting

Di bawah ini adalah pengelompokan subnet yang telah disesuaikan dengan alamat IP yang telah diperoleh.

#### Aura
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 10.31.14.129
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 10.31.14.133
	netmask 255.255.255.252
```

#### Heiter 
```
auto eth0
iface eth0 inet static
	address 10.31.14.130
	netmask 255.255.255.252
	gateway 10.31.14.129
	up echo nameserver 192.168.122.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 10.31.0.1
	netmask 255.255.248.0

auto eth2
iface eth2 inet static
	address 10.31.8.1
	netmask 255.255.252.0
```

#### Frieren 
```
auto eth0
iface eth0 inet static
	address 10.31.14.134
	netmask 255.255.255.252
	gateway 10.31.14.133
        up echo nameserver 192.168.122.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 10.31.14.137
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 10.31.14.141
	netmask 255.255.255.252
```

#### Himmel 

```
auto eth0
iface eth0 inet static
	address 10.31.14.142
	netmask 255.255.255.252
	gateway 10.31.14.141
        up echo nameserver 192.168.122.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 10.31.12.1
	netmask 255.255.254.0

auto eth2
iface eth2 inet static
	address 10.31.14.1
	netmask 255.255.255.128
```

#### Fern 
```
auto eth0
iface eth0 inet static
	address 10.31.14.2
	netmask 255.255.255.128
	gateway 10.31.14.1
        up echo nameserver 192.168.122.1 > /etc/resolv.conf

auto eth1
iface eth1 inet static
	address 10.31.14.145
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 10.31.14.149
	netmask 255.255.255.252
```

#### Revolte
```
auto eth0
iface eth0 inet static
	address 10.31.14.150
	netmask 255.255.255.252
	gateway 10.31.14.149
        up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

#### Richter
```
auto eth0
iface eth0 inet static
	address 10.31.14.146
	netmask 255.255.255.252
	gateway 10.31.14.145
        up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

#### Stark
```
auto eth0
iface eth0 inet static
	address 10.31.14.138
	netmask 255.255.255.252
	gateway 10.31.14.137
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

#### Sein 
```
auto eth0
iface eth0 inet static
	address 10.31.8.2
	netmask 255.255.252.0
	gateway 10.31.8.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

#### Client 
```
auto eth0
iface eth0 inet dhcp
```

### Routing

#### Aura
```bash
route add -net 10.31.14.140 netmask 255.255.255.252 gw 10.31.14.134
route add -net 10.31.14.136 netmask 255.255.255.252 gw 10.31.14.134
route add -net 10.31.12.0   netmask 255.255.254.0 gw 10.31.14.134
route add -net 10.31.14.0   netmask 255.255.255.128 gw 10.31.14.134
route add -net 10.31.14.144 netmask 255.255.255.252 gw 10.31.14.134
route add -net 10.31.14.148 netmask 255.255.255.252 gw 10.31.14.134

route add -net 10.31.0.0 netmask 255.255.248.0 gw 10.31.14.130
route add -net 10.31.8.0 netmask 255.255.252.0 gw 10.31.14.130
```

#### Heiter 
```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.31.14.129
```

#### Frieren 
```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.31.14.133

route add -net 10.31.12.0   netmask 255.255.254.0 gw 10.31.14.142
route add -net 10.31.14.0   netmask 255.255.255.128 gw 10.31.14.142
route add -net 10.31.14.144 netmask 255.255.255.252 gw 10.31.14.142
route add -net 10.31.14.148 netmask 255.255.255.252 gw 10.31.14.142
```

#### Himmel 

```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.31.14.141

route add -net 10.31.14.144 netmask 255.255.255.252 gw 10.31.14.2
route add -net 10.31.14.148 netmask 255.255.255.252 gw 10.31.14.2
```

#### Fern 
```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.31.14.1
```
### Konfigurasi

#### DNS Server

Router Richter bertindak sebagai server DNS dan akan diatur konfigurasinya menggunakan skrip bash yang akan disediakan.
```bash
apt-get update

apt-get install bind9 -y

service bind9 restart

echo '
options {
        directory "/var/cache/bind";

        forwarders {
                192.168.122.1;
        };

        allow-query{any;};
        auth-nxdomain no;
        listen-on-v6 { any; };
}; ' > /etc/bind/named.conf.options
```

#### DHCP Server
Setelah menyelesaikan konfigurasi DNS Server, kami akan beralih ke konfigurasi yang diperlukan pada DHCP Server sebagai langkah selanjutnya.
```bash
apt-get update
apt-get install isc-dhcp-server -y

service isc-dhcp-server start

echo '
INTERFACESv4="eth0"
' > /etc/default/isc-dhcp-server

echo '
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

ddns-update-style none;

subnet 10.31.14.128 netmask 255.255.255.252 {
}

subnet 10.31.14.132 netmask 255.255.255.252 {
}

subnet 10.31.14.136 netmask 255.255.255.252 {
}

subnet 10.31.14.140 netmask 255.255.255.252 {
}

subnet 10.31.14.144 netmask 255.255.255.252 {
}

subnet 10.31.14.148 netmask 255.255.255.252 {
}

subnet 10.31.14.0 netmask 255.255.255.128 {
    range 10.31.14.4 10.31.14.67;
    option routers 10.31.14.1;
    option broadcast-address 10.31.14.127;
    option domain-name-servers 10.31.14.146;
    default-lease-time 720;
    max-lease-time 5760;
}

subnet 10.31.12.0 netmask 255.255.254.0 {
    range 10.31.12.2 10.31.13.1;
    option routers 10.31.12.1;
    option broadcast-address 10.31.13.255;
    option domain-name-servers 10.31.14.146;
    default-lease-time 720;
    max-lease-time 5760;
}

subnet 10.31.0.0 netmask 255.255.248.0 {
    range 10.31.0.2 10.31.4.4;
    option routers 10.31.0.1;
    option broadcast-address 10.31.7.255;
    option domain-name-servers 10.31.14.146;
    default-lease-time 720;
    max-lease-time 5760;
}

subnet 10.31.8.0 netmask 255.255.252.0 {
    range 10.31.8.3 10.31.10.5;
    option routers 10.31.8.1;
    option broadcast-address 10.31.11.255;
    option domain-name-servers 10.31.14.146;
    default-lease-time 720;
    max-lease-time 5760;
} ' > /etc/dhcp/dhcpd.conf

service isc-dhcp-server restart
```
#### DHCP Relay

DHCP Relay diaktifkan pada router `Heiter` dan `Himmel`. Heiter berlokasi dekat dengan klien `TurkRegion` dan `GrobeForest`, sementara `Himmel` berdekatan dengan `LaubHills` dan SchwerMountain. Pengaturannya adalah sebagai berikut:
```bash
apt-get update
apt-get install isc-dhcp-relay -y

echo '
SERVERS="10.31.14.150"
INTERFACES="eth0 eth1 eth2"
OPTIONS="-m replace"
' >  /etc/default/isc-dhcp-relay

echo '
net.ipv4.ip_forward=1
' >  /etc/sysctl.conf

service isc-dhcp-relay start
```

#### Web Server
Di server web kami akan menggunakan Apache2 dan akan dikonfigurasi untuk router `Sein` dan `Stark` sesuai dengan instruksi berikut.
```bash
apt update
apt install netcat -y
apt install apache2 -y
service apache2 start

echo '# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default.conf

Listen 80
Listen 443

<IfModule ssl_module>
        Listen 443
</IfModule>

<IfModule mod_gnutls.c>
        Listen 443
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet' > /etc/apache2/ports.conf
```

#### Client
```bash
apt update
apt install netcat -y
apt install lynx -y
```

### Soal 1
### Soal 2
### Soal 3
### Soal 4
### Soal 5
### Soal 6
### Soal 7
### Soal 8
### Soal 9
### Soal 10
