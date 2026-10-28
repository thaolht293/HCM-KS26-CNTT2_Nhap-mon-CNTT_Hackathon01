# BÀI LÀM – HACKATHON 01

- **Mã đề:** 21
- **Họ tên:** LÊ HỒ THANH THẢO
- **Lớp:** HCM-KS26CNTT2
- **Link repository:** https://github.com/thaolht293/HCM-KS26-CNTT2_Nhap-mon-CNTT_Hackathon01
- **Hệ điều hành (Windows/macOS):** Windows

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
pwd
gci -recurse -force
mv ./mau_gui_qua.txt ./docs
mv ./logo_qua_luu_niem.png ./media
rm ./temp_293.tmp
cd ./logs 
gci; cd ../
```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

PS C:\Users\tisdo293\Downloads\starter-kit\starter-kit\qua-luu-niem-website> pwd

Path
----
C:\Users\tisdo293\Downloads\starter-kit\starter-kit\qua-luu-niem-website


PS C:\Users\tisdo293\Downloads\starter-kit\starter-kit\qua-luu-niem-website> gci -recurse


    Directory: C:\Users\tisdo293\Downloads\starter-kit\starter-kit\qua-luu-niem-website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        10/28/2026   1:48 PM                backup
d-----        10/28/2026   1:50 PM                data
d-----        10/28/2026   2:13 PM                docs
d-----        10/28/2026   1:51 PM                logs
d-----        10/28/2026   2:13 PM                media
-a----        10/27/2026   1:32 AM           6478 Logo_Qua_Luu_Niem.PNG
-a----        10/27/2026   1:32 AM             53 Mau_Goi_Qua.txt
-a----        10/27/2026   1:32 AM             22 temp_293.tmp


    Directory: C:\Users\tisdo293\Downloads\starter-kit\starter-kit\qua-luu-niem-website\data


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        10/27/2026   1:32 AM           6103 Don Qua Thang 12.xlsx


    Directory: C:\Users\tisdo293\Downloads\starter-kit\starter-kit\qua-luu-niem-website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        10/27/2026   1:32 AM           1040 Gift.log


PS C:\Users\tisdo293\Downloads\starter-kit\starter-kit\qua-luu-niem-website> mv ./mau_goi_qua.txt ./docs
PS C:\Users\tisdo293\Downloads\starter-kit\starter-kit\qua-luu-niem-website> mv ./logo_qua_luu_niem.png ./media
PS C:\Users\tisdo293\Downloads\starter-kit\starter-kit\qua-luu-niem-website> rm ./temp_293.tmp
PS C:\Users\tisdo293\Downloads\starter-kit\starter-kit\qua-luu-niem-website> cd ./logs
PS C:\Users\tisdo293\Downloads\starter-kit\starter-kit\qua-luu-niem-website\logs> gci; cd ../

```

## 4.3. Lọc log thủ công

### Lệnh đã chạy

```shell

PS C:\Users\tisdo293\Downloads\starter-kit\starter-kit\qua-luu-niem-website\logs> cd ../
PS C:\Users\tisdo293\Downloads\starter-kit\starter-kit\qua-luu-niem-website> get-content ./logs/Gift.log | select-string "ERROR" >> ./logs/daily_report.txt
PS C:\Users\tisdo293\Downloads\starter-kit\starter-kit\qua-luu-niem-website>

```

### 2 dòng lỗi đầu tiên trong daily_report.txt

```text

2026-12-28 07:38:36 [ERROR] Khong tim thay trang
/qua-tet (404)
2026-12-28 07:44:36 [ERROR] Het thoi gian cho (timeout)

```

## 4.4. Thao tác với tài liệu Markdown (README.md)

> README.md được chấm trực tiếp trên file `README.md` ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [x] Heading 1: tên dự án
- [x] Mô tả ngắn có cả **in đậm** và *in nghiêng*
- [x] Bảng `Thư mục | Nội dung`, ít nhất 3 dòng dữ liệu
- [x] Code block chứa lệnh PowerShell/Terminal liệt kê nội dung dự án
- [x] Task list ít nhất 2 công việc, có ít nhất 1 mục đã hoàn thành
- [x] Blockquote nhắc không upload `.env`

## 4.5. Chạy script auto_report (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell

# Script: auto_report.ps1
# Tac gia: THANH_THAO
# Ngay tao: 28/10/2026

new-item ./HOAN_THIEN.txt

$FileLogGoc    = "auto_report.ps1"      
$FileBaoCao    = "HOAN_THIEN.txt"   
$TuKhoa = "ERROR"            


Write-Host "Dang loc log..." 
Write-Output "=== BAO CAO LOI ===" > $FileBaoCao

Get-Content ./logs/daily_report.txt | Select-String $TuKhoa >> $FileBaoCao

Write-Host "hoan thanh"


```

### Kết quả hiển thị

```text

Dang loc log
hoan thanh

```

## 4.6. Đếm số dòng lỗi

### Lệnh

```shell
$sodong = (get-content .\HOAN_THIEN.txt).count

Write-Output "SỐ DÒNG LỖI:" >> .\HOAN_THIEN.txt
"$sodong" >> .\HOAN_THIEN.txt

```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```text
=== BAO CAO LOI ===
2026-12-28 07:38:36 [ERROR] Khong tim thay trang 
2026-12-28 07:44:36 [ERROR] Het thoi gian cho (timeout)
2026-12-28 07:56:36 [ERROR] Khong tim thay trang 
2026-12-28 08:05:36 [ERROR] Thanh toan bi tu choi
2026-12-28 08:08:36 [ERROR] Thanh toan bi tu choi
2026-12-28 08:17:36 [ERROR] Khong tim thay trang 
2026-12-28 08:23:36 [ERROR] Het thoi gian cho (timeout)
SỐ DÒNG LỖI:
7

```

## 4.7. Báo cáo tổng hợp

### Các lệnh đã chạy

```shell
Write-Output "=== BAO CAO LOI ===" >> ./logs/tong_hop.txt
Get-Content ./logs/Gift.log | Select-String "WARNING" >> ./logs/tong_hop.txt


```

### Nội dung file logs/tong_hop.txt

```text
=== BAO CAO LOI ===
2026-12-28 07:32:36 [WARNING] Anh mau qua dung luong lon
2026-12-28 08:02:36 [WARNING] Anh mau qua dung luong lon
2026-12-28 08:20:36 [WARNING] Don giao gap trong ngay

```

## 4.8. Excel

> Phần Excel được chấm trực tiếp trên file `data/don_qua_thang_12.xlsx`, không cần ghi vào đây.
