---
layout: default
title: Gửi email với Google App Script
description: Gửi email với Google App Script
redirect_from:
  - /9/
---

Gmail cho phép Google App Script truy cập vào hòm thư và gửi email nếu được cấp quyền. Đoạn script sau sẽ giúp bạn gửi email từ hòm thư của bạn tới hòm thư khác như sau: 

```javascript
function sendLogEmail() {
  var recipient = 'demanejar@gmail.com'; 
  var subject = "Hello, Demanejar";
  var body = "I'm Google Script Hub";
  MailApp.sendEmail(recipient, subject, body);
}
```

Bạn có thể kết hợp với các bài viết [Tạo Bot Telegram Thông Báo Công Việc Từ Google Sheets Bằng Google Apps Script](https://google-script-hub.github.io/send-notification-to-telegram) để lấy dữ liệu từ Google Sheet gửi email marketing tới email tương ứng trên Google sheet để đỡ phải soạn thảo từng email một.

Google App Script là một công cụ tối ưu, tự động hóa công việc cá nhân mạnh mẽ và đặc biệt là nó miễn phí.