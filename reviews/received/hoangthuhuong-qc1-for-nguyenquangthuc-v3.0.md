# Phiếu QC 1 v3.0 — Road v1.0

Lô được kiểm (học viên): Nguyễn Quang Thức (`nguyenquangthuc`)  
Người review: Hoàng Thu Hương (`hthuong`)  
Trạng thái: **Chờ Hương duyệt**  
Ngày lập: 22/11/2026  
Phiên bản guideline: Road v1.0  
Phiên bản CVAT: Server/UI 2.82.0

## Phạm vi kiểm

Phiếu này kiểm bản export đã sửa sau QC v2.0:

- `submission/nguyenquangthuc-front.zip`: 16 ảnh
- `submission/nguyenquangthuc-fisheye.zip`: 12 ảnh
- Tổng cộng: 28 ảnh
- Manifest: `submission/nguyenquangthuc-manifest.json`, **revision 5**
- Commit chứa bản export: `2f997cc`

## Kết quả đối chiếu với QC v2.0

| Hạng mục | Kết quả revision 5 | Trạng thái |
| --- | --- | --- |
| B01, B02, B05, B09, B10, B11 thiếu lane | Đã có lane trong XML | Đã xử lý, Hương xác nhận hình học |
| A07 lane L1 chỉ có 2 điểm | Lane hiện có 4 điểm | Đã xử lý |
| B03 chiều polyline | Điểm đầu gần xe, điểm cuối xa xe | Đã xử lý, Hương xác nhận hình học |
| B04 chiều polyline | Điểm đầu gần xe, điểm cuối xa xe | Đã xử lý, Hương xác nhận hình học |
| B07 chiều polyline | Điểm đầu gần xe, điểm cuối xa xe | Đã xử lý, Hương xác nhận hình học |
| B06 chiều polyline | Vẫn cần kiểm tra hai lane theo ảnh | Còn mở |
| B12 thiếu lane | XML hiện chưa có polyline `lane` | Cần Hương xác nhận có nhìn thấy lane trên ảnh |
| A03 traffic light nhỏ | Cảnh báo lint dưới 8 px | Cảnh báo nhẹ, không bắt buộc |

## Kiểm tra tự động

Lệnh đã chạy:

```powershell
$env:PYTHONPATH="src"
python -m road_lab.road_check lint `
  submission\nguyenquangthuc-front.zip `
  submission\nguyenquangthuc-fisheye.zip `
  --manifest submission\nguyenquangthuc-manifest.json `
  --name nguyenquangthuc `
  --revision 5
```

Kết quả:

- 28 ảnh hợp lệ.
- 0 lỗi nặng.
- 0 lỗi chính.
- 1 cảnh báo nhẹ ở A03: traffic light nhỏ hơn 8 px, không bắt buộc sửa.
- Bộ test repo: `31 passed`.

## Các điểm Hương cần duyệt trực tiếp trên CVAT

1. B06: xác nhận chiều vẽ của cả hai lane theo quy tắc gần xe → xa.
2. B12: xác nhận ảnh có vạch lane nhìn thấy hay không. Nếu có, bổ sung lane với position phù hợp; nếu không có, ghi rõ miễn QC1-02.
3. Xác nhận các lane mới ở B01, B02, B05, B09, B10, B11 bám đúng vạch nhìn thấy trên ảnh.
4. Xác nhận ca A03 và cảnh báo traffic light nhỏ là chấp nhận được.

## Đề nghị quyết định

Sau khi Hương kiểm tra ba nhóm điểm trên, chọn một trong hai kết luận:

- **RELEASE:** nếu B06 đúng chiều và B12 không có lane nhìn thấy, hoặc đã được bổ sung đúng.
- **REWORK:** nếu B06 còn ngược chiều hoặc B12 có lane nhìn thấy nhưng vẫn thiếu.

Phiếu này chưa tự đánh dấu Release; quyết định cuối cùng thuộc về người review.

## Ghi chú

QC v3.0 là bản review đề nghị Hương duyệt cho revision 5. Nó thay thế bản QC v2.0 về phạm vi phiên bản, nhưng không thay thế xác nhận trực quan của Hương trên CVAT.
