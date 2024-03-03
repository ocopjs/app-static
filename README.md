<!--[meta]
section: api
subSection: apps
title: Static file app
[meta]-->

# Static file app

> Lưu ý sau khi phiên bản KeystoneJS 5 dừng phát triển tính năng mới và chuyển
> sang chế độ duy trì để ra mắt phiên bản mới hơn. Chúng tôi đã dựa trên mã
> nguồn cũ này để phát triển một phiên bản khác với một số tính năng theo hướng
> microservices.

OcopJS - Ứng dụng để trả về trang từ tệp tĩnh.

## Sử dụng

```js title=index.js
const { Ocop } = require("@ocopjs/ocop");
const { GraphQLApp } = require("@ocopjs/app-graphql");
const { AdminUIApp } = require("@ocopjs/app-admin-ui");
const { StaticApp } = require("@ocopjs/app-static");

module.exports = {
  ocop: new Ocop(),
  apps: [
    new GraphQLApp(),
    new AdminUIApp(),
    new StaticApp({
      path: "/",
      src: "public",
      fallback: "index.html",
    }),
  ],
};
```

## Cấu hình

| Cấu hình   | Loại     | Mặc định | Mô tả                                                          |
| ---------- | -------- | -------- | -------------------------------------------------------------- |
| `path`     | `string` | `true`   | Đường dẫn tới tệp cần chạy.                                    |
| `src`      | `string` | `true`   | Đường dẫn tới thư mục chưa tệp tĩnh.                           |
| `fallback` | `string` | `false`  | Đường dẫn tới tệp sẽ hiển thị ra nếu tệp chính không tìm thấy. |
