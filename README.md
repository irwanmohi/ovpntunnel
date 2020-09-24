# openvpn tunnel + squid

## server vps tested [debian9]

### install openvpn
```wget https://git.io/vpn -O openvpn.sh && chmod +x openvpn.sh```
#### command untuk install dan membuat config ovpn
```./openvpn.sh```

### forward inet

```nano /etc/sysctl.conf```

edit ```#net.ipv4.ip_forward=1``` menjadi ```net.ipv4.ip_forward=1```

simpan ```ctrl+x``` ```y``` ```enter```

reboot server

### tambahan squid proxy
https://github.com/serverok/squid-proxy-installer


### penjelasan openvpn
Secara default config aka digenerate di ```/root/client.ovpn```

untuk mendapatkannya kita bisa menggunakan simple http server dari python

```
cd /root
python -m SimpleHTTPServer 8000
```

kemudian buka di browser http://ip-vps:8000/configname.ovpn

---

## client

```shell
wget -O /usr/bin/ovpnmon https://raw.githubusercontent.com/laksa19/openvpn/master/client/ovpnmon && chmod +x /usr/bin/ovpnmon

wget -O /usr/bin/ovpn https://raw.githubusercontent.com/laksa19/openvpn/master/client/ovpn && chmod +x /usr/bin/ovpnmon

```
### penggunaan tested [openWrt]

### install openvpn di openWrt

https://rureka.com/cara-install-openvpn-di-openwrt/

edit **ovpnmon** dan **ovpn**

```
nano /usr/bin/ovpnmon
nano /usr/bin/ovpn
```
edit satu per satu

ganti bagian ```config=/root/client.ovpn``` dengan lokasi config Anda

simpan ```ctrl+x``` ```y``` ```enter```

### vpnmon startup

```nano /etc/rc.local```

tambahkan baris berikut

```/usr/bin/ovpnmon```

simpan ```ctrl+x``` ```y``` ```enter```

reboot openWrt

### ganti CUSTOM-HEADER Host

```ovpn yt``` atau ```ovpn ig```

### contoh config proxy ovpn
cek di file config-proxy-ovpn.md

