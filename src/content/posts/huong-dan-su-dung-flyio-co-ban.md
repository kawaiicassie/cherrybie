---
title: "Hướng Dẫn Sử Dụng Fly.io Cơ Bản"
date: "2023-10-25"
description: "Bài viết hướng dẫn cách sử dụng Fly.io cơ bản để triển khai ứng dụng một cách dễ dàng."
category: "Công Nghệ"
tags: ["Fly.io", "Deployment", "Cloud"]
---

## Giới Thiệu
Fly.io là một nền tảng triển khai ứng dụng (deployment platform) giúp bạn chạy các ứng dụng của mình trên cloud một cách dễ dàng. Với Fly.io, bạn có thể triển khai ứng dụng từ container Docker hoặc trực tiếp từ mã nguồn mà không cần phải lo lắng về cơ sở hạ tầng.

## Cài Đặt Fly.io
1. **Cài đặt Fly CLI**: Đầu tiên, bạn cần cài đặt công cụ dòng lệnh (CLI) của Fly.io. Chạy lệnh sau trong terminal:
   ```bash
   curl -L https://fly.io/install.sh | sh
   ```

2. **Đăng nhập**: Sau khi cài đặt, đăng nhập vào tài khoản Fly.io của bạn bằng lệnh:
   ```bash
   fly auth login
   ```

## Triển Khai Ứng Dụng
1. **Khởi tạo ứng dụng**: Di chuyển đến thư mục dự án của bạn và chạy lệnh sau để khởi tạo ứng dụng trên Fly.io:
   ```bash
   fly launch
   ```
   Lệnh này sẽ hỏi bạn một số thông tin như tên ứng dụng, region, v.v.

2. **Triển khai ứng dụng**: Sau khi khởi tạo, triển khai ứng dụng bằng lệnh:
   ```bash
   fly deploy
   ```

3. **Mở ứng dụng**: Để mở ứng dụng sau khi triển khai, chạy lệnh:
   ```bash
   fly open
   ```

## Quản Lý Ứng Dụng
- **Xem danh sách ứng dụng**:
  ```bash
  fly apps list
  ```

- **Xem thông tin ứng dụng**:
  ```bash
  fly info
  ```

- **Scale ứng dụng**: Để tăng số lượng instance, chạy lệnh:
  ```bash
  fly scale count 2
  ```

## Kết Luận
Fly.io là một công cụ mạnh mẽ và dễ sử dụng để triển khai ứng dụng trên cloud. Với các bước đơn giản như trên, bạn có thể bắt đầu sử dụng Fly.io ngay hôm nay!

Nếu bạn có bất kỳ câu hỏi nào, hãy để lại bình luận bên dưới. Chúc bạn thành công!