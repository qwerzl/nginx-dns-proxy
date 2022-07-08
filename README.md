`git clone https://github.com/qwerzl/nginx-dns-proxy --recurse-submodules`

`cd nginx-dns`

`sudo docker run -v $(pwd)/nginx.conf:/etc/nginx/nginx.conf:ro -v [fullchain.cer]:/etc/nginx/ssl/certs/doh.local.pem  -v [key]:/etc/nginx/ssl/private/doh.local.pem -v $(pwd)/nginx-dns/njs.d:/etc/nginx/njs.d:ro -p [port]:8043  --name nginx-dns nginx:latest`

# TODO
[ ] get that `nginx-quic` docker image right
