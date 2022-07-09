# nginx-dns-proxy
```
git clone https://github.com/qwerzl/nginx-dns-proxy --recurse-submodules

cd nginx-dns

printf "[USERNAME]:$(openssl passwd -crypt [PASSWORD])\n" >>/home/htpasswd

sudo docker run \
  -v $(pwd)/nginx.conf:/etc/nginx/nginx.conf:ro \
  -v [fullchain.cer]:/etc/nginx/ssl/certs/doh.local.pem  \
  -v [key]:/etc/nginx/ssl/private/doh.local.pem \
  -v $(pwd)/nginx-dns/njs.d:/etc/nginx/njs.d:ro \
  -v $(pwd)/htpasswd:/home/htpasswd -p [port]:8043  \
  --name nginx-dns \
  nginx:latest
```

Defult max-connection number is set to 5. One may change it through `nginx.conf`.

**NOTICE**: basic auth is only configured for the DoH as for now.

# TODO
[ ] get that `nginx-quic` docker image right
