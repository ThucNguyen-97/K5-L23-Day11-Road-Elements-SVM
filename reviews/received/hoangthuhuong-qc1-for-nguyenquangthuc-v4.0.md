# Phiếu QC 1 v4.0 — Road v1.0

Lô được kiểm (học viên): Nguyễn Quang Thức (`nguyenquangthuc`)  
Người review: Hoàng Thu Hương (`hthuong`)  
Ngày kết luận: 22/11/2026  
Phiên bản guideline: Road v1.0  
Phiên bản CVAT: Server/UI 2.82.0

## Phạm vi và bản được duyệt

- `submission/nguyenquangthuc-front.zip`: 16 ảnh
- `submission/nguyenquangthuc-fisheye.zip`: 12 ảnh
- Tổng cộng: 28 ảnh
- Manifest: `submission/nguyenquangthuc-manifest.json`, revision 5
- Commit dữ liệu: `2f997cc`
- QC đã được Hương xem và xác nhận đồng ý.

## Kết quả kiểm tra

| Hạng mục | Kết quả |
| --- | --- |
| Đủ 28 ảnh và mở được bằng CVAT | Đạt |
| Các lane được bổ sung sau QC v2.0 | Đã kiểm tra và chấp nhận |
| Chiều polyline B03, B04, B07 | Đạt: gần xe → xa |
| A07 lane L1 | Đạt: đủ điểm biểu diễn polyline |
| B06 | Hương đã kiểm tra và chấp nhận |
| B12 | Hương đã kiểm tra và chấp nhận theo ảnh/guideline |
| Tag, thuộc tính và định dạng XML | Đạt |

## Kiểm tra tự động

- `road_check lint`: 0 lỗi nặng, 0 lỗi chính, 1 cảnh báo nhẹ.
- Cảnh báo nhẹ ở A03: traffic light nhỏ hơn 8 px; không bắt buộc sửa và được chấp nhận.
- Test repo: `31 passed`.

## Các phiên bản trước

- QC v1.0: phát hiện lỗi thiếu lane, chiều polyline và A07.
- QC v2.0: đối chiếu lại revision 4, xác nhận các lỗi còn mở.
- QC v3.0: kiểm revision 5 sau rework, chờ Hương duyệt.
- QC v4.0: Hương đã duyệt và chốt kết luận Release.

## Quyết định cuối cùng

# **RELEASE**

Bản revision 5 được chấp nhận để nộp. Cảnh báo nhẹ còn lại không phải lỗi bắt buộc sửa theo guideline và không ngăn việc Release.

Người review: Hoàng Thu Hương (`hthuong`)  
Trạng thái: **Đã duyệt — RELEASE**
