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
