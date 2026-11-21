# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): Phu (nguyendinhphu200)   Người kiểm (học viên): Lê Hoàng Đức  
Ngày: 2026-11-21                          Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): `Anotation_Phu_front.xml`, `Anotation_Phu_fisheye.xml` (nhận dạng XML; chưa có manifest nên chưa có `revision`)  
Số ảnh kiểm: 6 (A03, A07, A10, A12, B05, B06) (+ 0 ảnh thêm, ghi riêng)   Số nhãn đã kiểm (shape + tag): 96 (72 shape + 24 tag)  

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 6 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 6 | 2 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 9 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 9 | 0 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 9 | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 9 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 6 | 2 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 17 | 0 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 40 | 1 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 23 | 0 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 2 | 2 | chính |
| QC1-12 file | lỗi file | 2 | 0 | nhẹ / nặng |

Ngoài bảng trên có 1 lỗi chính chưa có mã riêng (vạch ngựa vằn A12, xem danh sách lỗi dòng 6).

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-02 | A03 | `lane` (thiếu L1) | nặng | Vạch vàng liền ở bên trái làn đang đi thấy rõ nhưng không có polyline `lane`; chỉ có R1 và R2 |
| 2 | QC1-02 | A10 | `lane` (thiếu R1) | nặng | Vạch trắng liền ở góc dưới bên phải làn đang đi thấy rõ nhưng chưa vẽ; chỉ có L1 và L2 |
| 3 | QC1-09 | A03 | `traffic_sign` (hộp ~794,312) | chính | Biển công trường màu cam hình thoi gán `group = prohibitory`, đúng ra là `warning` |
| 4 | QC1-07 | A07 | `drivable` (direct) | chính | Vùng lái dừng ngay sau đuôi xe phía trước, không kéo tiếp lên đường ở xa (khoét xe) |
| 5 | QC1-07 | A10 | `drivable` (direct) | chính | Vùng lái chỉ nằm dưới xe phía trước, không kéo tiếp lên đường ở xa (khoét xe) |
| 6 | chưa có mã (hình) | A12 | `crosswalk` | chính | Vạch ngựa vằn bị tách: hai đầu có polygon, đoạn giữa không thuộc polygon `crosswalk` nào |
| 7 | QC1-11 | B05 | `drivable` (direct) | chính | Polygon có phần đuôi ở góc dưới bên phải lấn vào thân xe và vùng tối viền ảnh |
| 8 | QC1-11 | B06 | `drivable` (direct) | chính | Polygon có phần đuôi ở góc dưới bên phải lấn vào thân xe và vùng tối viền ảnh |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A07 | Đường trắng mảnh ở sát hàng rào bên trái làn đang đi có phải L1 không (có thể chỉ là vạch lề)? Nếu là L1 thì thêm 1 lỗi nặng QC1-02 | |
| A12 | Vạch ngựa vằn bị tách thành nhiều polygon: xếp vào mã nào (QC1-04, QC1-07 hay mã riêng cho crosswalk) và có tính là lỗi chính không? | |
| B05 | `drivable` direct và alternative chồng lên vùng vạch ngựa vằn: có cần cắt vùng crosswalk khỏi `drivable` không? | |

## Quyết định
Lỗi nặng: 2   Lỗi chính: 6 / 96 nhãn = 6,25 %   Lỗi nhẹ: 0   Ca chờ lead: 3 (không ảnh hưởng kết luận)  
Quyết định (Release / Hold / Rework): **Rework**  
Lý do (theo luật của phiếu): Có 2 lỗi nặng (thiếu L1 ở A03, thiếu R1 ở A10), mỗi lỗi nặng đã đủ để Rework. Ngoài ra lỗi chính 6/96 = 6,25 % (nếu bỏ ca chưa có mã ở A12 thì 5/96 = 5,2 %) cũng vượt ngưỡng 5 %. Ba ca mơ hồ không làm đổi kết luận nên không dùng Hold.

## Ghi chú cho người sửa
- Cách kiểm: vẽ nhãn của Phu chồng lên ảnh gốc rồi đối chiếu; chưa đo từng pixel nên độ lệch 5 px của polyline chưa được kiểm kỹ.
- Cần mở A03 và A10 trên CVAT để xác nhận hai vạch bị thiếu trước khi gửi phiếu.
- Chưa kiểm zip và manifest bàn giao (QC1-12), vì chỉ nhận hai file XML.
- Ngoài mẫu: B05, B06 có chung lỗi viền `drivable` sát thân xe; nên rà lại B07, B08 (camera trái/phải) và các ảnh khác, vì kiểu lỗi này có thể lặp lại.
- Ảnh thưởng A13–A16 và B09–B12 chưa được gán, không tính là lỗi.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).
