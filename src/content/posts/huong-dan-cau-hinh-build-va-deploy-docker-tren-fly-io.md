---
title: 'Hướng dẫn cách cấu hình, build và deploy Docker trên Fly.io'
published: 2025-07-16T12:27:29.884-04:00
description: 'Bài viết hướng dẫn chi tiết cách cấu hình, build và deploy ứng dụng Docker trên nền tảng Fly.io.'
category: 'DevOps'
tags: ['Docker', 'Fly.io', 'Deployment', 'DevOps']
draft: false
---

# Hướng dẫn cách cấu hình, build và deploy Docker trên Fly.io

Fly.io là một nền tảng giúp bạn dễ dàng triển khai các ứng dụng container hóa với Docker. Bài viết này sẽ hướng dẫn bạn từng bước để cấu hình, build và deploy ứng dụng Docker lên Fly.io.

## 1. Chuẩn bị

Trước khi bắt đầu, bạn cần:

- Cài đặt [Docker](https://www.docker.com/get-started) trên máy tính.
- Cài đặt [Fly.io CLI](https://fly.io/docs/hands-on/install-flyctl/).
- Tạo một tài khoản trên [Fly.io](https://fly.io/).

## 2. Tạo Dockerfile

Đầu tiên, bạn cần tạo một `Dockerfile` trong thư mục gốc của dự án. Ví dụ:

```dockerfile
# Sử dụng image base
FROM node:14

# Tạo thư mục làm việc
WORKDIR /usr/src/app

# Sao chép package.json và package-lock.json
COPY package*.json ./

# Cài đặt các dependencies
RUN npm install

# Sao chép toàn bộ mã nguồn
COPY . .

# Expose cổng ứng dụng
EXPOSE 3000

# Khởi chạy ứng dụng
CMD ["npm", "start"]
```

## 3. Build Docker Image

Sau khi có `Dockerfile`, bạn có thể build image bằng lệnh:

```bash
docker build -t your-app-name .
```

## 4. Đăng nhập vào Fly.io

Mở terminal và chạy lệnh sau để đăng nhập:

```bash
flyctl auth login
```

## 5. Tạo ứng dụng trên Fly.io

Chạy lệnh sau để tạo ứng dụng mới:

```bash
flyctl launch
```

Lệnh này sẽ hỏi bạn một số thông tin như tên ứng dụng, region, v.v. Sau khi hoàn tất, Fly.io sẽ tạo một file `fly.toml` để cấu hình.

## 6. Deploy ứng dụng

Cuối cùng, deploy ứng dụng bằng lệnh:

```bash
flyctl deploy
```

Fly.io sẽ tự động build và deploy ứng dụng của bạn từ `Dockerfile`.

## 7. Kiểm tra ứng dụng

Sau khi deploy thành công, bạn có thể mở ứng dụng bằng lệnh:

```bash
flyctl open
```

Hoặc kiểm tra trạng thái ứng dụng:

```bash
flyctl status
```

## Kết luận

Với các bước đơn giản trên, bạn đã có thể cấu hình, build và deploy ứng dụng Docker lên Fly.io một cách dễ dàng. Fly.io cung cấp nhiều tính năng mạnh mẽ như scaling, monitoring, giúp bạn tập trung vào phát triển ứng dụng thay vì quản lý infrastructure.

Chúc bạn thành công!