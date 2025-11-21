# havefun

## Soal 1

> Lakukan subnetting pada topologi diatas menggunakan metode VLSM: [Referensi](https://github.com/arsitektur-jaringan-komputer/Modul-Jarkom/tree/master/Modul-4/Subnetting#2-vlsm-variable-length-subnet-masking)  
*Cantumkan juga tabel dan diagram pembagian subnet pada laporan praktikum*.


> _Subnet the topology above using the VLSM method: [Reference](https://github.com/arsitektur-jaringan-komputer/Modul-Jarkom/tree/master/Modul-4/Subnetting#2-vlsm-variable-length-subnet-masking)_  
_Also include the subnet table and diagram in the lab report._

**Answer:**

- Screenshot

  - Topologi dengan Subnetting
    <img width="2352" height="1342" alt="A1" src="https://github.com/user-attachments/assets/847df569-0f82-44f4-b129-568a3b75353a" />

  - Tabel Subnet

    <img width="654" height="1064" alt="Screenshot 2025-11-21 at 10 05 29" src="https://github.com/user-attachments/assets/dc0485cf-f833-4caf-85c7-b608ba649119" />

    - A1  : `IT-PC-1` + `IT-PC-2` + `IT-PC-3` = 50 + 25 + 40 = 115
    - A2  : `router-1 eth1` + `router-2 eth0` = 1 + 1 = 2
    - A3  : `router-2 eth2` + `router-3 eth0` = 1 + 1 = 2
    - A4  : `DB-Server-1` = 12
    - A5  : `DB-Server-2` = 18
    - A6  : `router-2 eth1` + `router-4 eth0` = 1 + 1 = 2
    - A7  : `router-4 eth3` + `router-5 eth0` = 1 + 1 = 2
    - A8  : `HR-PC-1` + `HR-PC-2` = 250 + 200 = 450
    - A9  : `Web-Server-1` = 25
    - A10 : `Web-Server-2` = 20

  - Diagram Subnet
    <img width="1390" height="1388" alt="Screenshot 2025-11-21 at 10 16 10" src="https://github.com/user-attachments/assets/e73747ef-dd42-407d-a1e5-5f8d2efb4b03" />

- Code
  - Node `router-1`
    ```sh
    auto eth0
    iface eth0 inet static
    	address 10.26.0.129
    	netmask 255.255.255.128
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf

    auto eth1
    iface eth1 inet static
    	address 10.26.0.2
    	netmask 255.255.255.252
    	gateway 10.26.0.1
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf
    ```
    
  - Node `router-2`
    ```sh
    auto eth0
    iface eth0 inet static
    	address 10.26.0.1
    	netmask 255.255.255.252
    	up echo nameserver 192.168.1.1 > /etc/resolv.conf

    auto eth1
    iface eth1 inet static
    	address 10.26.0.9
    	netmask 255.255.255.252
    	up echo nameserver 192.168.1.1 > /etc/resolv.conf

    auto eth2
    iface eth2 inet static
    	address 10.26.0.5
    	netmask 255.255.255.252
    	up echo nameserver 192.168.1.1 > /etc/resolv.conf
    ```
    
  - Node `router-3`
    ```sh
    auto eth0
    iface eth0 inet static
    	address 10.26.0.6
    	netmask 255.255.255.252
    	gateway 10.26.0.5
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf

    auto eth1
    iface eth1 inet static
    	address 10.26.0.17
    	netmask 255.255.255.240
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf

    auto eth2
    iface eth2 inet static
    	address 10.26.0.33
    	netmask 255.255.255.224
    	gateway 192.168.2.1
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf
    ```
    
  - Node `router-4`
    ```sh
    auto eth0
    iface eth0 inet static
    	address 10.26.0.10
    	netmask 255.255.255.252
    	gateway 10.26.0.9
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf

    auto eth1
    iface eth1 inet static
    	address 10.26.0.65
    	netmask 255.255.255.224
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf

    auto eth2
    iface eth2 inet static
    	address 10.26.0.97
    	netmask 255.255.255.224
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf

    auto eth3
    iface eth3 inet static
    	address 10.26.0.13
    	netmask 255.255.255.252
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf
    ```
  - Node `router-5`
    ```sh
    auto eth0
    iface eth0 inet static
    	address 10.26.0.14
    	netmask 255.255.255.252
      gateway 10.26.0.13
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf

    auto eth1
    iface eth1 inet static
    	address 10.26.2.1
    	netmask 255.255.254.0
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf
    ```
  - Node `IT-PC-1`
    ```sh
    auto eth0
    iface eth0 inet static
    	address 10.26.0.130
    	netmask 255.255.255.128
    	gateway 10.26.0.129
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf
    ```
  - Node `IT-PC-2`
    ```sh
    auto eth0
    iface eth0 inet static
    	address 10.26.0.131
    	netmask 255.255.255.128
    	gateway 10.26.0.129
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf
    ```
  - Node `IT-PC-3`
    ```sh
    auto eth0
    iface eth0 inet static
    	address 10.26.0.132
    	netmask 255.255.255.128
    	gateway 10.26.0.129
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf
    ```
  - Node `DB-Server-1`
    ```sh
    auto eth0
    iface eth0 inet static
    	address 10.26.0.18
    	netmask 255.255.255.240
    	gateway 10.26.0.17
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf
    ```
  - Node `DB-Server-2`
    ```sh
    auto eth0
    iface eth0 inet static
    	address 10.26.0.34
    	netmask 255.255.255.224
    	gateway 10.26.0.33
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf
    ```
  - Node `Web-Server-1`
    ```sh
    auto eth0
    iface eth0 inet static
    	address 10.26.0.66
    	netmask 255.255.255.224
    	gateway  10.26.0.65
    	up echo nameserver 192.168.0.1 > /etc/resolv.conf
    ```
  - Node `Web-Server-2`
    ```sh
    auto eth0
    iface eth0 inet static
    	address 10.26.0.98
    	netmask 255.255.255.224
    	gateway 10.26.0.97
    	up echo nameserver 192.168.1.1 > /etc/resolv.conf
    ```
  - Node `HR-PC-1`
    ```sh
    auto eth0
    iface eth0 inet static
    	address 10.26.2.2
    	netmask 255.255.254.0
    	gateway 10.26.2.1
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf
    ```
  - Node `HR-PC-2`
    ```sh
    auto eth0
    iface eth0 inet static
    	address 10.26.2.3
    	netmask 255.255.254.0
    	gateway 10.26.2.1
    	up echo nameserver 192.168.122.1 > /etc/resolv.conf
    ```

- Explanation

  `Put your explanation in here`

<br>

## Soal 2

> Buatlah agar router-2 dapat melakukan koneksi ke internet. [Dapat menggunakan static routing].

> _Make sure router-2 can connect to the internet. [Can use static routing]._

**Answer:**

- Screenshot
  <img width="1104" height="738" alt="Screenshot 2025-11-21 at 10 47 49" src="https://github.com/user-attachments/assets/85b9a57a-d096-440c-a4e2-7c47228f691e" />

- Code

  - Tambahkan bagian ini pada konfigurasi _network_ `router-2` dan _restart_ node tersebut.
    ```sh
    auto eth3
    iface eth3 inet dhcp
    ```

- Explanation

  `Put your explanation in here`

<br>

## Soal 3

> Setelah mengimplementasi subnetting, buatlah agar seluruh topologi dapat terhubung. Lakukan Dynamic Routing pada topologi tersebut.
*Pastikan seluruh node yang ada dapat mengakses internet*.

> _After implementing subnetting, ensure the entire topology is connected. Perform dynamic routing on the topology._  
_Ensure all existing nodes can access the internet._

**Answer:**

- Screenshot

  - Node `HR-PC-1` mengakses internet
    <img width="1098" height="732" alt="Screenshot 2025-11-21 at 10 54 32" src="https://github.com/user-attachments/assets/2a6765a3-363b-478d-8e7a-8e9b929e083d" />

  - Node `HR-PC-2` mengakses internet
    <img width="1098" height="738" alt="Screenshot 2025-11-21 at 10 55 01" src="https://github.com/user-attachments/assets/1c220f0e-4f52-4e68-becd-163b7a513fd5" />

  - Node `Web-Server-1` mengakses internet
    <img width="1094" height="732" alt="Screenshot 2025-11-21 at 10 55 45" src="https://github.com/user-attachments/assets/93bef3bb-167f-4d14-b525-3081118c7a91" />
    
  - Node `Web-Server-2` mengakses internet
    <img width="1096" height="740" alt="Screenshot 2025-11-21 at 10 56 09" src="https://github.com/user-attachments/assets/2f68cecd-ec09-44ab-8912-871e0e64324e" />

  - Node `DB-Server-1` mengakses internet
    <img width="1094" height="732" alt="Screenshot 2025-11-21 at 10 56 53" src="https://github.com/user-attachments/assets/4de8548b-c194-4dcc-96de-41e9e2eeaf30" />

  - Node `DB-Server-2` mengakses internet
    <img width="1100" height="736" alt="Screenshot 2025-11-21 at 10 56 34" src="https://github.com/user-attachments/assets/2cda4340-9804-4498-8b6c-ca3919b112f9" />

  - Node `IT-PC-1` mengakses internet
    <img width="1094" height="736" alt="Screenshot 2025-11-21 at 10 57 21" src="https://github.com/user-attachments/assets/71e1844e-9ada-4175-ba9c-43e26dd2352a" />

  - Node `IT-PC-2` mengakses internet
    <img width="1092" height="734" alt="Screenshot 2025-11-21 at 10 57 44" src="https://github.com/user-attachments/assets/5dc5c783-b18a-466a-aa03-59c521d7e240" />

  - Node `IT-PC-3` mengakses internet
    <img width="1094" height="730" alt="Screenshot 2025-11-21 at 10 58 19" src="https://github.com/user-attachments/assets/c31b36dc-6a56-4192-8155-d7451e228509" />

- Code (Dynamic Routing)

  - Lakukan pada semua `router`
    ```sh
    cd /usr/lib/frr
    
    ./zebra -d
    ./ripd -d
    ./mgmtd -d

    vtysh

    conf t
    router rip
    ```

  - Pada node `router-1`
    ```sh
    network 10.26.0.128/25
    network 10.26.0.0/30
    ```
  - Pada node `router-2`
    ```sh
    network 10.26.0.0/30
    network 10.26.0.4/30
    network 10.26.0.8/30
    ```
  - Pada node `router-3`
    ```sh
    network 10.26.0.4/30
    network 10.26.0.16/28
    network 10.26.0.32/27
    ```
  - Pada node `router-4`
    ```sh
    network 10.26.0.8/30
    network 10.26.0.12/30
    network 10.26.0.64/27
    network 10.26.0.96/27
    ```
  - Pada node `router-5`
    ```sh
    network 10.26.0.12/30
    network 10.26.2.0/23
    ```

- Code (`iptables`)

  - Lakukan pada semua `router` ketika bisa mengakses internet
    ```sh
    apt-get update
    apt-get install iptables -y
    ```

   - Pada node `router-2`
     ```sh
     iptables -t nat -A POSTROUTING -o eth3 -j MASQUERADE -s 10.26.0.0/16
     ```
   - Pada node `router-1`
     ```sh
     iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE -s 10.26.0.0/16
     ```
   - Pada node `router-3`
     ```sh
     iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.26.0.0/16
     ```
   - Pada node `router-4`
     ```sh
     iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.26.0.0/16
     ```
   - Pada node `router-5`
     ```sh
     iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.26.0.0/16
     ```

- Explanation

  `Put your explanation in here`

<br>
