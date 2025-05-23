---
layout: default
title: Tô màu từ khóa trong Google Docs
description: Tô màu từ khóa trong Google Docs
redirect_from:
  - /8/
  - /color-text-keyword-in-google-docs/
---

## Tại sao cần phải highlight?

Việc tô màu từ khóa (keyword), hay đoạn văn để làm nổi bật (highlight) là điều không hề còn xa lạ gì với học sinh, sinh viên hay bất kỳ ai làm văn phòng. Highlight giúp nhấn mạnh thông tin quan trọng giúp người đọc dễ dàng tập chung hơn vào các từ khóa chính, từ khóa quan trọng của đoạn văn, câu văn.

Giờ có một văn bản cả trăm trang hay nghìn trang thì việc đánh highlight quả thật là không dễ và rất gian nan. Bài viết này mình sẽ hướng dẫn sử dụng Google App Script để đánh highlight keyword cho Google Docs.

## Chuẩn bị

Chuẩn bị trước một file Google Docs cần highlight như hình dưới:

<img src="./../img/8_1.png" style="max-width: 100%">

Phần URL của file sẽ có dạng `https://docs.google.com/document/d/XXXXX/edit?tab=t.0`, phần `XXXXX` chính là phần ID của file, copy lại ID này để sử dụng cho phần dưới.

Chọn `Tiện ích -> Apps Script` để bắt đầu Code.

## Highlight bằng Google App Script

Đầu tiên định nghĩa một Object để chứa màu, như vậy code sẽ clear hơn: 

```javascript
var COLOR = {
  WHITE: "#FFFFFF",
  RED: "#FF0000",
  BLUD: "#0000FF"
};
```

Sau đó mình viết hàm đọc và tô màu Google Docs như sau: 

```javascript
function main() {
  parseGoogleDocById("1I894aTTHqAwZfFqIZUilTOgBdx7tWrswiCtB8dCZYwU");
}

function parseGoogleDocById(documentId) {
  var doc = DocumentApp.openById(documentId);
  var body = doc.getBody();
  var text = body.getText();

  var keyword = "thế giới quan";
  var keywordFindRegex = new RegExp(keyword, "gi");

  var range = body.editAsText();
  while ((match = keywordFindRegex.exec(text)) !== null) {
    Logger.log("FIND IT!");
    var keywordIndex = match.index; 
    
    // color keyword
    range.setBackgroundColor(keywordIndex, keywordIndex + keyword.length - 1, COLOR.RED);
  }
}
```

- Hàm `parseGoogleDocById` nhận đầu vào là ID của Google Docs (Cách lấy ID đã được trình bày ở phần trên)

- `new RegExp(keyword, "gi");`: Regex với tham số `g` cho phép tìm tất cả, `i` cho phép tìm không phân biệt hoa thường

Chạy chương trình với hàm chính là hàm `main` sẽ có được kết quả như sau: 

<img src="./../img/8_2.png" style="max-width: 100%">

<img src="./../img/8_3.png" style="max-width: 100%">

Xem mã nguồn trong phần `Tiện ích -> App Script` của file Google Docs [https://docs.google.com/document/d/1I894aTTHqAwZfFqIZUilTOgBdx7tWrswiCtB8dCZYwU/edit?usp=sharing](https://docs.google.com/document/d/1I894aTTHqAwZfFqIZUilTOgBdx7tWrswiCtB8dCZYwU/edit?usp=sharing), file `color_text.gs`.