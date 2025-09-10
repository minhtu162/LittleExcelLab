## Nhật ký chung (2 KT trở lên cùng nhập)
**Hệ thống quản lý nhật ký chung với kế toán viên từ 2 người trở lên (trong file mẫu sẽ làm 3 KTV)**  
File Excel này được thiết kế để hỗ trợ các kế toán viên nhập liệu riêng ở mỗi sheet, và có sheet tổng hợp nhật ký chung của các kế toán viên, tiện cho việc quản lý và kiểm tra dòng tiền.  

---

Tải file Excel: [Nhật ký chung (2 KTV trở lên).xlsx](https://github.com/minhtu162/ExcelLab/raw/main/Uploads/Nhật%20ký%20chung%20(2%20KT%20trở%20lên%20cùng%20nhập).xlsx)

---

### 📋 Nội dung chính

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

### 🧭 Hướng dẫn sử dụng
1. **Nhập dữ liệu ở mỗi sheet NV1, NV2, NV3:** từng bạn KTV nhập thu chi vào sheet của mình.  
   Lưu ý có thể chi tiết thông tin nhiều hơn, tùy Quản lý mong muốn.  
2. **Kiểm tra sheet `Nhật ký chung`:** Liệu ở sheet `Nhật ký chung` có hiện đầy đủ từ 3 sheet của KTV hay không, mình kiểm tra ô A1, TRUE là đúng, FALSE là sai

---

### ⚙️ Cách vận hành
1. **Cách đánh số thứ tự từng dòng trong nhật ký chung của NV:**
   - Đánh theo số thập phân: 1.01, 1.02, 2.01, 2.02
   - Trong đó, số nguyên được tính theo RANK của ngày tháng trong các ngày tháng đã nhập của 3 KTV; Số thập phân được tính bằng đếm số lần ngày tháng đó lặp lại của 3 KTV. Ví dụ:

| Ngày tháng có thu chi của các KTV  | Thứ tự    |
|------------------------------------|-----------|
| 01/11/2024 (thu tiền hàng 1)       | 1.01      |
| 01/11/2024 (thu tiền hàng 2)       | 1.02      |
| 10/11/2024 (chi tiền hàng 1)       | 2.01      |
| 10/11/2024 (chi tiền hàng 2)       | 2.02      |

   - Để tính số nguyên, đầu tiên mình cần liệt kê các ngày tháng đã nhập của 3 KTV, mình dùng hàm excel `UNIQUE` và `FILTER`    

Liệt kê các ngày tháng của NV1:
```Excel
=UNIQUE(FILTER('NV1'!C6:C1000, 'NV1'!C6:C1000 > 0))
```  
Liệt kê các ngày tháng của NV2:
```Excel
=UNIQUE(FILTER('NV2'!C6:C1000, (ISNA(MATCH('NV2'!C6:C1000, A6:A1000, 0))) * ('NV2'!C6:C1000 > 0)))
```  
Liệt kê các ngày tháng của NV3:
```Excel
=UNIQUE(FILTER('NV3'!C6:C1000, (ISNA(MATCH('NV3'!C6:C1000, B6:B1000, 0))) * (ISNA(MATCH('NV3'!C6:C1000, A6:A1000, 0)))*('NV3'!C6:C1000 > 0)))
```
   - Mình xác định số nguyên bằng hàm `RANK` như sau  

Của NV1, NV2, và NV3:
```Excel
=RANK(C6, Note!A:C, 1)
```  
   - Tiếp theo, xác định số thập phân bằng `COUNTIF`, ưu tiên thứ tự của NV1 trước, rồi đến NV2, và NV3. Mình dùng hàm:  

Xác định thứ tự bằng số thập phân NV1:
```Excel
=+0.01 * COUNTIF($C$6:C6, C6)
```  
Xác định thứ tự bằng số thập phân NV2:
```Excel
=+0.01 * (COUNTIF($C$6:C6, C6) + COUNTIF('NV1'!$C:$C, C6))
```  
Xác định thứ tự bằng số thập phân NV3:
```Excel
=+0.01 * (COUNTIF($C$6:C6, C6) + COUNTIF('NV1'!$C:$C, C6) + COUNTIF('NV2'!$C:$C, C6))
```

2. **Cách đánh số thứ tự từng dòng trong sheet `nhật ký chung` tổng:**
- STT dòng đầu tiên là số 1.01, từ dòng 2 trở đi, mình áp dụng công thức `IF`
- Có 3 trường hợp chính:
  + Nếu STT tiếp theo chỉ thay đổi số thập phân -> KQ cộng thêm 0.01
  + Nếu STT tiếp theo thay đổi số nguyên -> KQ cộng thêm 1
  + Nếu STT tiếp theo không có -> KQ là "-"
- Mình dùng hàm Excel sau:  
```Excel
=IF(COUNTIF('NV1'!A:A, A6+0.01) = 1, ROUND(A6+0.01, 2),
 IF(COUNTIF('NV2'!A:A, A6+0.01) = 1, ROUND(A6+0.01, 2),
 IF(COUNTIF('NV3'!A:A, A6+0.01) = 1, ROUND(A6+0.01, 2),
 IF(COUNTIF('NV1'!A:A, INT(A6)+1.01) = 1, ROUND(INT(A6)+1.01, 2),
 IF(COUNTIF('NV2'!A:A, INT(A6)+1.01) = 1, ROUND(INT(A6)+1.01, 2),
 IF(COUNTIF('NV3'!A:A, INT(A6)+1.01) = 1, ROUND(INT(A6)+1.01, 2), "-"))))))
```

3. **Cách kiểm tra TRUE / FALSE trong sheet `nhật ký chung` tổng:**
Công thức kiểm tra liệu sheet `nhật ký chung` tổng có nhập đủ số liệu từ 3 KTV hay không: Mình dùng `COUNTIF` để đếm số dòng hiện có trong sheet `Nhật ký chung`; cộng với lại số dư hiện có và so sánh với tổng số dòng và số dư từ 3 bảng còn lại
```Excel
= COUNTIF(D6:D50,">""") + G4 = COUNTIF('NV1'!D6:D998,">""") + COUNTIF('NV2'!D6:D1000,">""") + COUNTIF('NV3'!D6:D1000,">""") + 'NV1'!G4 + 'NV2'!G4 + 'NV3'!G4
```  

---

### 🐞 Lỗi có thể xảy ra
Hiện tại chưa có.
