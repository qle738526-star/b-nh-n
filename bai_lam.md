# BÀI LÀM – HACKATHON 02

- **Mã đề:** 01
- **Họ tên:*Lê Quốc Minh Quân*
- **Lớp:*CNTT2*
- **Link repository:**
- **Hệ điều hành (Windows/macOS):*Window*

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
 cd C:\bonhan\starter-kit\san-bong-website
 pwd
 ls 
 ls -force
 mv
 mkdir
 cp
 rm
 cd ..


```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
  Directory: C:\bonhan\starter-kit\san-bong-website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/10/2026   9:48 PM                backup
d-----        11/10/2026   9:44 PM                data
d-----        11/10/2026   9:48 PM                docs
d-----        11/10/2026   9:43 PM                evidence
d-----        11/10/2026   9:44 PM                logs
d-----        11/10/2026   9:42 PM                web
-a----        11/10/2026   9:42 PM             76 .env
-a----        11/10/2026   9:42 PM           2409 bai_lam.md


    Directory: C:\bonhan\starter-kit\san-bong-website\backup


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        11/10/2026   9:42 PM           6074 dat_san_thang_10.xlsx


    Directory: C:\bonhan\starter-kit\san-bong-website\data


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        11/10/2026   9:42 PM           6074 dat_san_thang_10.xlsx


    Directory: C:\bonhan\starter-kit\san-bong-website\docs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        11/10/2026   9:42 PM            154 ghi_chu_ban_giao.txt


    Directory: C:\bonhan\starter-kit\san-bong-website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        11/10/2026   9:42 PM            956 access.log


    Directory: C:\bonhan\starter-kit\san-bong-website\web


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/10/2026   9:42 PM                images
-a----        11/10/2026   9:42 PM            590 app.js
-a----        11/10/2026   9:42 PM            529 index.html
-a----        11/10/2026   9:42 PM            460 style.css


    Directory: C:\bonhan\starter-kit\san-bong-website\web\images


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        11/10/2026   9:42 PM           3101 logo-san-bong.png

```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng status=500

```shell
 select-string "status=500" .\logs\access.log

```

### 2 dòng đầu tiên trong logs/loi_500.txt

```text
logs\access.log:8:2026-10-28 08:24:34 POST /api/thanh-toan status=500
logs\access.log:9:2026-10-28 08:28:45 POST /api/thanh-toan status=500

```

### b) Lệnh đếm số dòng status=404 và kết quả

```shell
(Get-Content .\logs\access.log | Select-String "status=404").count

```

```text
4

```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
 C:\bonhan\starter-kit\san-bong-website> @'
>> # Script: tong_hop.ps1
>> # Tac gia: Lê Quốc Minh Quân
>> # Ngay tao : 11/11/2026
>> Write-Host "Dang tao bao cao..."
>> "===BAO CAO SU CO WEBSITE ===" > logs/tong_hop.txt
>> Get-Content .\logs\access.log | Select-String "status=404" >> logs/tong_hop.txt
>>  Get-Content .\logs\access.log | Select-String "status=500" | Measure-Object >> logs/tong_hop.txt
>> Write-Host "Hoan Thanh!"
>> '@ | Set-Content tong_hop.ps1
PS C:\bonhan\starter-kit\san-bong-website> .\tong_hop.ps1
PS C:\bonhan\starter-kit\san-bong-website> set-executionpolicy -scope process -executionpolicy bypass
PS C:\bonhan\starter-kit\san-bong-website> .\tong_hop.ps1

```

### Nội dung file logs/tong_hop.txt

```text

===BAO CAO SU CO WEBSITE ===

2026-10-28 08:07:39 GET /tin-tuc status=404
2026-10-28 08:13:01 GET /dat-san-cu status=404
2026-10-28 08:34:07 GET /images/san-7.jpg status=404
2026-10-28 08:57:24 GET /khuyen-mai status=404




Count    : 6
Average  :
Sum      :
Maximum  :
Minimum  :
Property :




```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [X] README.md: Heading 1, mô tả có **in đậm** và *in nghiêng*, bảng, code block, task list, blockquote
- [X] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [X] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | --- | --- | --- |
| 1 | không hiển thị logo  |GET file:///C:/bonhan/starter-kit/san-bong-website/web/images/logo.png net::ERR_FILE_NOT_FOUND  |img src="images/logo-san-bong.png" alt="Logo" c  |
| 2 |không nhận diện được bảng giá  |app.js:18
 Uncaught ReferenceError: hienThiBangGia is not defined |sửa code app.js ở dong số 18 thành HienThiBangGiaSan  |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- **Context:*Đăng nhập vào ưewbsite và bật F12 lên và hiển thi thông báo lôi không hiênmr thi logo và bảng giá, đang sử dụng hệ điều hành window 11* 
- **Expected:*sửa được lỗi của web site để hiển thị logo và bảng giá để biewets thông tin* 
- **Actual:*Đang gặp lôi ở console và netwwork và chưa biết cách sửa lỗi* 
- **Log:** 

- GET file:///C:/bonhan/starter-kit/san-bong-website/web/images/logo.png net::ERR_FILE_NOT_FOUND
+ Uncaught ReferenceError: hienThiBangGia is not defined*

### Câu tìm kiếm Google

```text
Site: Stackoverflow.com "Uncaught ReferenceError: hienThiBangGia is not defined" -quangcao -crack

```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/dat_san_thang_10.xlsx`, không cần ghi vào đây.
