# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): nguyenhoainam        Người kiểm (học viên): dinhduchieu  
Ngày: 21/11/2026                          Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): `nguyenhoainam-front.zip`, `nguyenhoainam-fisheye.zip`, revision 1 (manifest tạo 2026-11-21 03:16 UTC)  
Số ảnh kiểm: 6 (+ 0 ảnh thêm, ghi riêng)   Số nhãn đã kiểm (shape + tag): 77  

Ảnh đã kiểm: A03 (13 nhãn), A04 (11), A07 (13), A11 (12), B03 (20), B07 (8). Mỗi ảnh tính 4 tag + mọi shape.

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 6 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 5 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 14 | 1 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 14 | 1 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 14 | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 14 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 11 | 2 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 8 | 2 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 25 | 1 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 17 | 1 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 20 | 0 | chính |
| QC1-12 file | lỗi file | 2 | 1 | nhẹ / nặng |

Số mục kiểm: QC1-02 tính 5 ảnh có L1/R1 (B07 là camera bên phải, dùng `position = other`); QC1-03 đến QC1-06 tính 14 polyline lane; QC1-07 tính 11 polygon drivable; QC1-08 tính 8 đèn; QC1-09 tính 8 đèn + 17 biển; QC1-10 tính 17 biển; QC1-11 tính 20 nhãn của B03 và B07; QC1-12 tính 2 file zip.

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-03 | A11 | lane #5, L2 solid white, điểm đầu (77,718) | nặng | Thừa: đây là nét ngoài của vạch vàng đôi, không phải một vạch L2 trắng riêng. Bên trái vạch vàng đôi không có vạch nào khác |
| 2 | QC1-04 | A11 | lane #1, L1 solid yellow double, điểm đầu (125,717) | chính | Polyline nằm trên nét trong của vạch đôi, lệch khỏi tâm giữa hai nét khoảng 20 px ở gần xe (vạch đôi = một polyline đặt giữa hai nét) |
| 3 | QC1-08 | A03 | traffic_light (thiếu), khoảng (628,293)–(637,314) | chính | Bỏ sót đèn xanh cao ~21 px bên trái đèn đã gán (705,312) |
| 4 | QC1-08 | A04 | traffic_light (thiếu), khoảng (603,270)–(609,284) | chính | Bỏ sót đèn xanh thứ hai cạnh đèn đã gán (551,266) |
| 5 | QC1-09 | A07 | traffic_sign #2, box (583,207)–(604,233) | chính | Biển hình thoi nhìn từ mặt sau (trống, màu xám): phải là `facing = back`, `group = other`; đang gán `front`, `prohibitory` |
| 6 | QC1-10 | A07 | traffic_sign (thiếu), khoảng (0,168)–(15,186) | chính | Bỏ sót biển cảnh báo hình thoi cam sát mép trái (kèm biển phụ nhỏ bên dưới) |
| 7 | QC1-07 | A07 | drivable #0, direct | chính | Vùng lái dừng ở đuôi xe phía trước (y ≈ 330), khoét quanh xe; phải kéo tiếp theo làn tới chỗ xa nhất còn thấy ("đi được nếu đường trống") |
| 8 | QC1-07 | B07 | drivable #0, direct | chính | Tràn sang làn xe đạp nền đỏ (góc dưới trái, có ký hiệu xe đạp); làn xe đạp không phải vùng lái của xe |
| 9 | QC1-12 | — | `nguyenhoainam-manifest.json` | nhẹ | Manifest không khớp file nhận được: ghi 16 + 12 ảnh, nhưng zip chỉ có 12 ảnh front (A01–A12) và 8 ảnh fisheye (B01–B08); `bytes` và `sha256` cả hai file đều không khớp. Cần export và tạo lại manifest |

Ảnh không có lỗi trong mẫu: **B03** (tag đúng `fisheye_rear`, R1 theo cung, edge_zone bật đúng cho biển xanh có tâm ngoài 80 % bán kính, đèn/biển đủ thuộc tính).

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A11 | drivable alternative bên phải phủ tới hàng xe đỗ sát lề; dải đỗ có tính vào alternative không? (guideline chỉ nói rõ cho `direct`) | |
| A04 | Biển nhìn từ mặt sau trên cột trái, khoảng (232,151)–(253,170), cao ~19 px, chưa gán. A04 có yêu cầu gán biển theo bảng kế hoạch ảnh không? | |
| A03 | R1 được kéo thẳng tới (975,680), xa hơn đoạn còn thấy vệt sơn (vệt gần nhất khoảng y = 465); có tính là sai điểm dừng phía gần không? | |

Các ca mơ hồ trên không làm đổi kết luận (đã có lỗi nặng), nên không Hold.

## Quyết định
Lỗi nặng: 1   Lỗi chính: 7 / 77 nhãn = 9,1 %   Lỗi nhẹ: 1   Ca chờ lead: 3  
Quyết định (Release / Hold / Rework): **Rework**  
Lý do (theo luật của phiếu): Còn 1 lỗi nặng (QC1-03 ở A11), và tỉ lệ lỗi chính 9,1 % vượt ngưỡng 5 % số nhãn đã kiểm. Mỗi điều kiện riêng đã đủ để Rework.

Đề nghị sửa: gộp vạch vàng đôi A11 thành một polyline L1 ở giữa hai nét và xóa L2 thừa; thêm đèn còn thiếu ở A03, A04; sửa facing/group biển A07 và thêm biển cảnh báo bị sót; kéo drivable A07 qua xe phía trước; bỏ phần làn xe đạp khỏi drivable B07; export lại và tạo manifest mới với `--revision 2`.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: thang mức lỗi ở `docs/qc_severity_road_v1.0.md`.
