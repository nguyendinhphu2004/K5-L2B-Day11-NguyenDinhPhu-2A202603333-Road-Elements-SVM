# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): Lê Hoàng Đức-2A202603334 Người kiểm (học viên): Nguyễn Đình Phú-2A202603333
Ngày: 21/11/2026 Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): `LeHoangDuc_front.zip`, `LeHoangDuc_fisheye.zip`
Số ảnh kiểm: 6 Số nhãn đã kiểm (shape + tag): 102  
Ảnh kiểm: A01 (13), A04 (18), A08 (34), A10 (20), B02 (9), B05 (8)

## Tổng hợp theo mã

| Mã                                   | Loại lỗi                              | Số mục kiểm | Số lỗi | Mức            |
| ------------------------------------ | ------------------------------------- | ----------: | -----: | -------------- |
| QC1-01 tag camera                    | sai thuộc tính / bỏ sót               |           6 |      0 | nặng           |
| QC1-02 đủ L1, R1                     | bỏ sót                                |           5 |      0 | nặng           |
| QC1-03 position                      | sai thuộc tính / thừa                 |          18 |      1 | nặng           |
| QC1-04 tâm vạch, chiều, điểm dừng    | sai phạm vi / bỏ sót                  |          18 |      0 | chính          |
| QC1-05 vạch đứt, che                 | sai phạm vi / sai thuộc tính          |          18 |      1 | chính          |
| QC1-06 style, color, kind            | sai thuộc tính                        |          18 |      1 | chính          |
| QC1-07 vùng lái                      | sai phạm vi / bỏ sót / thừa           |          17 |      0 | chính          |
| QC1-08 đèn, màu                      | bỏ sót / sai phạm vi / sai thuộc tính |          11 |      5 | chính          |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính                        |          35 |      0 | chính          |
| QC1-10 hình in, đủ biển              | bỏ sót / sai phạm vi                  |          24 |      6 | 5 chính, 1 nhẹ |
| QC1-11 fisheye                       | sai phạm vi / sai thuộc tính          |           9 |      1 | chính          |
| QC1-12 file                          | lỗi file                              |           2 |      0 | nhẹ / nặng     |

## Danh sách lỗi (mỗi lỗi một dòng)

| #   | Mã     | Ảnh | Nhãn (label, id)      | Mức   | Mô tả ngắn                                                                                          |
| --- | ------ | --- | --------------------- | ----- | --------------------------------------------------------------------------------------------------- |
| 1   | QC1-03 | A04 | lane #2               | nặng  | Vạch trắng bên phải (1276,528)→(667,334) gán L2; đúng là R2                                         |
| 2   | QC1-05 | A04 | lane #5               | chính | Vàng đôi bị tách 2 polyline (#4 double + #5 single, cùng L1); xoá #5, giữ một polyline giữa hai nét |
| 3   | QC1-06 | A01 | lane #6               | chính | L2 sát lề trái là trắng đôi (phóng to thấy 2 nét), đang gán yellow / single                         |
| 4   | QC1-08 | A08 | traffic_light (thiếu) | chính | Bỏ sót đèn xanh (648,210)–(658,221), cao 11 px                                                      |
| 5   | QC1-08 | A08 | traffic_light (thiếu) | chính | Bỏ sót đèn xanh (603,202)–(611,215), cao 13 px                                                      |
| 6   | QC1-08 | A08 | traffic_light #13     | chính | Box (518,179)–(540,203) gộp 2 cụm đèn sát nhau; tách thành 2 box                                    |
| 7   | QC1-08 | A10 | traffic_light (thiếu) | chính | Bỏ sót đèn đỏ (560,196)–(568,209), cao 13 px                                                        |
| 8   | QC1-08 | B02 | traffic_light (thiếu) | chính | Bỏ sót cụm đèn góc trên phải (1087,22)–(1200,195)                                                   |
| 9   | QC1-10 | A08 | traffic_sign (thiếu)  | chính | Bỏ sót biển cấm trên cột phải (991,184)–(1012,216)                                                  |
| 10  | QC1-10 | A08 | traffic_sign (thiếu)  | chính | Bỏ sót biển cấm (991,216)–(1012,248)                                                                |
| 11  | QC1-10 | A10 | traffic_sign (thiếu)  | chính | Bỏ sót biển NO PARKING (47,48)–(91,81)                                                              |
| 12  | QC1-10 | A10 | traffic_sign (thiếu)  | chính | Bỏ sót biển NO STANDING (48,80)–(91,127)                                                            |
| 13  | QC1-10 | A10 | traffic_sign (thiếu)  | chính | Bỏ sót biển cấm đỗ "P" (49,137)–(94,170)                                                            |
| 14  | QC1-10 | A10 | traffic_sign #8       | nhẹ   | Box cao 7 px (< 8 px, không bắt buộc); nên xoá                                                      |
| 15  | QC1-11 | B02 | traffic_light #3      | chính | Tâm box (132,164) nằm ngoài 80 % bán kính → edge_zone phải bật                                      |

Ảnh không lỗi: B05 (camera trái: lane other, crosswalk, road_curb, drivable đều đúng).

## Ca mơ hồ

| Ảnh | Câu hỏi cho lead                                                                                                            | Lời đáp (nếu có) |
| --- | --------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| A08 | L1 tách 2 polyline (#1 solid + #2 dashed) vì vạch đổi kiểu liền → đứt gần giao lộ: chấp nhận hay phải gộp? (không tính lỗi) |                  |
| A10 | Tag weather = clear trong khi mặt đường ướt rõ do mưa (guideline: rain); tag này không có mã QC riêng                       |                  |

## Quyết định

Lỗi nặng: 1 Lỗi chính: 13 / 102 nhãn = 12,7 % Lỗi nhẹ: 1 Ca chờ lead: 2  
Quyết định (Release / Hold / Rework): Rework
Lý do (theo luật của phiếu): còn 1 lỗi nặng (QC1-03 ở A04) và tỉ lệ lỗi chính 12,7 % > 5 %. Ưu tiên sửa: position A04, đèn/biển bỏ sót ở A08–A10, edge_zone B02. Ghi chú: B09–B12 (ảnh thêm) chưa gán, không tính lỗi.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm.
