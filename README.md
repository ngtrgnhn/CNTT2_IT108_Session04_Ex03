<p align="center">
  <a href="https://ptit.edu.vn" target="_blank">
    <img src="./images/ptit.svg" alt="PTIT Logo" height="60" style="border-radius: 8px; padding: 4px; background: #ffffff;" />
  </a>
  &nbsp;&nbsp;&nbsp;&nbsp;
  <span style="font-size: 30px; font-weight: bold; color: #888;">✕</span>
  &nbsp;&nbsp;&nbsp;&nbsp;
  <a href="https://rikkei.edu.vn" target="_blank">
    <img src="./images/rikkei-logo.webp" alt="Rikkei Edu Logo" height="60" style="border-radius: 8px; padding: 4px; background: #ffffff;" />
  </a>
</p>
## **Phần 1: Mã nguồn PowerShell**

PowerShell

1.  Tạo cây thư mục lồng nhau cho dự án bằng đường dẫn tương đối

mkdir .\\Farm-Manager\\code\\app, .\\Farm-Manager\\database\\db, .\\Farm-Manager\\logs\\guides

- Ý nghĩa: mkdir (lệnh alias của New-Item cho thư mục) tạo cấu trúc cây thư mục theo yêu cầu; không cần dùng \-Recurse vì mkdir trong PowerShell hỗ trợ tạo chuỗi thư mục lồng nhau cùng lúc.

2.  Tạo sẵn 3 file rỗng (main.py, models.py, utils.py) trong thư mục app

New-Item .\\Farm-Manager\\code\\app\\main.py \-ItemType File \-Force; New-Item .\\Farm-Manager\\code\\app\\models.py \-ItemType File \-Force; New-Item .\\Farm-Manager\\code\\app\\utils.py \-ItemType File \-Force

- Ý nghĩa: New-Item tạo tệp tin mới với kiểu định dạng là File. Tham số \-Force giúp ghi đè hoặc bỏ qua cảnh báo nếu file đã tồn tại trước đó.

3.  Sao chép đệ quy toàn bộ thư mục logs sang bản lưu trữ logs-backup nằm ngang hàng

Copy-Item .\\Farm-Manager\\logs \-Destination .\\Farm-Manager\\logs-backup \-Recurse

- Ý nghĩa: Copy-Item thực hiện sao chép thư mục. Tham số \-Recurse là bắt buộc để sao chép đệ quy toàn bộ các thư mục con bên trong (như thư mục guides) cùng toàn bộ file, tránh bị bỏ sót hoặc chỉ copy vỏ thư mục rỗng (Bẫy 1).

## **Phần 2: Kiểm thử**

* **Lệnh kiểm tra và liệt kê cây thư mục vừa tạo:**  
* PowerShell

ls .\\Farm-Manager

- Hoặc: Get-ChildItem .\\Farm-Manager \-Recurse  
* **Giải thích việc sử dụng đường dẫn tương đối (`.\`):**  
  * Việc sử dụng đường dẫn tương đối (`.\`) giúp đảm bảo tính **linh hoạt và di động (portability)** cao (Bẫy 2).  
  * Câu lệnh có thể chạy chính xác ở bất kỳ thư mục làm việc nào (Desktop, Documents, v.v.) và trên bất kỳ phân vùng ổ đĩa nào mà người dùng đang thao tác, tránh tình trạng bị lỗi do gắn cứng (hard-code) tên ổ đĩa hoặc tên tài khoản người dùng cụ thể (như `C:\Users\Student\...`).

