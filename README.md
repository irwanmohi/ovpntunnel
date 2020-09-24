# openvpn tunnel + squid

## server vps tested [debian9]

### install openvpn
```wget https://git.io/vpn -O openvpn.sh && chmod +x openvpn.sh```
#### command untuk install dan membuat config ovpn
```./openvpn.sh```
#### penjelasan
Secara default config aka digenerate di ```/root/client.ovpn```

untuk mendapatkannya kita bisa menggunakan simple http server dari python

```
cd /root
python -m SimpleHTTPServer 8000
```

kemudian buka di browser http://ip-vps:8000/configname.ovpn


### forward inet

```nano /etc/sysctl.conf```

```net.ipv4.ip_forward=1```

### squid proxy
https://github.com/serverok/squid-proxy-installer

reboot server

## client

```shell
wget -O /usr/bin/ovpnmon https://raw.githubusercontent.com/laksa19/openvpn/master/client/ovpnmon && chmod +x /usr/bin/ovpnmon

wget -O /usr/bin/ovpn https://raw.githubusercontent.com/laksa19/openvpn/master/client/ovpn && chmod +x /usr/bin/ovpnmon

```
### penggunaan tested [openWrt]

edit **ovpnmon** dan **ovpn**

```
nano /usr/bin/ovpnmon
nano /usr/bin/ovpn
```
edit satu per satu

ganti bagian ```config=/root/client.ovpn``` dengan lokasi config Anda

### vpnmon startup

```nano /etc/rc.local```

tambahkan baris berikut

```/usr/bin/ovpnmon```

reboot openWrt

### ganti CUSTOM-HEADER Host

```ovpn yt``` atau ```ovpn ig```

