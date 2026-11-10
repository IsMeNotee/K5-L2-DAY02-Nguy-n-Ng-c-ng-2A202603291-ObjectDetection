# Báo cáo cá nhân — Ngày 2 Object Detection
## 1. Thông tin học viên

- Họ tên: Nguyễn Ngọc Đồng
- MSSV: 2A202603291
- Email: csjbvhfff@gmail.com
- Lớp: K5-L2
- Link repo bài làm: https://github.com/IsMeNotee/K5-L2-DAY02-Nguy-n-Ng-c-ng-2A202603291-ObjectDetection
- Link Colab đã chạy: https://colab.research.google.com/github/IsMeNotee/K5-L2-DAY02-Nguy-n-Ng-c-ng-2A202603291-ObjectDetection/blob/main/notebooks/day2_annotation_to_yolo.ipynb#scrollTo=3e0508d8

## 2. Schema và mini guideline

Dẫn tới [GUIDELINE_MINI.md](../../GUIDELINE_MINI.md).
Ba ca mơ hồ: xe ở xa khó nhận diện, xe bị che khuất và xe khó phân biệt car/van. Áp dụng schema 4 lớp để phân loại nhất quán. Cần giảng viên làm rõ quy tắc xử lý xe quá nhỏ và xe khó phân loại.

## 3. Annotation và self-QC

- Số file nhãn train: 50
- Kết quả checker và lỗi đã xử lý:  PASS, không còn lỗi
- Danh sách ít nhất 10 ảnh đã rà bằng mắt: : drive_001 đến drive_010
- Lỗi bỏ sót/box/class phát hiện khi rà và cách sửa: Không phát hiện lỗi khi rà bằng mắt
- Commit khóa nhãn ban đầu: 9f61152

## 4. Gold QC và rework

| Chỉ số | Trước sửa | Sau sửa nếu có |
|---|---:|---:|
| TP |421 | |
| FP | 585 | |
| FN | | 232  |
| Precision | 0.4185 | |
| Recall | 0.6447 | |
| F1 | 0.5075 | |
| mean_iou_of_matches | 0.7043 | |
| passed | True | |

Dẫn tới `outputs/annotation_evaluation.json` trong repo.
- Link: https://github.com/IsMeNotee/K5-L2-DAY02-Nguy-n-Ng-c-ng-2A202603291-ObjectDetection/blob/main/outputs/annotation_evaluation.json
- Không rework

## 5. Kết quả YOLO

- Runtime, GPU/CPU, phiên bản Ultralytics và Torch:
- Các tham số thay đổi so với notebook nếu có và lý do:
- Đường dẫn best checkpoint trong phiên chạy:

| Chỉ số trên 10 ảnh eval | Giá trị |
|---|---:|
| Precision | 0.4105 |
| Recall | 0.2303 |
| mAP50 | 0.2723 |
| mAP50–95 | 0.2017 |

Đặt cả 2 folder `assets/eval_predictions/` và `assets/yolo26_runs/` (giải nén từ `day2_colab_outputs.zip`) cạnh báo cáo và dẫn link tương đối. Không chỉ ghi số; chỉ ra ít nhất một ảnh và vật thể cụ thể.

Trả lời bốn câu hỏi cuối notebook:

1. Lớp nào recall thấp nhất? Ảnh nào minh họa?
Lớp bus có recall thấp nhất (0.000), tiếp theo là van (0.0833). Ảnh drive_053.jpg minh họa trường hợp xe buýt bị nhận diện chưa chính xác.
2. Nếu mAP50 cao nhưng mAP50–95 thấp, cần kiểm điều gì trên box?
Kiểm tra bounding box có bị lệch, quá rộng, quá hẹp hoặc không ôm sát vật thể.
3. Lỗi class nào có thể liên quan guideline? Dữ kiện nào hỗ trợ nhận xét?
Có dấu hiệu nhầm giữa bus, van và car. Ví dụ ở drive_053.jpg, một số phương tiện lớn bị dự đoán thành car. Recall của bus bằng 0 và van chỉ đạt 0.0833, cho thấy mô hình chưa phân biệt tốt các lớp này.
4. Vì sao không dùng 10 ảnh eval để train? Vai trò validation của chúng trong notebook là gì?
10 ảnh eval được giữ riêng để đánh giá mô hình trên dữ liệu chưa dùng huấn luyện. Chúng giúp tính Precision, Recall, mAP và kiểm tra khả năng tổng quát hóa, tránh rò rỉ dữ liệu và kết quả đánh giá thiếu khách quan.

## 6. Khó khăn và cách xử lý

| Bước/thời điểm | Lỗi quan sát | Cách đã thử | Kết quả/còn thiếu |
|---|---|---|---|
| Push GitHub | Git chưa nhận tên và email | Cấu hình git config |Push thành công |

## 7. Tự đánh giá theo rubric

Đối chiếu [RUBRIC.md](../../RUBRIC.md): phần nào đã có kết quả, phần nào còn thiếu hoặc chưa kiểm được. Không tự nhận hoàn thành bước chưa chạy.
Đã có 50 file nhãn YOLO, kết quả checker, mini guideline, Gold QC và pipeline YOLO trên Colab
- Gold QC: F1 = 0.5075, Mean IoU = 0.7043
- YOLO eval: mAP50 = 0.2723, mAP50–95 = 0.2017
- Còn thiếu/chưa xác nhận: Chất lượng annotation theo ngưỡng rubric, mức độ đầy đủ vật thể, độ chính xác box

## 8. Công cụ AI và tài liệu tham khảo

- ChatGPT: Hỗ trợ hướng dẫn GitHub, Colab, giải thích kết quả YOLO và trình bày báo cáo. Các số liệu lấy từ kết quả chạy thực tế.
- CVAT: Gán nhãn 50 ảnh.
- VS Code: Kiểm tra nhãn và hoàn thiện báo cáo.
- Google Colab: Train và đánh giá mô hình YOLO.
- Tài liệu: Repository K5-L2-Day02-ObjectDetection của VinUni.

