# Hướng dẫn giải (WRITEUP) - Simple Challenge

## 1. Sơ đồ topology

```text
[ student-vm ]
 10.10.10.10
      |
(attacker-net) 10.10.10.0/24
      |
 10.10.10.1
[ edge-router ]
 10.10.20.1
      |
(internal-net) 10.10.20.0/24
      |
 10.10.20.10
[ web-server ] (port 80)
```

## 2. Bảng tài khoản

| Hệ thống | User | Mật khẩu | Lấy từ đâu |
|---|---|---|---|
| student-vm | student | (Platform cấp) | SSH trực tiếp |

## 3. Luồng tấn công dự kiến

`student-vm` -> HTTP GET tới `10.10.20.10` -> Đọc mã nguồn HTML -> Có flag.

## 4. Lời giải từng mission

**Mission 1:**
Học viên vào `student-vm` và chạy lệnh sau để lấy nội dung web:
```bash
curl http://10.10.20.10
```
Flag nằm trong HTML comment: `<!-- Secret: FLAG{basic_web_discovery} -->`

## 5. Rà lối tắt

* Không có lỗi hổng nào cho phép lấy flag sai mục đích. Máy đích không cấp quyền SSH.
* Flag được giấu đơn giản trong mã nguồn HTML, phù hợp với người mới.
