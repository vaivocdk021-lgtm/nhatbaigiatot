# Web Nhật Bãi Giá Tốt (nhatbaigiatot.com) — hướng dẫn cho Claude

Luôn trả lời bằng tiếng Việt, câu ngắn, dễ hiểu. Chủ web là anh Hiếu (cửa hàng 32/33 phố Lam Sơn, An Biên, Hải Phòng; Zalo/điện thoại 0936 830 947). Anh Hiếu không rành máy tính: Claude tự làm trọn, chỉ hỏi khi cần thông tin (ảnh, tên, giá, số lượng).

## Web chạy thế nào
- Kho này đưa thẳng lên GitHub Pages, nhánh `main`, gốc kho. Đẩy lên `main` khoảng 1–2 phút sau là web đổi.
- Nếu phiên làm việc bắt buộc đẩy lên nhánh khác: tạo pull request vào `main` rồi chỉ anh Hiếu bấm nút xanh "Merge pull request" và "Confirm merge" (giải thích bằng tiếng Việt vì nút là chữ tiếng Anh).
- File `CNAME` (ghi `nhatbaigiatot.com`) PHẢI giữ nguyên, xoá là web mất tên miền.
- Cả trang nằm trong MỘT file `index.html` (chữ, kiểu dáng, JS). Ảnh, clip là file riêng cùng thư mục gốc.
- File `index.html` này trước đây được dựng bằng máy khác; từ khi giao cho anh Hiếu thì sửa thẳng `index.html`, không còn bước dựng.

## Giá lấy từ bảng Google (không cần sửa web)
- Khách mở trang, JS cuối `index.html` (biến `BANG`) tải bảng giá Google bản xuất bản CSV. Cột: 0 Mã (vd `noi_22`), 2 Giá, 3 Mới/Cũ, 4 Còn/Hết, 5 Điện áp.
- Anh Hiếu sửa Giá / Còn-Hết / Mới-Cũ / Điện áp trong bảng là web tự đổi. Nồi chọn "Hết" tự xuống cuối, ảnh mờ, nút "Đặt trước".
- Chỉ phải sửa web khi THÊM / BỚT sản phẩm, đổi ảnh, đổi chữ, đổi bố cục.
- Sản phẩm mới phải thêm cả dòng trong bảng Google, cùng mã với web.

## Bố cục trang (thứ tự đã chốt, giữ nguyên)
thanh đầu → hàng "Nồi đang bán" tự chạy (`#ds`, JS chép nguyên ô lưới nồi, nồi Hết không vào) → Phụ kiện (`#phu-kien`, lưới `#luoi-pk`) → lưới tất cả nồi (`#tat-ca`, `#luoi`) → Video (`#video`) → cam kết, cách đặt, câu hỏi thường gặp → trang chi tiết từng nồi (`#ct`, mở khi bấm ô nồi) → liên hệ.

## Thêm một phụ kiện (linh kiện, nắp vung...)
1. Ảnh: vuông, khoảng 800×800, jpg, dưới ~150 KB, đặt tên `pk_06.jpg`, `pk_07.jpg`... (đang có pk_01 → pk_05).
2. Chép một khối `<li class="o o-pk" data-id="pk_..">...</li>` có sẵn trong `#luoi-pk`, đổi: `data-id`, tên ảnh (2 chỗ `data-to` và `src`), `alt`, `aria-label`, hãng (`.hang`), tên (`h3`), giá (`.gia`, dạng `80.000đ`), và chữ trong link Messenger `m.me/...?text=` (mã hoá URL).
3. Thứ tự: món mới lên đầu, trừ khi anh Hiếu bảo khác.

## Thêm một nồi
Một nồi có mặt ở 4 chỗ, phải sửa đủ cả 4:
1. Ô trong lưới `#luoi` (`<li class="o" data-id="noi_xx" data-c="1L" data-h="Toshiba">`): ảnh nhỏ `noi_xx_nho.webp`, hãng, tên, nhãn điện áp `.dien`, ô `.chips` (dung tích, đời), giá, link Messenger.
2. `var NOI = [...]`: một đối tượng `{"id","hang","ten","co","ma","doi","gia","reel","nhan","diem","tinh","phu",...}` (chép một nồi có sẵn rồi đổi).
3. `var ANH = {...}`: `"noi_xx": ["noi_xx.webp","noi_xx_0.webp","noi_xx_1.webp","noi_xx_2.webp"]` (ảnh chính + 3 ảnh phụ, khoảng 900px, webp).
4. `var CLIP = {...}`: `"noi_xx": "noi_xx.mp4"` (clip ngắn ~7 giây, nhẹ, không tiếng; không có thì bỏ).
Mã nồi mới: lấy số tiếp theo chưa dùng (đã dùng tới `noi_27`).

## Điều đã chốt, KHÔNG làm
- KHÔNG đặt mã QR (sợ bị đổi thành mã lừa đảo).
- KHÔNG dùng ảnh có tay người che sản phẩm.
- KHÔNG chữ "nấu thử", "test cơm", "cọc" (cửa hàng không nấu thử). Không tự nghĩ số sao, số đã bán, lời khen chung chung.
- Giá chỉ ghi theo anh Hiếu báo đúng chiếc đó; chưa có giá thì để nút nhắn hỏi.
- Không bán lẻ lòng nồi: câu hỏi thường gặp giữ "chỉ bán nguyên nồi".
- Trước khi thêm, so mã in trên mặt nồi với nồi đã có: trùng thì không thêm, báo anh Hiếu.

## Kiểm trước khi đẩy lên (bắt buộc)
- Mở trang ở 2 cỡ: máy tính (~1366 rộng) và điện thoại (~390 rộng). Kiểm: không tràn ngang, các khối thẳng mép, ảnh không hỏng, nút gọi nổi không che chữ, hàng "Nồi đang bán" vẫn chạy, bấm ô nồi mở được trang chi tiết.
- Mọi file mà `index.html` nhắc tới phải có trong kho (thêm ảnh mới thì đẩy cả ảnh, không chỉ `index.html`).
- Đẩy lên xong, mở https://nhatbaigiatot.com thật (thêm `?v=` số bất kỳ để tránh bản cũ) xem lại, rồi mới báo anh Hiếu là xong.
- Mở trang bằng file trong máy (`file://`) thì bảng Google bị chặn, trang hiện giá dựng sẵn: bình thường, không phải lỗi.

## Báo lại anh Hiếu
Nói ngắn: đã đổi gì, xem ở đâu (link), còn chỗ nào chưa chắc. Không dùng chữ tiếng Anh khó hiểu.
