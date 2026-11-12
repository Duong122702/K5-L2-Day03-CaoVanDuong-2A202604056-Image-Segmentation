# Báo cáo thực hành Day 3 — điền trực tiếp trong fork của bạn



- Mã học viên theo lớp: 2A202604056
- Ngày / CVAT local: 11/11/2026
- Công cụ đã dùng: CVAT local (Brush, Polygon); gợi ý tự động của CVAT chỉ dùng ở task medium sau khi đã tự vẽ object đầu tiên

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh [LMS](https://aithucchien.vinuni.edu.vn) đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | … | … / 1 | 3 |
| cp2_slice | … | … / 1 | 3 |
| cp5_occlusion | … | … / 1 | 3 |
| cp3_thin | … | … / 1 | 3 |
| cp4_curb | … | … / 1 | 3 |
| cp6_coverage | … | … / 1 | 3 |
| **Tổng tối đa** | | | **100** |


## 2. Một quyết định trước khi dùng gợi ý

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: 000000181542.jpg, Object person nằm ở giữa màn hình có người phụ nữ mặc áo dài
- Class và quy tắc tôi dùng để chọn biên: class person, vẽ bám theo phần cơ thể và trang phục nhìn thấy được, dừng ở mép tà áo dài và mép tóc, không lấn sang nền phía sau. Phần bị vật khác che thì không vẽ xuyên qua.
- Nếu dùng gợi ý sau đó: vùng gợi ý sai/đúng, hành động sửa/giữ và lý do: Gợi ý tự động ở một người khác trong ảnh bị gộp cả phần nền/vật bên cạnh vào mask. Tôi sửa bằng cách xóa phần thừa ở sát biên và vẽ lại bằng Polygon, vì mask phải bám theo phần nhìn thấy của đúng một người.

## 3. Một lỗi tôi tìm thấy và sửa

- Task/ảnh/vùng: task 2, ảnh 000000181542.jpg
- Lỗi thuộc loại: sai lớp / thiếu-thừa vật / gộp-tách / biên / phủ vùng / khác: biên 
- Bằng chứng tôi nhìn thấy: biên của object bị tràn ra nền
- Quy tắc và hành động sửa: Quy tắc biên của vật phải bám sát vật, sửa lại đưa biên lại gần vật
- Sau sửa đã Save và export lại chưa? Đã sửa


## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| 000000460147.jpg | Phía xa trân trời có thể là buliding hoặc road | Pixel mờ, không đủ dấu hiệu để quyết định | Nên để trống hay gán lớp gần nhất? |
| 000000460147.jpg | Phần làn đường ở phía trong bên phải có thể là road hoặc sidewalk | Phân theo chức năng và bó vỉa, không theo màu nhựa đường | Quyết định chọn road |
| 000000181542.jpg | Người đi xe máy bên phải chân và yên xe tương đối giống nhau | Chỉ vẽ đến phần nhìn thấy | Quyết định chọn person |
