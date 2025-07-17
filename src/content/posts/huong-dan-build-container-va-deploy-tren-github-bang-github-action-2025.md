---
title: "Hướng dẫn Build Container và Deploy trên GitHub bằng GitHub Actions vào năm 2025"
published: 2025-07-17T02:47:15.747-04:00
description: "Hướng dẫn từng bước để build container và tự động deploy ứng dụng lên server bằng GitHub Actions và Docker vào năm 2025."
tags: ["GitHub Actions", "Docker", "CI/CD", "DevOps"]
category: "Công Nghệ"
draft: false
---

# Hướng dẫn Build Container và Deploy trên GitHub bằng GitHub Actions vào năm 2025

🚀 **GitHub Actions** và **Docker** đã trở thành bộ đôi không thể thiếu trong quy trình CI/CD hiện đại. Bài viết này sẽ hướng dẫn bạn từng bước để build container và tự động deploy ứng dụng lên server một cách dễ dàng và hiệu quả nhất vào năm 2025!

---

## 1. Tại sao nên sử dụng GitHub Actions và Docker?

✅ **Miễn phí** cho dự án cá nhân và mã nguồn mở.
✅ **Tự động hóa** quy trình build, test, và deploy.
✅ **Dễ dàng tích hợp** với các công cụ DevOps khác.
✅ **Hỗ trợ đa nền tảng** (Linux, Windows, macOS).

---

## 2. Chuẩn bị trước khi bắt đầu

### Yêu cầu cơ bản:
- Tài khoản GitHub.
- Docker đã cài đặt trên máy local (nếu muốn test trước).
- Một dự án có sẵn (ví dụ: NextJS, NodeJS, Python, v.v.).

---

## 3. Các bước triển khai CI/CD với GitHub Actions và Docker

### Bước 1: Tạo Dockerfile
Để build container, bạn cần một `Dockerfile` trong thư mục gốc của dự án. Ví dụ:

```dockerfile
# Sử dụng image base phù hợp (ví dụ: NodeJS)
FROM node:18-alpine

# Thiết lập thư mục làm việc
WORKDIR /app

# Copy file package.json và package-lock.json
COPY package*.json ./

# Cài đặt dependencies
RUN npm install

# Copy toàn bộ mã nguồn
COPY . .

# Build ứng dụng (nếu cần)
RUN npm run build

# Mở cổng (ví dụ: 3000 cho NextJS)
EXPOSE 3000

# Lệnh khởi chạy ứng dụng
CMD ["npm", "start"]
```

### Bước 2: Tạo workflow GitHub Actions
Tạo file `.github/workflows/deploy.yml` trong dự án của bạn:

```yaml
name: Build and Deploy

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Login to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKER_HUB_USERNAME }}
          password: ${{ secrets.DOCKER_HUB_TOKEN }}

      - name: Build and push Docker image
        uses: docker/build-push-action@v5
        with:
          context: .
          push: true
          tags: your-dockerhub-username/your-app-name:latest

  deploy:
    needs: build
    runs-on: ubuntu-latest

    steps:
      - name: SSH into server and deploy
        uses: appleboy/ssh-action@v1
        with:
          host: ${{ secrets.SERVER_HOST }}
          username: ${{ secrets.SERVER_USERNAME }}
          key: ${{ secrets.SERVER_SSH_KEY }}
          script: |
            docker pull your-dockerhub-username/your-app-name:latest
            docker stop your-app-name || true
            docker rm your-app-name || true
            docker run -d --name your-app-name -p 3000:3000 your-dockerhub-username/your-app-name:latest
```

### Bước 3: Cấu hình Secrets trên GitHub
Truy cập `Settings > Secrets and variables > Actions` để thêm các biến môi trường cần thiết:
- `DOCKER_HUB_USERNAME`: Tên đăng nhập Docker Hub.
- `DOCKER_HUB_TOKEN`: Token Docker Hub.
- `SERVER_HOST`, `SERVER_USERNAME`, `SERVER_SSH_KEY`: Thông tin server deploy.

---

## 4. Kiểm tra và triển khai
Sau khi push code lên branch `main`, GitHub Actions sẽ tự động chạy workflow:
1. Build Docker image.
2. Push image lên Docker Hub.
3. SSH vào server và deploy ứng dụng.

🎉 **Xong!** Ứng dụng của bạn đã được deploy tự động.

---

## 5. Tài liệu tham khảo
- [Triển khai CI/CD với GitHub Actions và Docker](https://devops.vn/posts/trien-khai-ci-cd-voi-github-actions-va-docker/)
- [Hướng dẫn triển khai CI/CD cho NextJS](https://200lab.io/blog/huong-dan-deploy-ung-dung-nextjs-voi-github-action)

---

## Kết luận
Với GitHub Actions và Docker, bạn có thể tự động hóa quy trình deploy một cách dễ dàng và tiết kiệm thời gian. Hãy thử ngay và chia sẻ kết quả với cộng đồng nhé!

💖 **Cảm ơn bạn đã đọc bài viết!** (づ｡◕‿‿◕｡)づ