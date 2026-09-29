# Hệ thống quản lý chung CSĐT

Kho chứa **bản cài và bản cập nhật** của phần mềm. Kho này chỉ chứa gói cài, không chứa mã nguồn.

---

## ⬇ TẢI BỘ CÀI (bấm vào đây)

### 👉 [**Setup_DatAggregator_v1.2.4.exe** — Hệ thống quản lý CSĐT](https://github.com/khavy1203/csdt-release/releases/download/dataggregator-latest/Setup_DatAggregator_v1.2.4_20260929_150057.exe)

Tải file đó về, bấm đúp để cài. **Không cần gỡ bản cũ** — cài đè, dữ liệu và cấu hình giữ nguyên.

> ⚠️ **Phải cài bằng file Setup này.** Bộ cài tự kiểm tra và **cài luôn ODBC Driver 17 for SQL
> Server** nếu máy chưa có — thiếu driver đó là phần mềm báo lỗi
> *"Data source name not found and no default driver specified (IM002)"* và không nối được
> cơ sở dữ liệu. Các file `.zip` trong mục Releases **không có driver**, chúng chỉ dùng cho
> chức năng tự cập nhật của phần mềm.

Khi cài, Windows có thể hiện **"Windows protected your PC"** → bấm **More info** → **Run anyway**
(bộ cài chưa mua chữ ký số). Bước cài driver sẽ hỏi quyền Administrator → bấm **Yes**.

---

## Máy đã cài rồi thì sao?

Phần mềm **tự kiểm tra và báo khi có bản mới**. Khi hiện hộp thoại "Cập nhật ngay?":

- **Yes** — tự tải, tự cài, mở lại (bản đang dùng được sao lưu tự động).
- **No** — dùng tiếp bản cũ, khi nào tiện thì cập nhật.

Nút **Phiên bản** trong phần mềm cho xem mọi bản đã phát hành và **quay lại bản cũ** nếu cần.
Bản mới lỗi không mở được thì phần mềm **tự khôi phục bản cũ**.

> Máy cài từ **trước 14/09/2026** thì nút Cập nhật không tìm thấy bản mới (kênh cập nhật đã đổi).
> Những máy đó hãy tải file Setup ở trên cài đè một lần, sau đó cập nhật tự động chạy lại bình thường.

---

## Lỗi hay gặp

**"Data source name not found... IM002"**
Máy thiếu ODBC Driver 17. Cài bằng file Setup ở trên, hoặc cài riêng driver:
[tải từ Microsoft](https://go.microsoft.com/fwlink/?linkid=2266337) (cần quyền Administrator).

**"No connection could be made because the target machine actively refused it"**
Máy chủ SQL không nhận kết nối. Kiểm tra theo thứ tự:

1. Dịch vụ **SQL Server** đã chạy chưa (`services.msc`).
2. **TCP/IP** đã bật chưa — SQL Server Configuration Manager → Protocols → TCP/IP → **Enable** → khởi động lại dịch vụ.
3. Máy chủ dạng `TÊNMÁY\SQLEXPRESS` thì cần bật thêm dịch vụ **SQL Server Browser**.
4. Kiểm tra nhanh: `Test-NetConnection <địa-chỉ-máy-chủ> -Port 1433`

---

## Liên hệ hỗ trợ

**Khả Vy · Nông Lâm Trung Bộ** — ĐT **0987980417**
