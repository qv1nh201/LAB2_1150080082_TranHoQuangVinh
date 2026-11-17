# LAB 2: MÃ HÓA ĐỐI XỨNG HIỆN ĐẠI
**Học phần:** An toàn và Bảo mật thông tin

## 1. Thông tin sinh viên
* **Họ và tên:** Trần Hồ Quang Vinh
* **MSSV:** 1150080082
* **Khoa:** Công nghệ thông tin - Trường Đại học Tài nguyên và Môi trường TP.HCM

---

## 2. Cấu trúc kho lưu trữ (Repository)
* `LAB2_MaHoaHienDai/`: Mã nguồn project Java Maven trên Apache NetBeans (bao gồm `pom.xml`, các lớp xử lý mã hóa `.java` và các tệp thiết kế giao diện `.form` trong package `week_02`).
* `LAB2_Python/`: Chương trình mã hóa nâng cao AES-256-CBC viết bằng ngôn ngữ Python (`aes_cbc_gui.py` sử dụng giao diện Tkinter).
* `SQL/`: Các tệp kịch bản khởi tạo CSDL (`01_Tao_CSDL.sql`), tạo tài khoản kết nối (`02_Tao_Tai_Khoan_SQL.sql`) và truy vấn kiểm tra dữ liệu (`03_Kiem_Tra_Du_Lieu.sql`).
* `HinhAnh_KetQua/`: Hình ảnh chụp màn hình kết quả chạy kiểm thử các bài thực hành từ 2.1 đến 2.6.

---

## 3. Hướng dẫn cài đặt và chạy chương trình

### Bước 1: Chuẩn bị Cơ sở dữ liệu (SQL Server)
1. Đảm bảo dịch vụ **SQL Server (SQLEXPRESS)** đang chạy, đã bật giao thức **TCP/IP** với cổng tĩnh **14333** và chế độ đăng nhập **SQL Server and Windows Authentication mode**.
2. Mở **SQL Server Management Studio (SSMS)**, chạy lần lượt 2 tệp:
   * `01_Tao_CSDL.sql`: Tạo CSDL `LAB2_MaHoaHienDai` cùng 2 bảng `dbo.app_users` và `dbo.crypto_history`.
   * `02_Tao_Tai_Khoan_SQL.sql`: Tạo tài khoản `lab2_user` với mật khẩu mặc định là `LabUser@2026`.

### Bước 2: Chạy ứng dụng Java trên Apache NetBeans (Bài 2.1 -> 2.6 Bài 1)
1. Yêu cầu môi trường: **JDK 17+** và **Apache NetBeans 20+**.
2. Mở NetBeans $\rightarrow$ chọn **File $\rightarrow$ Open Project...** và trỏ tới thư mục `LAB2_MaHoaHienDai`.
3. Nhấp chuột phải vào project $\rightarrow$ chọn **Clean and Build (Shift + F11)** để Maven tải thư viện `mssql-jdbc` và `bcprov-jdk18on` (BouncyCastle).
4. Nhấn **F6 (Run Project)** để khởi chạy cửa sổ chính `week_02.frm_Menu`.
5. Trên giao diện Menu chính:
   * Bấm **Kết nối SQL Server** $\rightarrow$ Nhập mật khẩu `LabUser@2026` $\rightarrow$ bấm **Test Connection** để kích hoạt lưu lịch sử thao tác.
   * Chọn lần lượt các nút **2.1 DES**, **2.2 TripleDES**, **2.3 AES + Login**, **2.4 RC4**, **2.5 Twofish**, **2.6 Nâng cao - AES-CTR** để thực hiện mã hóa/giải mã và kiểm tra tại mục **Xem lịch sử**.

### Bước 3: Chạy chương trình Python AES-CBC (Bài 2.6 Bài 2)
1. Yêu cầu môi trường: **Python 3.10+**.
2. Mở Command Prompt / Terminal, cài đặt thư viện mã hóa (chỉ cần chạy lần đầu):
   ```bash
   py -m pip install cryptography