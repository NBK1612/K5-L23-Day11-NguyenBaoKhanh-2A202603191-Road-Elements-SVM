# Phiếu QC 1 — Road v1.0

> **Ghi chú:** học viên làm lab cá nhân, không được ghép cặp nên không có lô của bạn khác để kiểm. Phiếu này áp dụng đúng quy trình Phiếu QC 1 lên **lô của chính mình** (tự kiểm). Mẫu 6 ảnh gồm 4 ảnh front và 2 ảnh fisheye; người kiểm không có GT nên đối chiếu bằng mắt với ảnh, guideline Road v1.0 và kết quả `road_check lint`.

Lô được kiểm (học viên): nguyenbaokhanh        Người kiểm (học viên): nguyenbaokhanh (tự kiểm)  
Ngày: 20/11/2026                               Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): `nguyenbaokhanh-front.zip`, `nguyenbaokhanh-fisheye.zip`, revision 1  
Số ảnh kiểm: 6 (A01, A04, A07, A11, B02, B03) (+ 0 ảnh thêm)   Số nhãn đã kiểm (shape + tag): 112 (84 shape + 28 tag)

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 6 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 8 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 18 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 18 | 0 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 18 | 7 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 18 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 31 | 3 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 10 | 2 | chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 35 | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 25 | 3 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 31 | 8 | chính |
| QC1-12 file | lỗi file | 2 | 1 | nhẹ |

Cách đếm số mục kiểm: QC1-01 theo ảnh; QC1-02 = 2 vị trí (L1, R1) × 4 ảnh front; QC1-03 đến QC1-06 theo số lane; QC1-07 = drivable + crosswalk + road_curb; QC1-08 theo số đèn; QC1-09 = đèn + biển; QC1-10 theo số biển; QC1-11 theo số shape trên ảnh fisheye; QC1-12 theo số file.

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-05 | A01 | lane #9 | chính | Trùng hệt lane L2 #1 (thừa một polyline) |
| 2 | QC1-05 | A01 | lane #12 | chính | Gần trùng lane L2 #1 (lệch < 5 px): L2 bị vẽ ba lần |
| 3 | QC1-05 | A04 | lane #2 + #3 | chính | Vạch vàng đôi vẽ thành hai polyline (mỗi nét một đường); phải là một polyline ở giữa hai nét, `kind = double` |
| 4 | QC1-05 | A11 | lane #10 + #11 | chính | Vạch vàng đôi vẽ thành hai polyline |
| 5 | QC1-05 | A11 | lane #18 | chính | Trùng hệt lane R1 #9 |
| 6 | QC1-05 | A11 | lane #19 | chính | Trùng hệt lane L1 #11 |
| 7 | QC1-05 | A11 | lane #21 | chính | Trùng hệt lane L1 #10 |
| 8 | QC1-07 | A11 | crosswalk #15 | chính | Trùng hệt crosswalk #6 |
| 9 | QC1-07 | A11 | drivable #16 | chính | Trùng hệt drivable direct #7 |
| 10 | QC1-07 | A11 | drivable #17 | chính | Trùng hệt drivable alternative #8 |
| 11 | QC1-08 | A11 | traffic_light #12 | chính | Trùng hệt traffic_light #1 |
| 12 | QC1-08 | A11 | traffic_light #13 | chính | Trùng hệt traffic_light #2 |
| 13 | QC1-10 | A11 | traffic_sign #5 | chính | Trùng hộp #0 nhưng khác `group` (#0 supplementary, #5 information) |
| 14 | QC1-10 | A11 | traffic_sign #14 | chính | Trùng hệt traffic_sign #4 |
| 15 | QC1-10 | A11 | traffic_sign #20 | chính | Trùng hộp #3 nhưng khác `group` (#3 information, #20 supplementary) |
| 16 | QC1-11 | B02 | traffic_light #0 | chính | Tâm hộp ngoài 80 % bán kính, `edge_zone` chưa bật |
| 17 | QC1-11 | B02 | traffic_light #1 | chính | Tâm hộp ngoài 80 % bán kính, `edge_zone` chưa bật |
| 18 | QC1-11 | B02 | traffic_light #3 | chính | Tâm hộp ngoài 80 % bán kính, `edge_zone` chưa bật |
| 19 | QC1-11 | B02 | traffic_light #5 | chính | Tâm hộp ngoài 80 % bán kính, `edge_zone` chưa bật |
| 20 | QC1-11 | B03 | traffic_sign #0 | chính | Tâm hộp ngoài 80 % bán kính, `edge_zone` chưa bật |
| 21 | QC1-11 | B03 | traffic_sign #7 | chính | Tâm hộp trong 80 % bán kính nhưng `edge_zone` đang bật |
| 22 | QC1-11 | B03 | traffic_sign #9 | chính | Tâm hộp trong 80 % bán kính nhưng `edge_zone` đang bật |
| 23 | QC1-11 | B03 | traffic_sign #10 | chính | Tâm hộp trong 80 % bán kính nhưng `edge_zone` đang bật |
| 24 | QC1-12 | A11 | tag (4 tag) | nhẹ | Bốn tag camera / timeofday / weather / source mỗi tag xuất hiện hai lần (cùng giá trị) |

Nhận xét: toàn bộ nhãn của A11 (11 shape và 4 tag) bị nhân đôi, khả năng do dán nhãn hai lần. Xóa bản sao ở A11 sẽ loại 11/23 lỗi chính.

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A07 | Bên trái làn là dải phân cách bê tông, không thấy vạch sơn: có được miễn QC1-02 (thiếu L1) không? | Chờ coach |
| A07 | Ảnh trọng tâm "đèn giao thông" nhưng không có hộp đèn; các cụm đèn ở xa (x ≈ 640–760, y ≈ 235) có cao từ 8 px không? Nếu có thì là lỗi bỏ sót QC1-08 | Chờ coach |
| A11 | `timeofday`: trời chạng vạng (trời còn xanh, đèn đường đã bật). Chọn `night` hay `dusk`? | Chờ coach |
| B03 | Camera sau: L1/R1 tính theo trái/phải của xe hay của ảnh? Lô đang tính theo xe | Chờ coach |

## Quyết định
Lỗi nặng: 0   Lỗi chính: 23 / 112 nhãn = 20,5 %   Lỗi nhẹ: 1   Ca chờ lead: 4  
Quyết định (Release / Hold / Rework): **Rework**  
Lý do (theo luật của phiếu): Không có lỗi nặng đã xác định, nhưng tỉ lệ lỗi chính 20,5 % vượt ngưỡng 5 % số nhãn đã kiểm, nên Rework. Bốn ca chờ lead không đổi kết luận: nếu lead trả lời theo hướng bất lợi nhất, kết quả vẫn là Rework. Vì vậy không chọn Hold.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).
