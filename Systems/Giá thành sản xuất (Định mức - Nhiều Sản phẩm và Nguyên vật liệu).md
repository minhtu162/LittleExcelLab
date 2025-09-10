## Giá thành sản xuất (Định mức - Nhiều Sản phẩm và Nguyên vật liệu)
**Hệ thống Excel hỗ trợ tính giá thành sản xuất theo định mức nguyên vật liệu cho nhiều sản phẩm**  
File này được xây dựng nhằm hỗ trợ các kế toán viên trong việc xác định giá thành sản phẩm một cách nhanh chóng, chính xác và dễ thao tác.  
*Lưu ý: Tất cả số liệu trong file chỉ mang tính minh họa, không phản ánh dữ liệu thực tế của bất kỳ doanh nghiệp nào.*

---

Tải file Excel: [Giá thành sản xuất.xlsx](https://github.com/minhtu162/ExcelLab/raw/main/Uploads/Giá%20thành%20sản%20xuất%20(định%20mức%2C%20nhiều%20SP%20và%20NVL).xlsx)

---

### 📋 Nội dung chính

File gồm các sheet sau:

| Sheet                  | Mô tả chức năng                                                                               |
|------------------------|-----------------------------------------------------------------------------------------------|
| `CTBH`                 | Sổ chi tiết bán hàng của 12 tháng, chi tiết sản phẩm, số lượng và số tiền của mỗi đơn hàng    |
| `ĐM`                   | Danh mục sản phẩm và định mức của mỗi sản phẩm                                                |
| `1521`                 | Chi tiết xuất nhập tồn của chi phí nguyên vật liệu của 12 tháng                               |
| `1523`                 | Chi tiết xuất nhập tồn của chi phí bao bì của 12 tháng                                        |
| `Tổng Chi Phí`         | Tổng hợp các chi phí sản xuất trong năm, gồm 621, 622, 627 và 154                             |
| `WIP` của 12 tháng     | Bảng tính chi phí sản xuất sản phẩm dở dang (có 12 sheet là tương đương 12 tháng)             |
| `STOCK` của 12 tháng   | Bảng xuất nhập tồn của từng sản phẩm trong tháng (có 12 sheet là tương đương 12 tháng)        |

---

### 🧭 Hướng dẫn sử dụng
1. Cập nhật thông tin bán hàng:
   Nhập chi tiết từng sản phẩm bán ra theo hóa đơn tại sheet CTBH.
   Kiểm tra số liệu tổng hợp tại ô M1 để đảm bảo dữ liệu chạy đúng.
2. Cập nhật danh mục và định mức sản phẩm
   Tại sheet ĐM, nhập danh mục sản phẩm và định mức nguyên vật liệu cho từng sản phẩm.
3. Cập nhật nguyên vật liệu đầu kỳ và nhập trong kỳ
   Tại sheet 1521, nhập thông tin NVL, số dư đầu kỳ và số lượng mua trong tháng (cột Nhập).
4. Cập nhật bao bì đầu kỳ, nhập và xuất trong kỳ
   Tại sheet 1523, nhập số liệu bao bì đầu kỳ, số lượng mua (cột Nhập) và số lượng sử dụng (cột Xuất).
5. Cập nhật chi phí sản xuất chung
   Tại sheet Tổng Chi Phí, nhập chi phí 622, 627 và chi phí 154 đầu kỳ.
   Kiểm tra số liệu chạy đúng tại từng sheet WIP.
6. Ghi nhận số dư đầu kỳ
   Tại sheet WIP T1: liệt kê chi tiết sản phẩm có số dư tài khoản 154 đầu kỳ.
   Tại sheet STOCK T1: cập nhật tồn kho đầu năm của từng sản phẩm.
7. Theo dõi sản phẩm dở dang tại các sheet WIP
   + Cột Nhập: ghi nhận số lượng sản phẩm dở dang phát sinh trong kỳ (đang trong quá trình sản xuất).
   + Cột Xuất: phản ánh số lượng sản phẩm dở dang đã hoàn thành trong kỳ và chuyển sang thành phẩm (sheet `STOCK`).
   + Cột Tồn cuối kỳ: thể hiện số lượng sản phẩm dở dang chưa hoàn thành, cần được chuyển tiếp sang tháng sau. Các bạn lưu ý không bỏ sót phần này ở WIP tháng tiếp theo.
8. Xác định chi phí nguyên vật liệu (621)
   Cột Nhập tại sheet WIP xác định số lượng sản phẩm dở dang phát sinh → từ đó tính số lượng NVL cần dùng.
   Số liệu NVL cần sẽ hiển thị tại sheet 1521, cột Xuất - SL cần.
   Điền số liệu thực tế vào cột Xuất - SL xuất để hệ thống tự động tính tổng chi phí NVL.
   Chi phí NVL sẽ được cập nhật vào sheet WIP, tạo ra chi phí 621.
   Kết hợp với các chi phí khác để xác định chi phí 154 và giá thành sản phẩm.
9. Theo dõi thành phẩm tại các sheet `STOCK`:
   + Cột Nhập: ghi nhận số lượng sản phẩm hoàn thành nhập kho trong kỳ.
   + Cột Xuất: phản ánh số lượng sản phẩm đã bán ra trong kỳ, căn cứ theo hóa đơn bán ra ở sheet `CTBH`.
   + Cột Tồn cuối kỳ: thể hiện số lượng thành phẩm còn lại trong kho, chưa được tiêu thụ, sẽ được tự động chuyển tiếp sang tháng sau.

---

### ⚙️ Cách vận hành
1. Tại sheet `WIP`:  
   + Cột chi phí 622, 627, Bao bì, CP khác:
     Tổng chi phí được lấy tự động từ sheet `Tổng Chi Phí`.  
     Chi phí của từng sản phẩm sẽ được phân bổ đều dựa trên số lượng sản phẩm được sản xuất trong tháng.  
   + Cột chi phí 621:
     Mỗi dòng tương ứng với một sản phẩm. Định mức NVL được thể hiện tại vùng bảng màu xám (kéo ngang sang phải để xem đầy đủ).
     Dựa trên số lượng sản phẩm dở dang phát sinh trong kỳ, hệ thống sẽ tính toán số lượng nguyên vật liệu cần dùng, cộng thêm 5% hao hụt.
     Sau khi tổng hợp đầy đủ sản phẩm dở dang, số liệu nguyên vật liệu cần dùng sẽ được xác định và tự động cập nhật tại sheet `1521`.
     Tại sheet `1521`, bạn có thể kiểm tra số lượng NVL thực tế sử dụng để tính ra tổng chi phí NVL trong tháng.
     Chi phí NVL sẽ được tự động cập nhật vào sheet `WIP`.
     Dựa trên tổng chi phí NVL ở dòng Tổng, hệ thống sẽ phân bổ chi phí cho từng sản phẩm theo tỷ lệ NVL sử dụng trong kỳ.
     Tổng chi phí NVL theo từng sản phẩm chính là chi phí 621.
2. Tại sheet `STOCK`:
   + Cột Nhập: số liệu được lấy tự động bằng cột Xuất sheet `WIP` - số lượng sản phẩm dở dang đã hoàn thành trong kỳ và chuyển sang thành phẩm.
   + Cột Xuất: số liệu được lấy tự động bằng số liệu ở sheet `CTBH`.

---

### 🐞 Lỗi có thể xảy ra
Cần kiểm tra lại số liệu ở sheet `Tổng Chi Phí` có chạy đúng chính xác qua các sheet `WIP`.

