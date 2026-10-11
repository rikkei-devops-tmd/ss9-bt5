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

3. CAC BUOC THUC HIEN VA KET QUA TERMINAL THUC TE

3.1. Khoi chay dich vu o che do ngam
Lenh thuc hien:
```bash
docker compose up -d
```
Ket qua dau ra:
```text
Container session_09_ex5-web-1 Creating
Container session_09_ex5-web-1 Created
Container session_09_ex5-web-1 Starting
Container session_09_ex5-web-1 Started
```

3.2. Kiem tra trang thai dich vu dang chay
Lenh thuc hien:
```bash
docker compose ps
```
Ket qua dau ra:
```text
NAME                   IMAGE          COMMAND                  SERVICE   CREATED        STATUS                  PORTS
session_09_ex5-web-1   nginx:alpine   "/docker-entrypoint.…"   web       1 second ago   Up Less than a second   0.0.0.0:8082->80/tcp, [::]:8082->80/tcp
```

3.3. Gui truy van HTTP kiem tra phan hoi
Lenh thuc hien:
```bash
curl -s http://localhost:8082
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
<p>If you see this page, nginx is successfully installed and working.
Further configuration is required for the web server, reverse proxy, 
API gateway, load balancer, content cache, or other features.</p>

<p>For online documentation and support please refer to
<a href="https://nginx.org/">nginx.org</a>.<br/>
To engage with the community please visit
<a href="https://community.nginx.org/">community.nginx.org</a>.<br/>
For enterprise grade support, professional services, additional 
security features and capabilities please refer to
<a href="https://f5.com/nginx">f5.com/nginx</a>.</p>

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
Container session_09_ex5-web-1 Stopping
Container session_09_ex5-web-1 Stopped
Container session_09_ex5-web-1 Removing
Container session_09_ex5-web-1 Removed
Network session_09_ex5_default Removing
Network session_09_ex5_default Removed
```

4. TONG KET CAC LENH
```bash
docker compose up -d
docker compose ps
curl -s http://localhost:8082
docker compose down
```
