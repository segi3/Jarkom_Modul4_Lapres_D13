## Praktikum Modul 4
Kelompok D13
- 05111840000094 Rafi Nizar Abiyyi
- 05111740000192 Faishal Abiyyudzakir

<br>

## Subnetting CIDR

Menentukan subnet dalam topologi

### Topologi CIDR

Subnet A:

![](/imgs/topo-vlsm.PNG)

SUBNET | JUMLAH IP | NETMASK
--- | --- | ---
A1 | 2 | 30
A2 | 502 | 23
A3 | 13 | 28
A4 | 521 | 22
A5 | 2 | 30
A6 | 721 | 22
A7 | 1001 | 22
A8 | 2 | 30
A9 | 701 | 22
A10 | 2 | 30
A11 | 2021 | 21
A12 | 101 | 25
A13 | 2 | 30
A14 | 2 | 30
A15 | 252 | 24

<br>

Subnet B:

![](/imgs/b.png)

SUBNET | NETMASK | ANGGOTA
--- | --- | ---
B1 | 21 | A6, A15
B2 | 20 | A11, A12
B3 | 22 | A2, A3

<br>

Subnet C:

![](/imgs/c.png)

SUBNET | NETMASK | ANGGOTA
--- | --- | ---
C1 | 21 | B3, A4
C2 | 20 | B1, A14
C3 | 19 | B2, A10

<br>

Subnet D:

![](/imgs/d.png)

SUBNET | NETMASK | ANGGOTA
--- | --- | ---
D1 | 19 | C1, C2
D2 | 18 | C3, A9

<br>

Subnet E:

![](/imgs/e.png)

SUBNET | NETMASK | ANGGOTA
--- | --- | ---
E1 | 18 | D1, A13
E2 | 17 | D2, A8

<br>

Subnet F:

![](/imgs/f.png)

SUBNET | NETMASK | ANGGOTA
--- | --- | ---
F1 | 17 | E1, A7

<br>

Subnet G:

![](/imgs/g.png)

SUBNET | NETMASK | ANGGOTA
--- | --- | ---
G1 | 16 | F1, E2

![](/imgs/topo-cidr.png)

Hasil akhir membutuhkan subnetmask /16 untuk menampung semua subnet

### Tree CIDR

![](/imgs/tree-cidr.PNG)

![](/imgs/tree-cidr-server.PNG)

## Hasil subnetting

![](/imgs/hasil-cidr-1.PNG)
![](/imgs/hasil-cidr-2.PNG)

## Topologi UML

Switch
```bash
# Switch
uml_switch -unix switch1 > /dev/null < /dev/null &
uml_switch -unix switch2 > /dev/null < /dev/null &
uml_switch -unix switch3 > /dev/null < /dev/null &
uml_switch -unix switch4 > /dev/null < /dev/null &
uml_switch -unix switch5 > /dev/null < /dev/null &
uml_switch -unix switch13 > /dev/null < /dev/null &
uml_switch -unix switch15 > /dev/null < /dev/null &
uml_switch -unix switch16 > /dev/null < /dev/null &
uml_switch -unix switch17 > /dev/null < /dev/null &
uml_switch -unix switch18 > /dev/null < /dev/null &
uml_switch -unix switch20 > /dev/null < /dev/null &
uml_switch -unix switch19 > /dev/null < /dev/null &
uml_switch -unix switch21 > /dev/null < /dev/null &
uml_switch -unix switch22 > /dev/null < /dev/null &
uml_switch -unix switch25 > /dev/null < /dev/null &
```
Router
```bash
# Router
# NID TUNTAP 10.151.78.56/30    10.151.79.112/29
xterm -T SURABAYA -e linux ubd0=SURABAYA,jarkom umid=SURABAYA eth0=tuntap,,,10.151.78.57 eth1=daemon,,,switch1 eth2=daemon,,,switch2 eth3=daemon,,,switch3 eth4=daemon,,,switch13 mem=64M &
xterm -T PASURUAN -e linux ubd0=PASURUAN,jarkom umid=PASURUAN eth0=daemon,,,switch4 eth1=daemon,,,switch19 eth2=daemon,,,switch2 mem=64M &
xterm -T PROBOLINGGO -e linux ubd0=PROBOLINGGO,jarkom umid=PROBOLINGGO eth0=daemon,,,switch15 eth1=daemon,,,switch16 eth2=daemon,,,switch4 mem=64M &
xterm -T BATU -e linux ubd0=BATU,jarkom umid=BATU eth0=daemon,,,switch3 eth1=daemon,,,switch5 eth2=daemon,,,switch21 eth3=daemon,,,switch22 mem=64M &
xterm -T MADIUN -e linux ubd0=MADIUN,jarkom umid=MADIUN eth0=daemon,,,switch22 eth1=daemon,,,switch25 mem=64M &
xterm -T KEDIRI -e linux ubd0=KEDIRI,jarkom umid=KEDIRI eth0=daemon,,,switch5 eth1=daemon,,,switch17 eth2=daemon,,,switch18 mem=64M &
xterm -T BLITAR -e linux ubd0=BLITAR,jarkom umid=BLITAR eth0=daemon,,,switch17 eth1=daemon,,,switch20 mem=64M &
```
Server
```bash
# Server
xterm -T MALANG -e linux ubd0=MALANG,jarkom umid=MALANG eth0=daemon,,,switch18 mem=64M &
xterm -T MOJOKERTO -e linux ubd0=MOJOKERTO,jarkom umid=MOJOKERTO eth0=daemon,,,switch13 mem=64M &
```
Klien
```bash
# Klien 
xterm -T SAMPANG -e linux ubd0=SAMPANG,jarkom umid=SAMPANG eth0=daemon,,,switch1 mem=64M &
xterm -T SIDOARJO -e linux ubd0=SIDOARJO,jarkom umid=SIDOARJO eth0=daemon,,,switch19 mem=64M &
xterm -T BANYUWANGI -e linux ubd0=BANYUWANGI,jarkom umid=BANYUWANGI eth0=daemon,,,switch16 mem=64M &
xterm -T JEMBER -e linux ubd0=JEMBER,jarkom umid=JEMBER eth0=daemon,,,switch16 mem=64M &
xterm -T BONDOWOSO -e linux ubd0=BONDOWOSO,jarkom umid=BONDOWOSO eth0=daemon,,,switch15 mem=64M &
xterm -T JOMBANG -e linux ubd0=JOMBANG,jarkom umid=JOMBANG eth0=daemon,,,switch22 mem=64M &
xterm -T BOJONEGORO -e linux ubd0=BOJONEGORO,jarkom umid=BOJONEGORO eth0=daemon,,,switch25 mem=64M &
xterm -T NGANJUK -e linux ubd0=NGANJUK,jarkom umid=NGANJUK eth0=daemon,,,switch21 mem=64M &
xterm -T LUMAJANG -e linux ubd0=LUMAJANG,jarkom umid=LUMAJANG eth0=daemon,,,switch17 mem=64M &
xterm -T TULUNGAGUNG -e linux ubd0=TULUNGAGUNG,jarkom umid=TULUNGAGUNG eth0=daemon,,,switch20 mem=64M &
```

### Interface UML

Malang: Server
```c
// switch 18
auto eth0
iface eth0 inet static
address 10.151.79.118
netmask 255.255.255.252
gateway 10.151.79.117
```

Mojokerto: Server
```c
// switch 13
auto eth0
iface eth0 inet static
address 10.151.79.114
netmask 255.255.255.252
gateway 10.151.79.113
```

Surabaya: Router
```c
// internet
auto eth0
iface eth0 inet static
address 10.151.78.58
netmask 255.255.255.252
gateway 10.151.78.57

// switch 1
auto eth1
iface eth1 inet static
address 192.168.64.1
netmask 255.255.252.0

// switch 2
auto eth2
iface eth2 inet static
address 192.168.192.1
netmask 255.255.255.252

// switch 3
auto eth3
iface eth3 inet static
address 192.168.32.1
netmask 255.255.255.252

// switch 13 (server)
auto eth4
iface eth4 inet static
address 10.151.79.113
netmask 255.255.255.252

```

Batu: Router
```c
// switch 3
auto eth0
iface eth0 inet static
address 192.168.32.2
netmask 255.255.255.252

// switch 5
auto eth1
iface eth1 inet static
address 192.168.8.1
netmask 255.255.255.252

// switch 21
auto eth2
iface eth2 inet static
address 192.168.20.1
netmask 255.255.252.0

// switch 22
auto eth3
iface eth3 inet static
address 192.168.18.1
netmask 255.255.254.0
```

Blitar: Router
```c
// switch 17
auto eth0
iface eth0 inet static
address 192.168.4.2
netmask 255.255.255.0

// switch 20
auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.252.0
```

Kediri: Router
```c
/// switch 5
auto eth0
iface eth0 inet static
address 192.168.8.2
netmask 255.255.255.252

// switch 17
auto eth1
iface eth1 inet static
address 192.168.4.1
netmask 255.255.255.0

// switch 18 (server)
auto eth2
iface eth2 inet static
address 10.151.79.117
netmask 255.255.255.252
```

Madiun: Router
```c
// switch 22
auto eth0
iface eth0 inet static
address 192.168.18.2
netmask 255.255.254.0

// switch 25
auto eth1
iface eth1 inet static
address 192.168.16.1
netmask 255.255.255.240
```

Pasuruan: Router
```c
// switch 4
auto eth0
iface eth0 inet static
address 192.168.144.1
netmask 255.255.255.252

// switch 19
auto eth1
iface eth1 inet static
address 192.168.160.1
netmask 255.255.252.0

// switch 2
auto eth2
iface eth2 inet static
address 192.168.192.2
netmask 255.255.255.252
```

Probolinggo: Router
```c
// switch 15
auto eth0
iface eth0 inet static
address 192.168.136.1
netmask 255.255.255.128

// switch 16
auto eth1
iface eth1 inet static
address 192.168.128.1
netmask 255.255.248.0

// switch 4
auto eth2
iface eth2 inet static
address 192.168.144.2
netmask 255.255.255.252
```

Banyuwangi: Klien
```c
// switch 16
auto eth0
iface eth0 inet static
address 192.168.128.2
netmask 255.255.248.0
gateway 192.168.128.1
```

Bojonegoro: Klien
```c
// switch 25
auto eth0
iface eth0 inet static
address 192.168.16.2
netmask 255.255.255.240
gateway 192.168.16.1
```

Bondowoso: Klien
```c
// switch 15
auto eth0
iface eth0 inet static
address 192.168.136.2
netmask 255.255.255.128
gateway 192.168.136.1
```

Jember: Klien
```c
// switch 16
auto eth0
iface eth0 inet static
address 192.168.128.3
netmask 255.255.248.0
gateway 192.168.128.1
```

Jombang: Klien
```c
// switch 22
auto eth0
iface eth0 inet static
address 192.168.18.3
netmask 255.255.254.0
gateway 192.168.18.1
```

Lumajang: Klien
```c
// switch 17
auto eth0
iface eth0 inet static
address 192.168.4.3
netmask 255.255.255.0
gateway 192.168.4.1
```

Nganjuk: Klien
```c
// switch 21
auto eth0
iface eth0 inet static
address 192.168.20.2
netmask 255.255.252.0
gateway 192.168.20.1
```

Sampang: Klien
```c
// switch 1
auto eth0
iface eth0 inet static
address 192.168.64.2
netmask 255.255.252.0
gateway 192.168.64.1
```

Sidoarjo: Klien
```c
// switch 19
auto eth0
iface eth0 inet static
address 192.168.160.2
netmask 255.255.252.0
gateway 192.168.160.1
```

Sidoarjo: Klien
```c
// switch 20
auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.252.0
gateway 192.168.0.1
```

### Routing

Routing di Surabaya
```c
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.32.1                  // SBY
route add -net 192.168.16.0 netmask 255.255.255.240 gw 192.168.18.2     // A3
route add -net 192.168.0.0 netmask 255.255.248.0 gw 192.168.8.2         // B1
route add -net 10.151.79.116 netmask 255.255.255.252 gw 192.168.8.2     // server
```

Routing di Blitar
```c
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.4.1 // SBY
```

Routing di Kediri
```c
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.8.1               // SBY
route add -net 192.168.0.0 netmask 255.255.252.0 gw 192.168.4.2     // A6
```

Routing di Madiun
```c
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.18.1 // SBY
```

Routing di Pasuruan
```c
route add -net 192.168.128.0 netmask 255.255.240.0 gw 192.168.144.2 // B2
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.192.1             // SBY
```

Routing di Probolinggo
```c
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.144.1 // surabaya
```

Routing di Surabaya
```c
route add -net 192.168.128.0 netmask 255.255.128.0 gw 192.168.192.2  // E2
route add -net 192.168.0.0 netmask 255.255.224.0 gw 192.168.32.2     // D1
route add -net 10.151.79.116 netmask 255.255.255.252 gw 192.168.32.2 //server malang
```


<br>

## Subnetting VLSM

Menentukan subnet dalam topologi

### Topologi VLSM

![](/imgs/topo-vlsm.PNG)

Hasil subnetting

SUBNET | JUMLAH IP | NETMASK
--- | --- | ---
A1 | 2 | 30
A2 | 502 | 23
A3 | 13 | 28
A4 | 521 | 22
A5 | 2 | 30
A6 | 721 | 22
A7 | 1001 | 22
A8 | 2 | 30
A9 | 701 | 22
A10 | 2 | 30
A11 | 2021 | 21
A12 | 101 | 25
A13 | 2 | 30
A14 | 2 | 30
A15 | 252 | 24
total | 5845 | 

Kebutuhan total adalah 5845 IP maka menggunakan subnet /19

### Tree VLSM

![](/imgs/tree-vlsm.png)

Leaf yang digaris bawahi berwarna merah adalah subnet yang tidak terpakai.

### Hasil subnetting

![](/imgs/hasil-vlsm-1.PNG)
![](/imgs/hasil-vlsm-2.PNG)