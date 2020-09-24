# proxy ovpn

Edit file .ovpn tambahkan sebelum ```<ca>```

Contoh untuk sawer paket youtube tsel

```
http-proxy-retry
http-proxy ip-proxy port-proxy stdin basic
<http-proxy-user-pass>
userproxy
passwordproxy
</http-proxy-user-pass>
http-proxy-option CUSTOM-HEADER CONNECT HTTP/1.1
http-proxy-option CUSTOM-HEADER Host m.youtube.com
```
