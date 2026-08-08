# Hướng dẫn cài đặt — Phần mềm Kiểm tra Mô phỏng

Hướng dẫn này viết cho **người không biết lập trình**. Cứ làm tuần tự từ trên xuống, không bỏ bước nào.

Cài xong mất khoảng **45–60 phút** cho lần đầu.

---

## Cần chuẩn bị gì

| Thứ | Ghi chú |
|---|---|
| 1 máy tính làm **máy chủ** | Windows 10/11, còn trống ít nhất **10 GB**, có nối mạng LAN |
| Các máy tính làm **máy trạm** | Máy thí sinh ngồi thi. Bao nhiêu máy cũng được |
| Mạng LAN nối các máy | Dây mạng hoặc Wifi chung một mạng |
| 1 máy in | Cắm vào **máy chủ**. Máy trạm **không cần** máy in |
| Internet | **Chỉ máy chủ cần**, và chỉ lúc cài đặt / cập nhật |

> **Máy chủ** là máy đặt ở phòng giám thị, chứa dữ liệu và video.
> **Máy trạm** là máy thí sinh ngồi làm bài.

---

# PHẦN A — Cài trên MÁY CHỦ

## A1. Cài MySQL (nơi lưu dữ liệu)

1. Vào **https://dev.mysql.com/downloads/installer/**
2. Tải bản **Windows (x86, 32-bit), MSI Installer** cái **dung lượng lớn hơn** (khoảng 300 MB)
3. Bấm **No thanks, just start my download** nếu nó hỏi đăng ký
4. Chạy file vừa tải:
   - Chọn **Server only** → **Next** → **Execute** → chờ
   - Đến bước **Type and Networking**: để nguyên, **Next**
   - Đến bước **Authentication Method**: chọn dòng trên cùng (**Use Strong Password Encryption**) → **Next**
   - Đến bước **Accounts and Roles**: **gõ mật khẩu** vào 2 ô. **GHI MẬT KHẨU NÀY RA GIẤY**, lát nữa cần dùng
   - **Next** → **Next** → **Execute** → **Finish**

> ⚠️ Quên mật khẩu MySQL là phải cài lại từ đầu. Ghi ra giấy dán vào màn hình.

## A2. Cài .NET Runtime (nơi chạy phần mềm)

1. Vào **https://dotnet.microsoft.com/download/dotnet/8.0**
2. Ở cột **ASP.NET Core Runtime 8.0.x**, tìm dòng **Hosting Bundle** → bấm tải
3. Chạy file vừa tải → **Install** → **Close**

## A3. Giải nén phần mềm

1. Tải **`MayChu-v1.0.0.zip`** ở mục **Releases**
2. Bấm chuột phải vào file → **Extract All...** (Giải nén tất cả)
3. Ở ô đường dẫn, xoá hết rồi gõ đúng dòng này:

   ```
   C:\ThiMophong_MayChu
   ```

4. Bấm **Extract**

Xong bước này, mở **This PC → ổ C** phải thấy thư mục **ThiMophong_MayChu**.

## A4. Điền mật khẩu MySQL vào phần mềm

1. Vào thư mục `C:\ThiMophong_MayChu`
2. Tìm file tên **`appsettings.json`**
3. Bấm chuột phải → **Open with** → **Notepad**
4. Tìm dòng có chữ `DAT_MAT_KHAU_MYSQL_O_DAY`, ví dụ:

   ```
   "DefaultConnection": "Server=127.0.0.1;Port=3306;Database=tss;User=root;Password=DAT_MAT_KHAU_MYSQL_O_DAY;"
   ```

5. **Xoá đúng chữ** `DAT_MAT_KHAU_MYSQL_O_DAY`, thay bằng mật khẩu MySQL anh ghi ra giấy ở bước A1.

   Ví dụ mật khẩu là `abc123` thì thành:

   ```
   "DefaultConnection": "Server=127.0.0.1;Port=3306;Database=tss;User=root;Password=abc123;"
   ```

6. Nhấn **Ctrl + S** để lưu, đóng Notepad

> ⚠️ **Đừng xoá dấu chấm phẩy `;` và dấu nháy `"`**. Xoá nhầm là phần mềm không chạy được.

## A5. Tạo cơ sở dữ liệu

1. Tải file **`tss_khoitao.sql`** ở mục Releases, để vào `C:\ThiMophong_MayChu`
2. Bấm nút **Start** của Windows, gõ `cmd`
3. Bấm chuột phải vào **Command Prompt** → **Run as administrator** → **Yes**
4. Trong cửa sổ đen, gõ từng dòng, mỗi dòng xong nhấn **Enter**:

   ```
   cd C:\ThiMophong_MayChu
   ```

   ```
   "C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe" -u root -p < tss_khoitao.sql
   ```

5. Nó hỏi `Enter password:` → gõ mật khẩu MySQL rồi Enter
   (gõ vào **không hiện chữ gì cả**, đó là bình thường, cứ gõ rồi Enter)
6. Không báo lỗi gì là xong. Đóng cửa sổ đen.

## A6. Cài bộ video

Bộ video nặng **2,67 GB** nên không đi kèm bản cài (GitHub chỉ cho đính kèm tối đa 2 GB mỗi file).

1. Tải file **`Video-MoPhong-120-tinh-huong.zip`** theo đường dẫn ghi ở **đầu trang Releases**
2. Vào `C:\ThiMophong_MayChu`, bấm đúp vào file **`CaiDatVideo.bat`**
3. Hiện cửa sổ đen hỏi file zip → **kéo file zip vừa tải thả vào cửa sổ đen** → nhấn **Enter**
4. Chờ vài phút. Xong nó báo `So file video: 473`

> Nếu báo **ít hơn 400 file** nghĩa là file zip tải chưa xong. Tải lại rồi làm lại.

## A7. Khởi động máy chủ

1. Trong `C:\ThiMophong_MayChu`, bấm chuột phải vào **`1_CaiDatVaChayMayChu.bat`**
2. Chọn **Run as administrator** → **Yes**
3. Chờ chạy xong, nhấn phím bất kỳ để đóng

Máy chủ đã chạy. Trên màn hình Desktop có thêm biểu tượng **"May Chu Thi Mo Phong"** — lần sau chỉ cần bấm đúp vào đó.

## A8. Kiểm tra và đổi mật khẩu

1. Mở trình duyệt (Chrome / Edge), gõ:

   ```
   http://localhost:5212
   ```

2. Hiện màn hình đăng nhập → gõ:
   - Tên đăng nhập: **admin**
   - Mật khẩu: **admin**
3. Vào **Tài khoản** → **đổi mật khẩu ngay**

> ⚠️ Không đổi mật khẩu là ai trong phòng thi cũng vào sửa được điểm.

## A9. Ghi lại địa chỉ máy chủ

1. Bấm **Start**, gõ `cmd`, Enter
2. Gõ `ipconfig` rồi Enter
3. Tìm dòng **IPv4 Address**, ví dụ `192.168.1.15`
4. **Ghi con số này ra giấy** — lát nữa cài máy trạm cần dùng

---

# PHẦN B — Cài trên MÁY TRẠM

Làm y hệt trên **từng máy** thí sinh.

1. Tải **`MayTram-v1.0.0.zip`** ở mục Releases
2. Chuột phải → **Extract All...** → gõ đường dẫn:

   ```
   D:\ThiMoPhongClient
   ```

   (máy không có ổ D thì dùng `C:\ThiMoPhongClient`)
3. Vào thư mục đó, bấm đúp **`1_CaiDatMayTram.bat`**
4. Hiện cửa sổ hỏi IP máy chủ → gõ con số ghi ở bước **A9** (ví dụ `192.168.1.15`) → **Enter**
5. Xong. Trên Desktop có biểu tượng phần mềm thi

**Máy trạm không cần cài MySQL, không cần .NET, không cần video, không cần máy in.**

---

# PHẦN C — Cài máy in

Chỉ cắm máy in vào **máy chủ**. Biên bản in tự động tại đó.

1. Cắm máy in vào máy chủ, cài driver như bình thường
2. Vào **Settings → Bluetooth & devices → Printers & scanners**
3. Bấm vào máy in vừa cài → **Set as default** (đặt làm mặc định)

> ⚠️ **Không** để mặc định là *Microsoft Print to PDF*, *XPS Document Writer*, *OneNote* hay *Fax*.
> Đó là "máy in ảo", in ra sẽ hiện hộp thoại lưu file làm gián đoạn buổi thi.

---

# PHẦN D — Chạy một buổi thi

### Bước 1 — Nhập danh sách thí sinh

1. Trên máy chủ mở `http://localhost:5212`, đăng nhập
2. Vào **Khóa thi** → bấm nút xanh **Nhập XML sát hạch**
3. Chọn file XML của Cục Đường bộ (tên kiểu `52_52505_5250562029_OK.xml`)
4. Bấm **Nhập dữ liệu** → chờ khoảng **1 phút** (file 625 thí sinh)

Xong là có luôn khóa thi, đầy đủ thí sinh, số báo danh và ảnh chân dung. **Không phải gõ tay gì cả.**

Muốn sửa tên khóa hay ngày thi thì bấm nút **Sửa** ở dòng khóa đó.

### Bước 2 — Mở kỳ thi

Ở màn hình **Khóa thi**, cột **Trạng thái**, đổi ô chọn thành **Đang thi**.

> Chưa đổi thì máy trạm **không thấy khóa nào** để chọn.

### Bước 3 — Bật in tự động

1. Trong `C:\ThiMophong_MayChu`, bấm đúp **`MoManHinhGiamThi.bat`**
2. Nó tự mở trình duyệt → đăng nhập → vào **Khóa thi** → bấm **Học viên** của khóa đang thi
3. Góc phải thanh xanh có công tắc **Tự động in bài nộp** → bật lên
4. **Giữ nguyên cửa sổ này suốt buổi thi**

> ⚠️ Phải mở bằng `MoManHinhGiamThi.bat`. Mở trình duyệt kiểu thường thì mỗi bài nộp
> sẽ hiện hộp thoại in phải bấm tay hàng trăm lần.
>
> ⚠️ Đóng cửa sổ đó là **ngừng in**.

### Bước 4 — Thí sinh vào thi

Tại máy trạm, thí sinh:
1. Chọn kỳ sát hạch
2. Gõ **số báo danh** (in trên phiếu dự thi)
3. Bấm **Kiểm tra thông tin** → đối chiếu ảnh, họ tên, ngày sinh
4. Bấm **VÀO THI** → bắt đầu tính giờ 20 phút

Nộp bài xong, biên bản tự in ra ở máy chủ.

### Bước 5 — Xuất báo cáo

Vào **Báo cáo** → chọn khóa → xuất Excel hoặc in danh sách.

### Bước 6 — Đóng kỳ thi

Về **Khóa thi**, đổi trạng thái thành **Đã thi**.

---

# PHẦN E — Lỗi hay gặp

### Máy trạm báo "Không thể kết nối đến Máy chủ"

1. Máy chủ đã bật chưa? Bấm đúp biểu tượng **"May Chu Thi Mo Phong"** trên Desktop
2. IP có đúng không? Ở máy chủ gõ `ipconfig` xem lại, so với file `config.txt` trong thư mục máy trạm
3. Tường lửa: ở máy chủ chạy **`MoCongTuongLua_RunAsAdmin.bat`** bằng quyền Administrator
4. Hai máy có cùng mạng không? Thử ở máy trạm gõ `ping 192.168.1.15` (thay IP của anh)

### Màn hình thí sinh không thấy khóa thi nào

Khóa đang ở trạng thái **Chưa thi**. Vào **Khóa thi** đổi thành **Đang thi**.

### Video không chạy, màn hình đen

Video đặt sai chỗ. Đường dẫn đúng phải là:

```
C:\ThiMophong_MayChu\wwwroot\videos\CHUONG_I\1\index.m3u8
```

Nếu thấy thành `wwwroot\videos\videos\CHUONG_I\...` (chữ **videos** hai lần) là bị lồng thừa một cấp.
Xoá thư mục `videos` bên trong, chép các thư mục `CHUONG_I`…`CHUONG_VI` ra ngoài một cấp.

### Nộp bài mà không in ra

1. Cửa sổ mở bằng `MoManHinhGiamThi.bat` còn mở không?
2. Công tắc **Tự động in bài nộp** đã bật chưa?
3. Đang đứng ở đúng khóa thi đang diễn ra chứ?
4. Máy in mặc định của máy chủ có phải máy in giấy thật không?

### Phần mềm báo lỗi kết nối cơ sở dữ liệu

Mật khẩu trong `appsettings.json` sai. Làm lại bước **A4**.

Kiểm tra MySQL có chạy không: bấm **Start**, gõ `services.msc`, Enter, tìm dòng **MySQL80**,
trạng thái phải là **Running**. Nếu không, chuột phải → **Start**.

### Thí sinh bị kẹt "Đang thi" do máy trạm treo

Vào **Khóa thi → Học viên**, tick vào thí sinh đó, bấm nút **Reset**.

---

# PHẦN F — Cập nhật phiên bản mới

### Máy chủ

1. **Sao lưu trước:** bấm đúp **`SaoLuuCSDL.bat`**, gõ mật khẩu MySQL
2. Bấm đúp **`CapNhatMayChu.bat`** → **Yes**
3. Nó tự tải, tự sao lưu lần nữa, tự cài, tự bật lại

Bộ video, ảnh thí sinh, dữ liệu và mật khẩu **được giữ nguyên**.

> ⚠️ **Đừng cập nhật khi đang có buổi thi** — máy chủ sẽ dừng vài phút.

### Máy trạm

**Không phải làm gì.** Lúc mở phần mềm, máy trạm tự hỏi máy chủ, có bản mới thì hiện hộp thoại
"Cập nhật ngay bây giờ?" → bấm **Yes**.

> Máy trạm lấy bản mới **từ máy chủ qua mạng LAN**, không cần Internet.
>
> Đang có thí sinh làm bài thì bấm **No**, để cuối buổi cập nhật sau.

---

# PHẦN G — Việc nên làm định kỳ

| Khi nào | Làm gì |
|---|---|
| Sau mỗi buổi thi | Chạy **`SaoLuuCSDL.bat`** |
| Trước mỗi lần cập nhật | Chạy **`SaoLuuCSDL.bat`** |
| Mỗi tháng | Chép thư mục `C:\ThiMophong_MayChu\SaoLuu` ra ổ cứng ngoài |

> File sao lưu chứa **họ tên, ảnh, số CCCD của thí sinh**. Cất giữ nội bộ, không gửi qua mạng.

---

## Cần hỗ trợ

Ghi lại **đúng dòng chữ báo lỗi** trên màn hình rồi liên hệ đơn vị cung cấp phần mềm.
Chụp màn hình thì càng nhanh xử lý.
