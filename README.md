BAI 5: KHOI CHAY DICH VU DON GIAN VOI DOCKER COMPOSE

1. MUC TIEU
- Khai bao cau hinh dich vu bang tep docker-compose.yml voi cu phap Compose Spec v2.
- Khoi chay va quan ly vong doi dich vu bang Docker Compose CLI.
- Kiem tra ket noi dich vu qua port 8082 va ha dich vu sach se.

2. CAU HINH DOCKER COMPOSE

Tep docker-compose.yml:
```yaml
services:
  web:
    image: nginx:alpine
    ports:
      - "8082:80"
```

3. CAC BUOC THUC HIEN VA KIEM TRA

3.1. Khoi chay dich vu o che do ngam
Lenh thuc hien:
```bash
docker compose up -d
```
Ket qua dau ra:
```text
[+] Running 2/2
 ✔ Network ss9-bt5_default  Created
 ✔ Container ss9-bt5-web-1  Started
```

3.2. Kiem tra trang thai dich vu dang chay
Lenh thuc hien:
```bash
docker compose ps
```
Ket qua dau ra:
```text
NAME              IMAGE          COMMAND                  SERVICE   CREATED          STATUS          PORTS
ss9-bt5-web-1     nginx:alpine   "/docker-entrypoint.…"   web       10 seconds ago   Up 9 seconds    0.0.0.0:8082->80/tcp
```

3.3. Gui truy van HTTP kiem tra phan hoi
Lenh thuc hien:
```bash
curl http://localhost:8082
```
Ket qua dau ra:
```text
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

3.4. Ha dich vu va don dep tai nguyen
Lenh thuc hien:
```bash
docker compose down
```
Ket qua dau ra:
```text
[+] Running 2/2
 ✔ Container ss9-bt5-web-1  Removed
 ✔ Network ss9-bt5_default  Removed
```

4. TONG KET CAC LENH
```bash
docker compose up -d
docker compose ps
curl http://localhost:8082
docker compose down
```
