# Mini guideline — bài làm cá nhân

> Điền nội dung này trước khi bắt đầu gán nhãn. Giữ lại các quyết định sau khi self-QC.

## Định nghĩa lớp

| Lớp | Định nghĩa của bạn | Ví dụ/điểm phân biệt |
| --- | --- | --- |
| `car` | Xe ô tô con dùng để chở người, thường có kích thước nhỏ, gồm sedan, hatchback và SUV | Phân biệt với van dựa vào hình dáng thân xe và mục đích thiết kế |
| `truck` | Xe tải được thiết kế chủ yếu để vận chuyển hàng hóa, thường có thùng hàng hoặc khoang chở hàng riêng | Phân biệt với bus vì truck có phần chở hàng thay vì khoang chở hành khách |
| `bus` | Xe buýt hoặc xe khách cỡ lớn, được thiết kế để vận chuyển nhiều hành khách | Thân xe thường dài, có nhiều cửa sổ và hàng ghế hành khách |
| `van` | Xe dạng van hoặc minibus cỡ nhỏ, có thân xe cao, khoang chở người hoặc hàng tương đối rộng | Phân biệt với car bởi kiểu thân xe dạng hộp; phân biệt với bus bởi kích thước và cấu trúc xe |

## Quy tắc chung

- Box bám sát vật thể nghĩa là: Bounding box phải bao quanh sát phần nhìn thấy của phương tiện, hạn chế chứa nền thừa, không bỏ sót phần thân xe có thể quan sát được
- Vật thể bị che khuất: Nếu vẫn nhận diện được loại phương tiện thì tiếp tục gán nhãn, box bao quanh phần có thể quan sát được, không tự suy đoán phần bị che khuất
- Vật thể bị cắt bởi rìa ảnh: Vẫn gán nhãn nếu có đủ đặc điểm để xác định lớp, box giới hạn trong phạm vi ảnh
- Vật thể rất nhỏ/mơ hồ: Chỉ gán nhãn khi có thể xác định tương đối chắc chắn loại phương tiện. Không gán nhãn nếu vật thể quá nhỏ, mờ hoặc không đủ thông tin để phân loại

## Ghi lại quyết định cho ít nhất ba ca mơ hồ

| Ảnh | Tình huống | Quyết định cuối | Lý do theo schema |
| --- | --- | --- | --- |
| `drive_012` | Xe ở xa, kích thước nhỏ, khó phân biệt car và van | Gán car nếu nhận diện rõ kiểu thân xe | Dựa vào đặc điểm hình dạng |
| `drive_025` | Xe bị che khuất một phần | 	Vẽ box quanh phần nhìn thấy | Không suy đoán phần bị che |
| `drive_038` | Xe nằm sát mép ảnh | Vẽ box giới hạn trong ảnh | Không để box vượt ranh giới ảnh |
