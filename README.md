# Jarkom_Modul4_Lapres_B10




## UML

### Topologi.sh
    # Switch
    uml_switch -unix switch1 > /dev/null < /dev/null &  #   R SURABAYA  P SAMPANG (1000)
    uml_switch -unix switch2 > /dev/null < /dev/null &  #   R SURABAYA  R PASURUAN
    uml_switch -unix switch3 > /dev/null < /dev/null &  #   R SURABAYA  R BATU
    uml_switch -unix switch4 > /dev/null < /dev/null &  #   R BATU      R KEDIRI
    uml_switch -unix switch5 > /dev/null < /dev/null &  #   R PASURUAN  R PROBOLINGGO (100)
    uml_switch -unix switch13 > /dev/null < /dev/null & #   R SURABAYA  S MOJOKERTO
    uml_switch -unix switch15 > /dev/null < /dev/null & #   R PROBOLINGGO P BONDOWOSO
    uml_switch -unix switch16 > /dev/null < /dev/null & #   R PROBOLINGGO P JEMBER(1020) P BANYUWANGI (1000)
    uml_switch -unix switch17 > /dev/null < /dev/null & #   R KEDIRI    R BLITAR        P LUMAJANG (250)
    uml_switch -unix switch18 > /dev/null < /dev/null & #   R KEDIRI    S MALANG
    uml_switch -unix switch19 > /dev/null < /dev/null & #   R PASURUAN  P SIDOARJO(700)
    uml_switch -unix switch20 > /dev/null < /dev/null & #   R BLITAR    P TULUNGAGUNG 720
    uml_switch -unix switch21 > /dev/null < /dev/null & #   R BATU      P NGANJUK 520
    uml_switch -unix switch22 > /dev/null < /dev/null & #   R BATU      P JOMBANG 500   R MADIUN
    uml_switch -unix switch25 > /dev/null < /dev/null & #   R MADIUN    P BOJONEGORO 12

    # Router
    xterm -T SURABAYA -e linux ubd0=SURABAYA,jarkom umid=SURABAYA eth0=tuntap,,,10.151.74.45 eth1=daemon,,,switch1 eth2=daemon,,,switch2 eth3=daemon,,,switch3 eth4=daemon,,,switch13  mem=64M &
    xterm -T PASURUAN -e linux ubd0=PASURUAN,jarkom umid=PASURUAN eth0=daemon,,,switch2 eth1=daemon,,,switch5 eth2=daemon,,,switch19 mem=64M &
    xterm -T PROBOLINGGO -e linux ubd0=PROBOLINGGO,jarkom umid=PROBOLINGGO eth0=daemon,,,switch5 eth1=daemon,,,switch15 eth2=daemon,,,switch16 mem=64M &
    xterm -T BATU -e linux ubd0=BATU,jarkom umid=BATU eth0=daemon,,,switch3 eth1=daemon,,,switch4 eth2=daemon,,,switch21 eth3=daemon,,,switch22 mem=64M &   
    xterm -T MADIUN -e linux ubd0=MADIUN,jarkom umid=MADIUN eth0=daemon,,,switch22 eth1=daemon,,,switch25 mem=64M &
    xterm -T KEDIRI -e linux ubd0=KEDIRI,jarkom umid=KEDIRI eth0=daemon,,,switch4 eth1=daemon,,,switch17 eth2=daemon,,,switch18 mem=64M &
    xterm -T BLITAR -e linux ubd0=BLITAR,jarkom umid=BLITAR eth0=daemon,,,switch17 eth1=daemon,,,switch20 mem=64M &

    # Server
    xterm -T MOJOKERTO -e linux ubd0=MOJOKERTO,jarkom umid=MOJOKERTO  eth0=daemon,,,switch13   mem=64M &
    xterm -T MALANG -e linux ubd0=MALANG,jarkom umid=MALANG eth0=daemon,,,switch18 mem=64M &   

    # Klien 
    xterm -T SAMPANG -e linux ubd0=SAMPANG,jarkom umid=SAMPANG eth0=daemon,,,switch1 mem=64M &
    xterm -T BONDOWOSO -e linux ubd0=BONDOWOSO,jarkom umid=BONDOWOSO eth0=daemon,,,switch15 mem=64M &
    xterm -T JEMBER -e linux ubd0=JEMBER,jarkom umid=JEMBER eth0=daemon,,,switch16 mem=64M &
    xterm -T BANYUWANGI -e linux ubd0=BANYUWANGI,jarkom umid=BANYUWANGI eth0=daemon,,,switch16 mem=64M &
    xterm -T SIDOARJO -e linux ubd0=SIDOARJO,jarkom umid=SIDOARJO eth0=daemon,,,switch19 mem=64M &
    xterm -T LUMAJANG -e linux ubd0=LUMAJANG,jarkom umid=LUMAJANG eth0=daemon,,,switch17 mem=64M &
    xterm -T TULUNGAGUNG -e linux ubd0=TULUNGAGUNG,jarkom umid=TULUNGAGUNG eth0=daemon,,,switch20 mem=64M &
    xterm -T NGANJUK -e linux ubd0=NGANJUK,jarkom umid=NGANJUK eth0=daemon,,,switch21 mem=64M &
    xterm -T BOJONEGORO -e linux ubd0=BOJONEGORO,jarkom umid=BOJONEGORO eth0=daemon,,,switch25 mem=64M &
    xterm -T JOMBANG -e linux ubd0=JOMBANG,jarkom umid=JOMBANG eth0=daemon,,,switch22 mem=64M &

### Subneting Tree

![](.//img/TREECIDR.png)

192.168.0.0 / 16 H
    192.168.0.0 / 17 G
        192.168.64.0 / 22 A10 
        192.168.0.0 / 18 F1
            192.168.32.0 / 30 A8
            192.168.0.0 / 19 E1 
                192.168.16.0 / 21 D1 
                    192.168.20.0 / 22 A5
                    192.168.16.0 / 22 C2
                        192.168.16.16 / 23 A7
                        192.168.16.0 / 28 A6
                192.168.0.0 / 20 C1
                    192.168.8.0 / 30 A4
                    192.168.0.0 / 21 B1
                        192.168.1.0 / 22 A2
                        192.168.0.0 / 24 A1
    192.168.128.0 / 17 F2
        192.168.192.0 / 30 A15 
        192.168.128.0 / 18 E2 
            192.168.160.0 / 22 A14
            192.168.128.0 / 19 D2
                192.168.144.0 / 30 A13
                192.168.128.0 / 20 C3
                    192.168.136.0 / 25 A12
                    192.168.128.0 / 21 A11
### interface
```
Router 
    SURABAYA
        auto eth0
        iface eth0 inet static
        address 10.151.74.46
        netmask 255.255.255.252
        gateway 10.151.74.45

        auto eth1
        iface eth1 inet static
        address 192.168.64.1
        netmask 255.255.252.0

        auto eth2
        iface eth2 inet static
        address 192.168.192.1
        netmask 255.255.255.252

        auto eth3
        iface eth3 inet static
        address 192.168.32.1
        netmask 255.255.255.252

        auto eth4
        iface eth4 inet static
        address 10.151.83.89
        netmask 255.255.255.248
    PASURUAN
        auto eth0
        iface eth0 inet static
        address 192.168.192.2
        netmask 255.255.255.252

        auto eth1
        iface eth1 inet static
        address 192.168.144.1
        netmask 255.255.255.252

        auto eth2
        iface eth2 inet static
        address 192.168.160.1
        netmask 255.255.252.0
    PROBOLINGGO 
        auto eth0
        iface eth0 inet static
        address 192.168.144.2
        netmask 255.255.255.252

        auto eth1
        iface eth1 inet static
        address 192.168.136.1
        netmask 255.255.255.128

        auto eth2
        iface eth2 inet static
        address 192.168.128.1
        netmask 255.255.255.248.0
    BATU
        auto eth0
        iface eth0 inet static
        address 192.168.32.2
        netmask 255.255.255.252

        auto eth1
        iface eth1 inet static
        address 192.168.8.1
        netmask 255.255.255.252

        auto eth2
        iface eth2 inet static
        address 192.168.20.1
        netmask 255.255.252.0

        auto eth3
        iface eth3 inet static
        address 192.168.16.17
        netmask 255.255.254.0
    MADIUN
        auto eth0
        iface eth0 inet static
        address 192.168.16.18
        netmask 255.255.254.0

        auto eth1
        iface eth1 inet static
        address 192.168.16.1
        netmask 255.255.255.240
    KEDIRI
        auto eth0
        iface eth0 inet static
        address 192.168.8.2
        netmask 255.255.255.252

        auto eth1
        iface eth1 inet static
        address 192.168.1.1
        netmask 255.255.252.0

        auto eth2
        iface eth2 inet static
        address 10.151.83.89
        netmask 255.255.255.248
    BLITAR
        auto eth0
        iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.252.0

        auto eth1
        iface eth1 inet static
        address 192.168.0.1
        netmask 255.255.255.0

Server 
    MOJOKERTO
        auto eth0
        iface eth0 inet static
        address 10.151.83.90
        netmask 255.255.255.248
        gateway 10.151.83.89
    MALANG
        auto eth0
        iface eth0 inet static
        address 10.151.83.91
        netmask 255.255.255.248
        gateway 10.151.83.89

Client 
    SAMPANG 
        auto eth0
        iface eth0 inet static
        address 192.168.64.2
        netmask 255.255.252.0
        gateway 192.168.64.1
    BONDOWOSO 
        auto eth0
        iface eth0 inet static
        address 192.168.136.2
        netmask 255.255.255.128
        gateway 192.168.136.1
    JEMBER 
        auto eth0
        iface eth0 inet static
        address 192.168.128.2
        netmask 255.255.248.0
        gateway 192.168.128.1
    BANYUWANGI 
        auto eth0
        iface eth0 inet static
        address 192.168.128.3
        netmask 255.255.248.0
        gateway 192.168.128.1
    SIDOARJO 
        auto eth0
        iface eth0 inet static
        address 192.168.160.2
        netmask 255.255.252.0
        gateway 192.168.160.1
    LUMAJANG 
        auto eth0
        iface eth0 inet static
        address 192.168.1.3
        netmask 255.255.252.0
        gateway 192.168.1.1
    TULUNGAGUNG 
        auto eth0
        iface eth0 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        gateway 192.168.0.1
    NGANJUK 
        auto eth0
        iface eth0 inet static
        address 192.168.20.2
        netmask 255.255.252.0
        gateway 192.168.20.1
    BOJONEGORO 
        auto eth0
        iface eth0 inet static
        address 192.168.16.2
        netmask 255.255.255.240
        gateway 192.168.16.1
    JOMBANG 
        auto eth0
        iface eth0 inet static
        address 192.168.16.18
        netmask 255.255.254.0
        gateway 192.168.16.16

```
### Routing
```
SURABAYA
    PASURUAN
        route add -net 192.168.128.0 netmask 255.255.128.0 gw 192.168.192.2
    BATU
        route add -net 192.168.0.0 netmask 255.255.128.0 gw 192.168.32.2
        route add -net 10.151.83.92 netmask 255.255.255.252 gw 192.168.32.2
PASURUAN
    route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.192.1
    PROBOLINGGO
        route add -net 192.168.128.0 netmask 255.255.192.0 gw 192.168.144.2
PROBOLINGGO
    route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.144.1
BATU
    route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.32.1
    MADIUN
        route add -net 192.168.16.0  netmask 255.255.255.240 gw 192.168.16.18
    KEDIRI
        route add -net 10.151.83.92 netmask 255.255.255.252 gw 192.168.8.2
        route add -net 192.168.0.0 netmask 255.255.240.0 gw 192.168.8.2
MADIUN
    route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.16.17
KEDIRI 
    route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.8.1
    BLITAR
        route add -net 192.168.0.0 netmask 255.255.255.0 gw 192.168.1.1
BLITAR 
    route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.1.2
    
```
