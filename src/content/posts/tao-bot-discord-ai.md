---
title: "Hướng Dẫn Tạo Bot Discord AI Đơn Giản Với Chức Năng Chat"
published: 2025-07-17T03:05:58.305-04:00
description: 'Hướng dẫn chi tiết cách tạo một bot Discord AI với chức năng trò chuyện cơ bản, dành cho người mới bắt đầu.'
tags: ["Discord", "AI", "Chatbot", "Lập Trình"]
category: "Công Nghệ"
draft: false
---

# Hướng Dẫn Tạo Bot Discord AI Đơn Giản Với Chức Năng Chat 💬🤖

Bạn muốn tạo một bot Discord có khả năng trò chuyện thông minh như AI? Bài viết này sẽ hướng dẫn bạn từng bước để tạo một bot Discord AI đơn giản, sử dụng các công cụ miễn phí và dễ dàng triển khai. Hãy cùng bắt đầu nhé! 🚀

## 1. Chuẩn Bị Trước Khi Tạo Bot

Trước khi bắt đầu, bạn cần chuẩn bị những thứ sau:

- **Tài khoản Discord**: Đăng ký nếu bạn chưa có.
- **Máy chủ Discord (Server)**: Tạo một server để thử nghiệm bot.
- **Node.js**: Cài đặt Node.js (phiên bản LTS) để chạy mã bot.
- **Trình chỉnh sửa mã**: Ví dụ: Visual Studio Code.

## 2. Tạo Ứng Dụng Bot Trên Discord Developer Portal

1. Truy cập [Discord Developer Portal](https://discord.com/developers/applications).
2. Nhấn **New Application** và đặt tên cho bot.
3. Vào mục **Bot** và nhấn **Add Bot**.
4. Sao chép **Token** của bot (giữ bí mật token này!).

## 3. Thiết Lập Mã Bot Cơ Bản

Sử dụng thư viện `discord.js` để tạo bot:

```bash
npm init -y
npm install discord.js
```

Tạo file `index.js` và thêm mã sau:

```javascript
const Discord = require('discord.js');
const client = new Discord.Client();

client.on('ready', () => {
  console.log(`Bot đã sẵn sàng: ${client.user.tag}`);
});

client.on('message', async (message) => {
  if (message.author.bot) return;

  if (message.content === '!hello') {
    message.reply('Xin chào! Tôi là bot AI của bạn. 👋');
  }
});

client.login('YOUR_BOT_TOKEN');
```

Thay `YOUR_BOT_TOKEN` bằng token của bạn.

## 4. Thêm Chức Năng AI Chat

Bạn có thể sử dụng API miễn phí như **OpenAI** hoặc **Dialogflow** để tích hợp AI. Ví dụ với OpenAI:

```bash
npm install openai
```

Thêm mã sau vào file `index.js`:

```javascript
const { Configuration, OpenAIApi } = require('openai');
const configuration = new Configuration({
  apiKey: 'YOUR_OPENAI_API_KEY',
});
const openai = new OpenAIApi(configuration);

client.on('message', async (message) => {
  if (message.author.bot) return;

  if (message.content.startsWith('!ask')) {
    const prompt = message.content.slice(5);
    const response = await openai.createCompletion({
      model: 'text-davinci-003',
      prompt: prompt,
      max_tokens: 150,
    });
    message.reply(response.data.choices[0].text);
  }
});
```

## 5. Chạy Bot Và Kiểm Thử

1. Chạy bot bằng lệnh:
   ```bash
   node index.js
   ```
2. Mời bot vào server Discord của bạn.
3. Thử gõ `!hello` hoặc `!ask [câu hỏi]` để kiểm tra.

## Kết Luận

Vậy là bạn đã tạo thành công một bot Discord AI đơn giản với chức năng trò chuyện! 🎉 Bạn có thể nâng cấp bot bằng cách thêm nhiều tính năng hơn như xử lý hình ảnh, phản hồi tự động, hay tích hợp AI mạnh mẽ hơn.

Nếu có thắc mắc, hãy để lại bình luận bên dưới nhé! Cảm ơn bạn đã theo dõi bài viết. (＾▽＾)／

**CTA:** Bạn muốn tìm hiểu thêm về bot Discord? Theo dõi blog của chúng tôi để cập nhật các hướng dẫn mới nhất!