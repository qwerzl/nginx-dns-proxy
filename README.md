# nginx-dns-proxy
```
git clone https://github.com/qwerzl/nginx-dns-proxy --recurse-submodules

cd nginx-dns-proxy


sudo docker pull macbre/nginx-http3:latest

sudo docker run \
  -v $(pwd)/nginx.conf:/etc/nginx/nginx.conf:ro \
  -v [fullchain.cer]:/etc/nginx/ssl/certs/doh.local.pem  \
  -v [key]:/etc/nginx/ssl/private/doh.local.pem \
  -v $(pwd)/nginx-dns/njs.d:/etc/nginx/njs.d:ro \
  -p [port]:8043  \
  --name nginx-dns \
  macbre/nginx-http3:latest
```

Defult max-connection number is set to 5. One may change it through `nginx.conf`.

**NOTICE**: basic auth is only available for DoH.

# TODO
- [x] get that `nginx-quic` docker image right
