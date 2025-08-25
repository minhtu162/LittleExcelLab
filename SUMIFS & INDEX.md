## SUMIFS + INDEX
### Mục đích
Dùng SUMIFS để tính tổng dựa trên một hoặc nhiều điều kiện
Dùng INDEX để xác định cột được dùng để cộng


### Công thức mẫu
=SUMIFS(INDEX($A$1:$G$8,,MATCH(C$10,$1:$1,0)),$B$1:$B$8,$B11)
!(images/sumifs&index1.png)

### Giải thích
INDEX($A$1:$G$8,,MATCH(C$10,$1:$1,0))  
--> Xác định cột được dùng để cộng là cột có điều kiện 'MATCH(C$10,$1:$1,0)'

SUM(...)   
--> Tính tổng dựa trên điều kiện '$B$1:$B$8' có giá trị bằng '$B11', và cộng tổng ở cột được xác định bởi INDEX


### Ứng dụng thực tế
Giả sử bạn có bảng doanh số từ B2 đến B10, và bạn muốn tính tổng từ tháng đầu tiên đến tháng thứ n, trong đó n là giá trị trong ô A1:


### Lưu ý
Công thức này hoạt động tốt trong các báo cáo có độ dài thay đổi
