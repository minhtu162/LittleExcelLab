## SỐ THỨ TỰ & COUNTIF
### 🎯 Mục đích
- Lập số thứ tự bằng mã quản lý và `COUNTIF`, ví dụ:
Mình có bảng tổng:  
![](https://github.com/minhtu162/ExcelLab/blob/main/Uploads/STT%26COUNTIF.1.png)  
Nhờ có STT mới, mình có được bảng chi tiết nhanh chỉ bằng cách nhập `Mã QL`:  
![](https://github.com/minhtu162/ExcelLab/blob/main/Uploads/STT%26COUNTIF.2.png)  

- Ngoài ra, nếu bạn muốn tìm hiểu cách làm STT để tổng hợp nhật ký chung thu chi của 2 KTV trở lên vào 1 bảng NKC tổng, bạn có thể tham khảo [Nhật ký chung (2 KTV trở lên cùng nhập)](https://github.com/minhtu162/LittleExcelLab/blob/main/Systems/Nh%E1%BA%ADt%20k%C3%BD%20chung%20(2%20KTV%20tr%E1%BB%9F%20l%C3%AAn%20c%C3%B9ng%20nh%E1%BA%ADp).md)

---

### 📐 Công thức mẫu
```excel
=SUMIFS(INDEX($A$1:$G$7 , , MATCH(C$9,$1:$1,0)), $B$1:$B$7, $B10)
```
![](https://github.com/minhtu162/ExcelLab/blob/main/Uploads/sumifs%26index1.png)

---

### 🧠 Giải thích
`INDEX($A$1:$G$7 , , MATCH(C$9,$1:$1,0))`  
--> Xác định cột được dùng để cộng là cột có điều kiện 'MATCH(C$9,$1:$1,0)'. Lưu ý không xác định dòng, chỉ xác định cột.

`SUM(...)`   
--> Tính tổng dựa trên điều kiện cột 'B1:B7' có giá trị bằng 'B10', và cộng tổng ở cột được xác định bởi INDEX

---

### 📈 Ứng dụng thực tế
Giả sử bạn có bảng lương từ A1 đến G7, và bạn muốn tính tổng lương theo 6421, 622, 6271 từ và theo tháng bạn muốn:
![](https://github.com/minhtu162/ExcelLab/blob/main/Uploads/sumifs%26index1.png)

---

### ⚠️ Lưu ý
Công thức này hoạt động tốt trong:
- Các báo cáo có độ dài thay đổi
- Các báo cáo tổng hợp lương theo các tháng trong 1 sheet (có thể tổng hợp yếu tố khác như thuế TNCN, BHXH...)
