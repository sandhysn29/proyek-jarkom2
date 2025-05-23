Pengumpulan UTS DHCP, DNS, Firewall | Jaringan Komputer 2 | Universitas Teknologi Bandung
<br>

Kelas: TIF K 23B – Departemen Informatika, Universitas Teknologi Bandung 

Dosen Pengampu: Muchamad Rusdan, S.T., M.T. 

Nama Mahasiswa: Sandhy Safarudin Nurdiansyah (23552011464)

<br>
<br>

a. /etc/dhcp/dhcpd.conf

  subnet 192.168.10.0 netmask 255.255.255.0 {
  
    range 192.168.10.100 192.168.10.200;
    
    option routers 192.168.10.1;
    
    option domain-name-servers 192.168.10.1;
    
    option domain-name "server.local";
  }

  b. /etc/bind/named.conf.local
  
    zone "server.local" {
      type master;
      file "/etc/bind/db.server.local";
    };

    zone "10.168.192.in-addpr.arpa" {
      type master;
      file "/etc/bind/db.192";
    };

  c. Script Firewall (iptables)
  
    sudo iptables -F
    sudo iptables -P INPUT DROP
    sudo iptables -A INPUT -s 192.168.56.0/24 -p icmp -j ACCEPT
    sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
    sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
    sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT
    sudo iptables -A INPUT -m state ESTABLISHED,RELATED -j ACCEPT

  d. Link Video Youtube: <a href="https://youtu.be/ZePag7utyRg">Klik di sini</a>
