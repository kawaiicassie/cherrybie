---
title: 'Hướng Dẫn Sử Dụng GitHub Action và GitHub Pages Để Deploy Trang Web Tĩnh 🚀'
published: 2025-07-16T13:43:27.401-04:00
description: 'Bài viết hướng dẫn chi tiết cách sử dụng GitHub Action và GitHub Pages để tự động deploy trang web tĩnh miễn phí, dành cho người mới bắt đầu.'
category: 'Lập Trình Web'
tags: ['GitHub', 'GitHub Actions', 'GitHub Pages', 'Deploy', 'Web Tĩnh']
draft: false
---

# Hướng Dẫn Sử Dụng GitHub Action và GitHub Pages Để Deploy Trang Web Tĩnh 🚀

Bạn đang muốn host một trang web tĩnh miễn phí và tự động hóa quá trình deploy? GitHub Action và GitHub Pages là bộ đôi hoàn hảo dành cho bạn! Bài viết này sẽ hướng dẫn bạn từ A đến Z cách triển khai trang web tĩnh một cách dễ dàng và hiệu quả. Cùng bắt đầu thôi! 💻✨

## 1. Giới Thiệu Về GitHub Action và GitHub Pages

### GitHub Pages 🌐
GitHub Pages là dịch vụ hosting miễn phí của GitHub, cho phép bạn publish trang web tĩnh (HTML, CSS, JavaScript) trực tiếp từ repository GitHub của mình.

### GitHub Actions ⚙️
GitHub Actions là công cụ CI/CD (Continuous Integration/Continuous Deployment) giúp tự động hóa các tác vụ như build, test, và deploy code. Bạn có thể thiết lập workflow để tự động deploy trang web mỗi khi có thay đổi code.

## 2. Các Bước Triển Khai

### Bước 1: Tạo Repository Trên GitHub
1. Đăng nhập vào GitHub và tạo một repository mới.
2. Đặt tên repository theo định dạng `username.github.io` (nếu bạn muốn sử dụng GitHub Pages cho trang cá nhân).

### Bước 2: Thêm Code Trang Web Tĩnh
- Clone repository về máy.
- Thêm các file HTML, CSS, JavaScript vào thư mục gốc của repository.
- Push code lên GitHub.

### Bước 3: Thiết Lập GitHub Pages
1. Vào **Settings** của repository.
2. Chọn **Pages** từ menu bên trái.
3. Chọn nhánh (branch) chứa code (thường là `main` hoặc `master`).
4. Nhấn **Save**.

### Bước 4: Tạo GitHub Action Workflow
1. Tạo thư mục `.github/workflows` trong repository.
2. Tạo file `deploy.yml` với nội dung sau:
```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./  # Thư mục chứa file web tĩnh
```
3. Push file này lên GitHub.

## 3. Case Studies Thực Tế

### Case Study 1: Portfolio Cá Nhân 🎨
- **Mục đích**: Host portfolio cá nhân miễn phí.
- **Kết quả**: Trang web tự động deploy mỗi khi có thay đổi, tiết kiệm thời gian và công sức.

### Case Study 2: Blog Tĩnh 📝
- **Mục đích**: Tạo blog sử dụng Jekyll hoặc Hugo.
- **Kết quả**: Bài viết mới được publish ngay lập tức sau khi push code.

### Case Study 3: Landing Page Sản Phẩm 🚀
- **Mục đích**: Giới thiệu sản phẩm mới.
- **Kết quả**: Khách hàng truy cập nhanh chóng, không cần server phức tạp.

## 4. Kết Luận
GitHub Action và GitHub Pages là công cụ mạnh mẽ giúp bạn triển khai trang web tĩnh một cách dễ dàng và miễn phí. Hãy thử ngay và chia sẻ thành quả của bạn nhé! 🎉

**CTA**: Theo dõi blog của mình để không bỏ lỡ các bài viết hữu ích khác về lập trình và công nghệ! Cảm ơn bạn đã đọc bài viết! (＾▽＾)／