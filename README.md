# Tugas1-Jarkom-Maritza-Adelia-111

## Membuat Topologi dengan CPT

![topologi](assets/topologi.jpg)

Karena jaringan butuh 7 interface, tambah module PT-ROUTER-NM-1CGE
```
klik router -> physical -> matikan router -> tambahkan PT-ROUTER-NM-1CGE -> nyalakan router
```
![module](assets/module.jpg)


di CLI HQ tambahkan IP Address:
```bash
enable
conf t
```

```bash
interface g0/0
 ip address 10.151.0.1 255.255.254.0
 no shut
exit

interface g1/0
 ip address 10.151.2.1 255.255.255.0
 no shut
exit

interface g2/0
 ip address 10.151.3.1 255.255.255.128
 no shut
exit

interface g3/0
 ip address 10.151.3.129 255.255.255.192
 no shut
exit

interface g4/0
 ip address 10.151.3.193 255.255.255.224
 no shut
exit

interface g5/0
 ip address 10.151.3.225 255.255.255.240
 no shut
exit

interface GigabitEthernet6/0
 ip address 10.151.4.17 255.255.255.252
 no shut
exit
ip route 10.151.5.0 255.255.255.224 10.151.4.18
end

```

Di Branch (Gi0/1):
```bash
conf t
interface GigabitEthernet0/1
 ip address 10.151.4.18 255.255.255.252
 no shut
exit
ip route 0.0.0.0 0.0.0.0 10.151.4.17
end
```
Cek dengan:
```bash
show ip interface brief
```
![setip](assets/aftersetip.jpg)

Cek Prefix:

![setpre](assets/setprefix.jpg)

tes koneksi HQ - BR:

di HQ:
```bash
ping 10.151.4.18
```
![pingHQ](assets/pingbr.jpg)

Di BR:
```bash
ping 10.151.4.17
```
![pingBR](assets/pinghq.jpg)
