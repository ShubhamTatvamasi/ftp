# ftp


```bash
docker run -d \
  --name sftpgo \
  -p 8080:8080 \
  -p 21:21 \
  -p 51000-51100:51000-51100 \
  -v $(pwd)/data:/srv/sftpgo/data/ \
  -v $(pwd)/sftpgo:/var/lib/sftpgo/ \
  -e SFTPGO_DATA_PROVIDER__CREATE_DEFAULT_ADMIN=true \
  -e SFTPGO_DEFAULT_ADMIN_USERNAME=admin \
  -e SFTPGO_DEFAULT_ADMIN_PASSWORD=admin123 \
  -e SFTPGO_FTPD__BINDINGS__0__PORT=21 \
  -e SFTPGO_FTPD__PASSIVE_PORT_RANGE__START=51000 \
  -e SFTPGO_FTPD__PASSIVE_PORT_RANGE__END=51100 \
  -e SFTPGO_FTPD__FORCE_PASSIVE_IP=YOUR_SERVER_IP \
  -e SFTPGO_SFTPD__BINDINGS__0__PORT=0 \
  -e SFTPGO_HTTPD__BINDINGS__0__PORT=8080 \
  -e SFTPGO_WEBDAVD__BINDINGS__0__PORT=0 \
  drakkan/sftpgo:latest
```

http://192.168.1.8:8080/web/admin/login

http://192.168.1.8:8080/web/client/login

---

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
> NOTE: change the IP of `PASV_ADDRESS` variable
