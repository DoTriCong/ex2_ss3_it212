# BÀI 2: Tối ưu Prompt (Thiết kế Prompt Tóm tắt & Hệ thống hóa Tài liệu học tập)

## Prompt sau khi tối ưu
"Hãy đóng vai là một Giảng viên Java giàu kinh nghiệm giảng dạy trực quan. Tóm tắt đoạn văn bản về Garbage Collection trong Java thành một **bảng so sánh** giữa Young Generation và Old Generation theo các tiêu chí: (1) Các vùng con bên trong, (2) Loại đối tượng lưu trữ, (3) Điều kiện kích hoạt GC, (4) Tốc độ thực thi của GC. Sau đó, hãy cung cấp thêm một **sơ đồ ASCII đơn giản** để trực quan hóa đường đi của một đối tượng từ khi được khởi tạo bằng `new` cho tới khi được thăng cấp lên Old Generation."

---

## Phản hồi từ AI sau khi chạy thử Prompt tối ưu

### Bảng so sánh Young Generation vs Old Generation

| Tiêu chí                  | Young Generation                                                                 | Old Generation                                      |
|---------------------------|----------------------------------------------------------------------------------|-----------------------------------------------------|
| **Các vùng con bên trong** | Eden Space, Survivor S0, Survivor S1                                             | Không chia nhỏ, toàn bộ vùng Old Generation          |
| **Loại đối tượng lưu trữ** | Đối tượng mới tạo, có vòng đời ngắn                                               | Đối tượng sống lâu, tồn tại qua nhiều lần Minor GC   |
| **Điều kiện kích hoạt GC** | Eden đầy → Minor GC; đối tượng sống sót được chuyển sang Survivor, sau nhiều lần sẽ được thăng cấp | Old Generation đầy → Major GC hoặc Full GC           |
| **Tốc độ thực thi GC**    | Nhanh hơn, chỉ quét vùng Young Generation                                        | Chậm hơn, phải duyệt toàn bộ Heap, gây "Stop-the-world" |

---

### Sơ đồ ASCII trực quan hóa vòng đời đối tượng

new Object
|
v
Eden Space
|
| (Minor GC - đối tượng sống sót)
v
Survivor S0/S1
|
| (Qua nhiều lần Minor GC, đạt ngưỡng tuổi)
v
Old Generation
|
| (Major/Full GC khi đầy)
v
Thu hồi bộ nhớ

---

## Kết luận
Prompt tối ưu đã giúp AI:  
- Đóng vai giảng viên → giải thích trực quan, dễ hiểu.  
- Tóm tắt bằng bảng so sánh → hệ thống hóa kiến thức rõ ràng.  
- Bổ sung sơ đồ ASCII → trực quan hóa đường đi của đối tượng, dễ ghi nhớ.  
