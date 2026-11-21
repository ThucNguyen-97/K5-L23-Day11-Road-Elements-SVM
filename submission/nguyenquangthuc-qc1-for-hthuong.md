# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): hthuong  
Người kiểm (học viên): Nguyễn Quang Thức  
Ngày: 21/11/2026  
Phiên bản guideline: Road v1.0  
File được kiểm: `hthuong-front.zip` và `hthuong-fisheye.zip` (`revision` 1)  
Số ảnh kiểm: 6 (A01, A02, A03, A04, A08, A10)  
Số nhãn đã kiểm (shape + tag): 109  

## Tổng hợp theo mã

| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót |  | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót |  | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa |  | 1 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót |  | 4 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính |  | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính |  | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa |  | 0 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính |  | 0 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính |  | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 6 | 2 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính |  |  | chính |
| QC1-12 file | lỗi file |  | 0 | nhẹ / nặng |

## Danh sách lỗi

| # | Mã | Ảnh | Nhãn | Mức | Mô tả ngắn |
| ---: | --- | --- | --- | --- | --- |
| 1 | QC1-10 | A01 | `traffic_sign` (2 biển) | chính | Thiếu 2 biển chỉ dẫn nhóm `information`. |
| 2 | QC1-03 | A02 | `lane` (polyline ngoài cùng bên trái) | nặng | Thừa một polyline lane ngoài cùng bên trái ảnh; không cần gán. |
| 3 | QC1-04 | A03 | `road_curb` | chính | Không cần vẽ vỉa hè/lề phía bên kia đường. |
| 4 | QC1-04 | A04 | `road_curb` | chính | Không cần vẽ vỉa hè/lề phía bên kia đường. |
| 5 | QC1-04 | A08 | `road_curb` | chính | Không cần vẽ vỉa hè/lề phía bên kia đường. |
| 6 | QC1-04 | A10 | `road_curb` | chính | Không cần vẽ vỉa hè/lề phía bên kia đường. |

## Ca mơ hồ

1. Quy tắc không vẽ road_curb phía bên kia đường áp dụng cho A03, A04, A08 và A10 theo nội dung review.

## Quyết định

Lỗi nặng: 1  
Lỗi chính: 6 / 109 nhãn = 5,50 %  
Lỗi nhẹ: 0  
Ca chờ lead: 0  
Quyết định: **Rework**  
Lý do: Có 1 lỗi nặng QC1-03; đồng thời lỗi chính vượt ngưỡng 5 %.  
