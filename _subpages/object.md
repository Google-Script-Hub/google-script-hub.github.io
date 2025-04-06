---
layout: default
title: Đối tượng (Object)
description: Object trong Google App Script
redirect_from:
  - /3/
---

Vì dựa trên Javascript nên Google App Script vẫn có Object. Về đa số, Google App Script chỉ cần lập trình hàm là đủ, tuy nhiên để cho mã trở lên sáng sủa hơn chúng ta có thể sử dụng thêm Object.

Object trong Google App Script được khai báo và goi như sau: 

```javascript
var Utils = {
  sayHello: function(name) {
    return "Hello from Utils, " + name + "!";
  }
};

function myFunction() {
  let mess = Utils.sayHello("Hello");
  Logger.log(mess);
}

```

Chọn funciton `myFunction`, xong đó bấm chạy để xem kết quả:

<img src="./../img/3.png" style="max-width: 100%">