# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): Nguyễn Quang Thức (nguyenquangthuc)  
Người kiểm (học viên): Hoàng Thu Hương (hthuong)  
Ngày: 21/11/2026                          Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): `nguyenquangthuc-front.zip`, `nguyenquangthuc-fisheye.zip`, revision 2  
Số ảnh kiểm: 16 front + 12 fisheye = 28 ảnh   Số nhãn đã kiểm (shape + tag): 378 (183 lane + 73 drivable + 16 crosswalk + 14 road_curb + 60 traffic_light + 57 traffic_sign + 112 tag = 392 tổng)

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 28 ảnh | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 44 L1/R1 (22 ảnh × 2) | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 44 lane | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 44 lane | 6 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 44 lane | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 44 lane | 0 | chính |
| QC1-07 vùng lái, vạch qua đường | sai phạm vi / bỏ sót / thừa | 73 drivable + 16 crosswalk = 89 | 7 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 60 traffic_light | 0 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 60 light + 57 sign = 117 | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 57 traffic_sign | 0 (1 sign < 8 px, không bắt buộc) | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính / **bỏ sót lane** | 12 ảnh fisheye | 7 | chính / nặng |
| QC1-12 file | lỗi file | 2 file zip | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-04 | A07 | lane L1, 2 điểm | chính | Polyline chỉ 2 điểm, cách xa 157 px (từ y=443 đến y=395). Quá cơ sở, không theo cung hay gấp khúc |
| 2 | QC1-04 | B03_04267_RV | lane L1, chiều | chính | Vẽ **từ xa về gần**: firstY=295 → lastY=654. Ngược quy tắc 2 |
| 3 | QC1-04 | B04_05535_RV | lane R1, chiều | chính | Vẽ **từ xa về gần**: firstY=274 → lastY=529. Ngược quy tắc 2 |
| 4 | QC1-04 | B06_04068_MVL | lane `other`, chiều | chính | Vẽ **từ xa về gần**: firstY=492 → lastY=818. Ngược quy tắc 2 |
| 5 | QC1-04 | B07_01216_MVR | lane `other`, chiều | chính | Vẽ **từ xa về gần**: firstY=660 → lastY=754. Ngược quy tắc 2. (Nhưng ảnh này `drivable` đã được vẽ nên vạch vẫn có) |
| 6 | QC1-04 | B06_04068_MVL | lane #2 `other`, chiều | chính | Lane thứ hai của B06 cũng vẽ ngược chiều: firstY=492 → lastY=818. Tổng 2 lane trên B06 cùng lỗi |
| 7 | QC1-07 | B01_02688_FV | (thiếu) lane | **nặng** | Ảnh không có lane nào, chỉ có 1 crosswalk + 1 drivable + 1 road_curb + 2 đèn. Fisheye_front phải có lane (ít nhất L1/R1 hoặc `other` tùy camera) |
| 8 | QC1-11 | B01 | lane bỏ sót | nặng | Fisheye_front (FV) phải gán lane nếu thấy vạch. B01 không có lane |
| 9 | QC1-11 | B02_03177_FV | lane bỏ sót | nặng | Fisheye_front (FV) không có lane, chỉ có drivable + crosswalk + road_curb + đèn |
| 10 | QC1-11 | B05_05780_MVL | lane bỏ sót | nặng | Fisheye_left (MVL) chỉ có 1 crosswalk + 1 drivable, không có lane |
| 11 | QC1-11 | B09_02686_FV | lane bỏ sót | nặng | Fisheye_front (FV) không có lane |
| 12 | QC1-11 | B10_01153_MVL | lane bỏ sót | nặng | Fisheye_left (MVL) chỉ có 1 crosswalk + 1 drivable, không có lane |
| 13 | QC1-11 | B11_07282_RV | lane bỏ sót | nặng | Fisheye_rear (RV) chỉ có 1 drivable, không có lane. Ảnh phía sau thấy rõ vạch vàng |
| 14 | QC1-11 | B12_05885_MVR | lane bỏ sót | nặng | Fisheye_right (MVR) chỉ có 2 crosswalk + 1 drivable + 1 road_curb, không có lane |

**Nhận xét**:
- **Lỗi chính (QC1-04, QC1-07)**: 13 lỗi chính
- **Lỗi nặng (QC1-11 lane bỏ sót fisheye)**: 7 lỗi nặng
- **Tỉ lệ lỗi chính**: 13 / 378 ≈ 3,4% (vẫn < 5%)
- **Nhưng**: 7 lỗi nặng trên 7 ảnh fisheye khác nhau = lỗi hệ thống, không phải sơ suất riêng lẻ

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A03 | Cần kiểm: lane #2 (xanh) có phải là thừa? Overlay cho thấy 3 lane nhưng đó chỉ nên là 2 | (chờ) |

## Quyết định
Lỗi nặng: **7** (QC1-11 lane bỏ sót 7 ảnh fisheye)   Lỗi chính: 13 / 378 nhãn ≈ 3,4 %   Lỗi nhẹ: 1 (1 traffic_sign < 8 px)   Ca chờ lead: 1  

Quyết định (Release / Hold / Rework): **REWORK**  

Lý do (theo luật của phiếu): Còn **7 lỗi nặng** → Rework theo luật "Một lỗi nặng là đủ để Rework". Cộng thêm 1 ca mơ hồ chưa có lời đáp.

**Việc cần làm ở revision 3:**
1. Vẽ lane cho 7 ảnh fisheye không có: B01, B02, B05, B09, B10, B11, B12. Ảnh B11 thấy rõ vạch vàng phía sau.
2. Sửa chiều polyline cho B03, B04, B06, B07 (2 lần): vẽ từ gần xe ra xa.
3. Sửa A07 lane L1: thêm điểm, từ 2 điểm thành ≥3 điểm.
4. Kiểm lại A03 xem có thừa lane không.
5. Export lại, chạy `lint`, chỉ được còn cảnh báo ≤ nhẹ.
6. Tạo manifest `--revision 3`, giữ manifest revision 2 trong thư mục `r2/`.

---
Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).
