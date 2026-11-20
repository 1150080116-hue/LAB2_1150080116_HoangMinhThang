# BÁO CÁO BÀI THỰC HÀNH LAB 2 - MÃ HÓA ĐỐI XỨNG HIỆN ĐẠI

## THÔNG TIN SINH VIÊN
- **Họ và tên:** Hoàng Minh Thắng
- **Mã số sinh viên (MSSV):** 1150080116
- **Lớp:** 11_ĐH_THMT
- **Môn học:** An toàn và bảo mật hệ thống thông tin (ATVBMHTTT)
- **Bài thực hành:** Bài 2 – Mã hóa đối xứng hiện đại (DES, 3DES, AES, RC4, Twofish, AES-CTR, Python AES-CBC, SQL Server)

---

## HƯỚNG DẪN CHẠY CHƯƠNG TRÌNH

### 1. Chuẩn bị Cơ sở dữ liệu SQL Server (Bắt buộc trước khi chạy)
1. Mở **SQL Server Management Studio (SSMS)** và đăng nhập vào SQL Server cục bộ (`localhost` hoặc tên máy).
2. Mở tệp `02_SQL/01_Tao_CSDL.sql` $\rightarrow$ Nhấn **Execute** (hoặc phím `F5`) để khởi tạo CSDL `LAB2_MaHoaHienDai`, bảng `dbo.users` và bảng `dbo.crypto_history`.
3. Mở tệp `02_SQL/02_Tao_Tai_Khoan_SQL.sql` $\rightarrow$ Nhấn **Execute** (`F5`) để tạo tài khoản SQL `lab2_user` (Mật khẩu: `LabUser@2026`) và cấp quyền `db_owner`.
4. Mở tệp `02_SQL/03_Kiem_Tra_Du_Lieu.sql` $\rightarrow$ Dùng để truy vấn đối soát dữ liệu lịch sử thao tác sau khi chạy chương trình.

---

### 2. Hướng dẫn mở và chạy Project Java trên NetBeans
1. Khởi động **Apache NetBeans IDE**.
2. Trên thanh công cụ, chọn **File** $\rightarrow$ **Open Project...**
3. Điều hướng tới thư mục:
   ```
   SUBMISSION_PACKAGE/01_Java_NetBeans/LAB2_MaHoaHienDai
   ```
   *(NetBeans sẽ tự động nhận diện dự án có biểu tượng Maven).*
4. Nhấn **Open Project**.
5. Trong cửa sổ **Projects**, nhấp chuột phải vào `LAB2_MaHoaHienDai` $\rightarrow$ chọn **Clean and Build** (phím tắt **`Shift + F11`**). NetBeans sẽ tự nạp 2 thư viện từ Maven:
   - `mssql-jdbc:12.8.1.jre11` (Kết nối SQL Server)
   - `bcprov-jdk18on:1.78.1` (Thư viện mật mã BouncyCastle cho Twofish)
6. **Cách khởi chạy ứng dụng:**
   - **Cách 1 (Chạy Menu tổng hợp toàn bộ bài):**
     - Nhấp chuột phải vào tên project $\rightarrow$ chọn **Run** (phím **`F6`**).
     - Cửa sổ Menu **LAB 2 - MÃ HÓA ĐỐI XỨNG HIỆN ĐẠI** sẽ hiển thị. Nhấp chuột vào các nút tương ứng để mở form:
       - `2.1 DES`
       - `2.2 TripleDES`
       - `2.3 AES + Login`
       - `2.4 RC4`
       - `2.5 Twofish`
       - `2.6 Nâng cao - AES-CTR`
       - `Kết nối SQL Server`
       - `Xem lịch sử`
   - **Cách 2 (Chạy từng form giao diện riêng lẻ):**
     - Mở rộng: `Source Packages` $\rightarrow$ `week_02`.
     - Nhấp chuột phải vào file form cần mở (ví dụ: `frm_AES.java`, `frm_DES.java`, `frm_RC4.java`, v.v.) $\rightarrow$ chọn **Run File** (phím tắt **`Shift + F6`**).

---

### 3. Hướng dẫn chạy chương trình Python (Bài nâng cao 02 AES-CBC)
1. Cài đặt thư viện mật mã nếu máy chưa có:
   ```bash
   pip install cryptography
   ```
2. Mở Command Prompt hoặc PowerShell tại thư mục:
   ```
   SUBMISSION_PACKAGE/03_Python/
   ```
3. **Khởi chạy ứng dụng đồ họa Tkinter:**
   ```bash
   python aes_cbc_gui.py
   ```
   *(Giao diện đồ họa hiển thị cho phép tạo khóa ngẫu nhiên, tạo vector khởi tạo IV, mã hóa và giải mã văn bản hoặc tệp tin).*
4. **Chạy kiểm thử tự động (Self-test CLI):**
   ```bash
   python aes_cbc_gui.py --self-test
   ```
   Kết quả trả về: `SELF-TEST OK: 4 thông điệp mã hóa/giải mã đúng, sai khóa bị phát hiện.`

---

