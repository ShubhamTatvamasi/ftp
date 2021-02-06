# ftp

check your local IP address:
```bash
ip addr
```

start ftp server:
```bash
docker run -d -v ${PWD}:/home/vsftpd \
  -p 20:20 -p 21:21 -p 47400-47470:47400-47470 \
  -e FTP_USER=admin \
  -e FTP_PASS=admin \
  -e PASV_ADDRESS=192.168.0.109 \
  --name ftp \
  --restart=always \
  bogem/ftp
```
