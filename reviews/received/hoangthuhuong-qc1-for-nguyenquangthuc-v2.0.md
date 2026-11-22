# Phiếu QC 1 v2.0 — Road v1.0

Lô được kiểm (học viên): Nguyễn Quang Thức (`nguyenquangthuc`)  
Người kiểm: Hoàng Thu Hương (`hthuong`)  
Ngày cập nhật: 22/11/2026  
Phiên bản guideline: Road v1.0  
Phiên bản CVAT: Server/UI 2.82.0

## Phạm vi kiểm

Phiếu này cập nhật từ phiếu QC v1.0, chuyển phạm vi kiểm từ revision 2 sang **revision 4**:

- `nguyenquangthuc-front.zip`: 16 ảnh
- `nguyenquangthuc-fisheye.zip`: 12 ảnh
- Tổng cộng: 28 ảnh
- Manifest: `submission/nguyenquangthuc-manifest.json`, revision 4

Revision 4 đã cập nhật lại front và đã chạy kiểm tra tự động. Tuy nhiên, việc cập nhật revision không tự động đóng các lỗi hình học/thiếu nhãn được nêu trong phiếu cũ.

## Đối chiếu lỗi từ phiếu v1.0

| Nhóm | Trạng thái ở revision 4 | Ghi chú |
| --- | --- | --- |
| A07 — lane L1 chỉ có 2 điểm | **Còn mở** | A07 vẫn có một lane chỉ gồm 2 điểm; cần thêm điểm để biểu diễn đường cong/gấp khúc rõ hơn. |
| B03, B04 — chiều polyline | **Còn mở** | Thứ tự điểm vẫn có dạng từ xa về gần theo tiêu chí phiếu cũ. |
| B06, B07 — chiều polyline | **Còn mở** | Các lane bị nêu trong phiếu cũ vẫn cần xác nhận/sửa theo quy tắc gần xe → xa. |
| B01, B02, B05, B09, B10, B11, B12 — thiếu lane | **Còn mở** | Kiểm tra XML revision 4 vẫn không thấy polyline `lane` ở 7 ảnh này. |
| A03 — lane thứ hai có thừa không | **Cần lead xác nhận** | Vẫn là ca mơ hồ, không tự ý kết luận. |

## Danh sách lỗi còn mở

| # | Mã | Ảnh | Mức | Kết luận v2.0 |
| ---: | --- | --- | --- | --- |
| 1 | QC1-04 | A07 | chính | Lane L1 chỉ có 2 điểm; cần bổ sung điểm. |
| 2 | QC1-04 | B03 | chính | Chiều polyline cần kiểm/sửa theo quy tắc gần xe → xa. |
| 3 | QC1-04 | B04 | chính | Chiều polyline cần kiểm/sửa theo quy tắc gần xe → xa. |
| 4 | QC1-04 | B06 | chính | Hai lane được nêu trong phiếu cũ cần kiểm/sửa chiều. |
| 5 | QC1-04 | B07 | chính | Các lane được nêu trong phiếu cũ cần kiểm/sửa chiều. |
| 6 | QC1-11 | B01 | nặng | Thiếu lane. |
| 7 | QC1-11 | B02 | nặng | Thiếu lane. |
| 8 | QC1-11 | B05 | nặng | Thiếu lane. |
| 9 | QC1-11 | B09 | nặng | Thiếu lane. |
| 10 | QC1-11 | B10 | nặng | Thiếu lane. |
| 11 | QC1-11 | B11 | nặng | Thiếu lane. |
| 12 | QC1-11 | B12 | nặng | Thiếu lane. |

## Kiểm tra file và lint

- Hai ZIP mở được và có đủ 28 ảnh.
- Manifest revision 4 khai báo 0 lỗi nặng, 0 lỗi chính và 1 cảnh báo nhẹ từ `road_check lint`.
- Cảnh báo lint nhẹ không thay thế cho QC thủ công: lint không kết luận được lane bị thiếu hoặc chiều polyline.
- Phiếu v1.0 có sai lệch số liệu: phần tiêu đề ghi 378 nhãn nhưng tổng chi tiết là 392. v2.0 không dùng con số 378 làm mẫu số.

## Quyết định

**REWORK — chưa đủ điều kiện Release.**

Lý do: revision 4 vẫn còn 7 trường hợp thiếu lane trong fisheye, cùng các lỗi chiều polyline và A07 chỉ có 2 điểm đã nêu ở phiếu v1.0. Sau khi sửa, cần export revision mới, cập nhật manifest và kiểm lại toàn bộ các ảnh bị nêu.

## Việc cần làm trước lần kiểm tiếp theo

1. Bổ sung lane cho B01, B02, B05, B09, B10, B11, B12 nếu vạch lane nhìn thấy theo guideline.
2. Sửa/ xác nhận chiều polyline ở B03, B04, B06, B07.
3. Bổ sung điểm cho lane L1 của A07.
4. Xin lead kết luận cho ca A03.
5. Export revision mới, chạy `python -m road_lab.road_check lint ...` và ghi lại kết quả.
6. Người review xác nhận lại bản export mới trước khi chuyển sang Release.

> Đây là bản cập nhật v2.0 dựa trên phiếu v1.0 và đối chiếu XML revision 4. Để được xem là phiếu review chéo chính thức, Hương cần xác nhận lại các kết luận trên sau khi mở trực tiếp revision 4 trong CVAT.
