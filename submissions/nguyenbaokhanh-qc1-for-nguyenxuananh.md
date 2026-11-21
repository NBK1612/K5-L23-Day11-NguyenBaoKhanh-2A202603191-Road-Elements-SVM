# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): Nguyễn Xuân Anh        Người kiểm (học viên): Nguyễn Bảo Khánh  
Ngày: 21/11/2026                               Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): `NguyenXuanAnh-front.zip` (sha256 `49237351…`), `NguyenXuanAnh-fisheye.zip` (sha256 `658dbc44…`); không nhận được manifest nên không có `revision`  
Số ảnh kiểm: 6 (A03, A04, A07, A09, B02, B04) (+ 0 ảnh thêm)   Số nhãn đã kiểm (shape + tag): 77 (53 shape + 24 tag)

Cách kiểm: mở từng nhãn trong file export, đối chiếu bằng mắt với ảnh gốc và guideline Road v1.0, kết hợp `road_check lint` (lint báo 37 cảnh báo trên cả lô 28 ảnh). Người kiểm không có GT nên không đo độ lệch pixel so với GT.

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 6 | 1 | nhẹ (tag weather; tag camera đúng cả 6 ảnh) |
| QC1-02 đủ L1, R1 | bỏ sót | 8 | 1 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 11 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 11 | 3 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 11 | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 11 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 15 | 0 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 11 | 0 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 27 | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 16 | 0 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 11 | 3 | chính |
| QC1-12 file | lỗi file | 2 | 0 | nhẹ / nặng |

Cách đếm số mục kiểm: QC1-01 theo ảnh; QC1-02 = 2 vị trí (L1, R1) × 4 ảnh front; QC1-03 đến QC1-06 theo số lane; QC1-07 = drivable + crosswalk + road_curb; QC1-08 theo số đèn; QC1-09 = đèn + biển; QC1-10 theo số biển; QC1-11 theo số shape trên ảnh fisheye; QC1-12 theo số file (cả hai mở được bằng `road_check lint`, đúng định dạng CVAT for images 1.1, không kèm ảnh).

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-02 | A03 | lane L1 (không có) | nặng | Thiếu L1: vạch vàng liền bên trái làn xe đang đi thấy rõ, chạy từ đáy ảnh (x ≈ 230) lên tới x ≈ 530, y ≈ 380 |
| 2 | QC1-04 | A03 | lane #7 (R1) | chính | Vẽ ngược chiều: điểm đầu (594,384) ở xa, điểm cuối (925,655) ở gần xe |
| 3 | QC1-04 | A04 | lane R2 (không có) | chính | Thiếu vạch trắng liền bên phải, giữa làn xe và làn xe đạp màu xanh (từ x ≈ 680, y ≈ 335 ra mép phải ảnh y ≈ 520); polyline road_curb #9 chỉ theo mép vỉa hè |
| 4 | QC1-04 | A09 | lane #9 (L2) | chính | Vẽ ngược chiều: điểm đầu (463,459) ở xa, điểm cuối (473,662) ở gần xe |
| 5 | QC1-11 | B02 | traffic_light #3 | chính | Tâm hộp ngoài 80 % bán kính vòng ảnh nhưng `edge_zone` chưa bật |
| 6 | QC1-11 | B02 | traffic_light #4 | chính | Tâm hộp ngoài 80 % bán kính vòng ảnh nhưng `edge_zone` chưa bật |
| 7 | QC1-11 | B04 | traffic_sign #2 (biển cấm đi ngược chiều) | chính | Tâm hộp ngoài 80 % bán kính vòng ảnh nhưng `edge_zone` chưa bật |
| 8 | QC1-01 | A07 | tag weather | nhẹ | `overcast`, nhưng mặt đường ướt rõ và có giọt nước trên kính: theo guideline là `rain` |

Ảnh không có lỗi nặng hoặc chính: **A07** (chỉ có lỗi nhẹ số 8; hai câu hỏi về A07 nằm ở mục Ca mơ hồ).

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A03, A04 | Tag `timeofday = dusk`: trời còn sáng, mây ánh chiều. Nên chọn `day` hay `dusk`? A04 có nhiều mây: `weather = clear` hay `overcast`? | Chờ coach |
| A07 | Bên trái làn là dải phân cách bê tông, không thấy vạch sơn: có được miễn QC1-02 (thiếu L1) không? Các cụm đèn ở xa (x ≈ 640–760, y ≈ 235) có cao từ 8 px để bắt buộc gán không? | Chờ coach |
| A09 | Bên phải làn là mép vỉa hè không sơn: thiếu R1 có được miễn QC1-02 không? Ảnh trọng tâm "biển báo" có bắt buộc gán road_curb bên phải không? | Chờ coach |
| B04 | Camera sau: vạch đứt nằm bên trái ảnh được gán `L1`. Nếu tính trái/phải theo hướng xe chạy thì đây là `R1` (ảnh RV lật trái–phải). Lô tính theo ảnh: quy ước nào đúng? Nếu tính theo xe, đây là lỗi nặng QC1-03 | Chờ coach |

## Quyết định
Lỗi nặng: 1   Lỗi chính: 6 / 77 nhãn = 7,8 %   Lỗi nhẹ: 1   Ca chờ lead: 4  
Quyết định (Release / Hold / Rework): **Rework**  
Lý do (theo luật của phiếu): Còn 1 lỗi nặng (A03 thiếu L1 trong khi vạch vàng thấy rõ), nên Rework. Tỉ lệ lỗi chính 7,8 % cũng vượt ngưỡng 5 % số nhãn đã kiểm. Bốn ca chờ lead không đổi kết luận nên không chọn Hold.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).
