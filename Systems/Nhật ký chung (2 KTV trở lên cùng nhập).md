## Nhật ký chung (2 KT trở lên cùng nhập)
**Hệ thống quản lý nhật ký chung với kế toán viên từ 2 người trở lên (trong file mẫu sẽ làm 3 KTV)**  
File Excel này được thiết kế để hỗ trợ các kế toán viên nhập liệu riêng ở mỗi sheet, và có sheet tổng hợp nhật ký chung của các kế toán viên, tiện cho việc quản lý và kiểm tra dòng tiền.  

---

Tải file Excel: [NhậtKýChung(2KTVtrởlên).xlsx](https://github.com/minhtu162/ExcelLab/raw/main/Uploads/Nhật%20ký%20chung%20(2%20KT%20trở%20lên%20cùng%20nhập).xlsx)

---

### Nội dung chính

File gồm các sheet sau:

| Sheet          | Mô tả chức năng                                  |
|----------------|--------------------------------------------------|
| `Nhật ký chung`| Tổng hợp thu chi từ nhật ký chung của 3 KTV      |
| `NV1`          | Nhật ký thu chi của KTV 1                        |
| `NV2`          | Nhật ký thu chi của KTV 2                        |
| `NV3`          | Nhật ký thu chi của KTV 3                        |
| `Note`         | Ghi chú linh tinh để hệ thống được vận hành      |

Nên dùng giới hạn chỉnh sửa ở các sheet để tránh KTV này nhập vào sheet của KTV khác

---

### Hướng dẫn sử dụng
1. **Nhập dữ liệu ở mỗi sheet NV1, NV2, NV3** từng bạn KTV nhập thu chi vào sheet của mình.  
   Lưu ý có thể chi tiết thông tin nhiều hơn, tùy Quản lý mong muốn.
3. **Kiểm tra sheet Nhật ký chung** ô A1, True là đúng, False là sai

---

### Cách vận hành
1. **Cách đánh số thứ tự từng dòng trong nhật ký chung của NV:**
   - Đánh theo số thập phân: 1.01, 1.02, 2.01, 2.02
   - Trong đó, số nguyên được tính theo RANK của ngày tháng trong các ngày tháng đã nhập của 3 KTV. Để liệt kê các ngày tháng đã nhập của 3 KTV, mình dùng hàm excel
Lấy các ngày tháng của NV1:
```Excel
=UNIQUE(FILTER('NV1'!C6:C1000,'NV1'!C6:C1000>0))```  
Lấy các ngày tháng của NV2:
```Excel
=UNIQUE(FILTER('NV2'!C6:C1000,(ISNA(MATCH('NV2'!C6:C1000,A6:A1000,0)))*('NV2'!C6:C1000>0)))```  
Lấy các ngày tháng của NV3:
```Excel
=UNIQUE(FILTER('NV3'!C6:C1000,(ISNA(MATCH('NV3'!C6:C1000,B6:B1000,0)))*(ISNA(MATCH('NV3'!C6:C1000,A6:A1000,0)))*('NV3'!C6:C1000>0)))```  

---

### Lỗi có thể xảy ra
Hiện tại chưa có.
