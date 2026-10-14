# Bài 2: Đóng gói Ứng dụng Backend với Dockerfile Chuẩn Production

## Mục tiêu
- Viết `Dockerfile` chuẩn theo các best practices: dùng alpine base image, thiết lập `WORKDIR`, cấu hình biến môi trường `ENV`, ánh xạ cổng `EXPOSE`, sử dụng `.dockerignore`.
- Build image và khởi chạy container kiểm tra khả năng phục vụ HTTP.

---

## 1. Cấu trúc Dự án

```text
ss10/b2/
├── .dockerignore
├── Dockerfile
├── package.json
├── server.js
└── README.md
```

---

## 2. Các Bước Build & Chạy Container

### Bước 1: Build Docker Image
```bash
docker build -t backend-api:v1 .
```

### Bước 2: Khởi chạy Container
```bash
docker run -d -p 3000:3000 --name api-service backend-api:v1
```

### Bước 3: Kiểm tra Kết quả qua `curl`
```bash
$ curl -s http://localhost:3000 | jq .
{
  "message": "Hello from Node.js Express Backend Container!",
  "status": "UP",
  "timestamp": "2026-10-11T03:30:00.000Z"
}
```

---

## 3. Dọn dẹp
```bash
docker rm -f api-service
```
