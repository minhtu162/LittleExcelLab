## GGForms & Doanh thu (đơn giản)
**Hệ thống quản lý đơn hàng và doanh thu nội bộ**  
File Excel này được thiết kế để hỗ trợ người bán hàng photo nhập liệu, kiểm tra phiếu giao hàng, và tổng hợp doanh thu theo từng khu vực và quản lý.  

---

Tải file Excel: [GGForms và Doanh thu.xlsx](https://github.com/minhtu162/ExcelLab/raw/main/Uploads/GGForms%20%26%20Doanh%20thu%20(%C4%91%C6%A1n%20gi%E1%BA%A3n).xlsx)

---

### Nội dung chính

File gồm các sheet sau:

| Sheet         | Mô tả chức năng                                  |
|---------------|--------------------------------------------------|
| `README`      | Ghi chú và hướng dẫn sử dụng hệ thống             |
| `Google Forms`   | Nhập liệu đơn hàng theo từng khu vực và QL       |
| `Doanh thu`   | Tổng hợp doanh thu theo tháng, khu vực, QL       |
| `Phiếu giao hàng`  | Mẫu phiếu giao hàng để đối chiếu và kiểm tra (được in ra làm 2 tờ cùng 1 lúc để tránh sự gian lận)     |

Nên dùng giới hạn chỉnh sửa ở các sheet, trừ 3 cột ở sheet `Google Forms` và 1 ô ở `Phiếu giao hàng`

---

### Hướng dẫn sử dụng
**1. Nhập dữ liệu** vào sheet `Google Forms` theo định dạng:   
   Tên mặt hàng / Đơn giá / Số lượng   
   Lưu ý khi nhập số tiền thì dùng dấu phẩy để đánh dấu hàng nghìn.  
**2. Kiểm tra phiếu giao hàng** trong sheet `Phiếu giao hàng` để đối chiếu thực tế.  
**3. Xem tổng hợp doanh thu** theo từng khu vực và quản lý tại sheet `Doanh thu`.  
**4. Ghi chú quan trọng**:  
   - Các bạn TVV khi nhận ĐC nhớ kiểm tra lại với phiếu giao hàng  
   - Nếu có sai sót, vui lòng báo lại trong ngày để được xử lý kịp thời

---

### Lỗi có thể xảy ra
- Mỗi lần nhập mới 1 Form, cột "Thứ tự" ở sheet `Google Forms` sẽ bị lỗi.  
  Lý do vì dòng nhập mới đó không có sẵn công thức như những dòng trên.  
  -> Vì thế cần copy lại.
