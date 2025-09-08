## SỐ THỨ TỰ & COUNTIF
### 🎯 Mục đích
- Lập số thứ tự bằng mã quản lý và `COUNTIF`, ví dụ:
Mình có bảng tổng:  
![](https://github.com/minhtu162/ExcelLab/blob/main/Uploads/STT%26COUNTIF.1.png)  

Nhờ có STT mới, mình có được bảng chi tiết nhanh chỉ bằng cách nhập `Mã QL`:  
![](https://github.com/minhtu162/ExcelLab/blob/main/Uploads/STT%26COUNTIF.2.png)  

- Ngoài ra, nếu bạn muốn tìm hiểu cách làm STT để tổng hợp nhật ký chung thu chi của 2 KTV trở lên vào 1 bảng NKC tổng, bạn có thể tham khảo [Nhật ký chung (2 KTV trở lên cùng nhập)](https://github.com/minhtu162/LittleExcelLab/blob/main/Systems/Nh%E1%BA%ADt%20k%C3%BD%20chung%20(2%20KTV%20tr%E1%BB%9F%20l%C3%AAn%20c%C3%B9ng%20nh%E1%BA%ADp).md)

---

### 📐 Công thức mẫu và Giải thích:
- Ở bảng tổng, mình tạo STT mới bằng `Mã QL` dùng công thức Excel như sau:
Mình lấy ô `Mã QL`, kết hợp với dấu chấm và `COUNTIF`.
Lưu ý `COUNTIF` dải ô sẽ cố định ở ô đầu tiên, khi đó lúc mình kéo công thức xuống thì dải ô sẽ được kéo xuống dần.  
```excel
=E2 & "." & COUNTIF($E$2:E2, E2)
```  
- Ở bảng chi tiết, mình thiết lập STT bằng công thức Excel như sau:
Chuẩn bị sẵn ô `Mã QL` để mình có thể nhập mã bất kỳ mà mình muốn xem chi tiết.
Sau đó, ở ô STT, mình kết hợp với ô `Mã QL` (cố định) và hàm `ROW`
```excel
= $B$1 & "." & ROW()-2
```

---

### 📈 Ứng dụng thực tế
Từ bảng tổng, bạn có thể làm ra từng bảng chi tiết theo `Mã QL` mà bạn muốn:
![](https://github.com/minhtu162/ExcelLab/blob/main/Uploads/STT%26COUNTIF.2.png)
![](https://github.com/minhtu162/ExcelLab/blob/main/Uploads/STT%26COUNTIF.3.png)
![](https://github.com/minhtu162/ExcelLab/blob/main/Uploads/STT%26COUNTIF.4.png)

---

### ⚠️ Lưu ý
Không có.
