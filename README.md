# Báo cáo Phân tích I/O & Source Code Markdown

## I. Báo cáo Phân tích Input / Output (I/O)

1. **Input (Văn bản thô - Plain Text):**
   * Các câu lệnh, tên biến, đoạn mã Python, dữ liệu so sánh dạng bảng và danh sách kiểm tra.
   * Ký tự đặc biệt như `*` hoặc `#` nếu viết trực tiếp sẽ bị Markdown hiểu lầm là in nghiêng, in đậm hoặc tiêu đề (Heading).

2. **Output (Giao diện Render chuyên nghiệp):**
   * **Inline Code:** Các câu lệnh Terminal hoặc tên biến ngắn được bọc trong dấy backtick `` ` `` (ví dụ: `python main.py`) giúp phân biệt rõ nét với văn bản hướng dẫn thường.
   * **Code Block:** Đoạn mã Python lập trình máy bơm được đặt trong khối mã có chỉ định ngôn ngữ `python` để kích hoạt **Syntax Highlighting** (tô màu cú pháp).
   * **Bảng (Table):** Cấu trúc cột/dòng rõ ràng, canh đều giúp so sánh trực quan giữa cảm biến cũ và mới.
   * **Task List:** Danh sách công việc có ô tích `- [ ]` và `- [x]` tiện cho việc quản lý quy trình lắp đặt.
   * **Ký tự Escape (`\`):** Sử dụng dấu gạch chéo ngược `\` trước các ký tự `\*` hoặc `\#` để hiển thị nguyên bản ký tự mà không bị lỗi định dạng.

---

## II. Source Code Markdown Hoàn chỉnh

```markdown
# Hướng dẫn Cài đặt Cảm biến Độ ẩm cho Trang trại Lan

Tài liệu này hướng dẫn thiết lập cảm biến độ ẩm tự động. Vui lòng thực hiện đúng theo các bước bên dưới.

## 1. Cài đặt môi trường & Cấu hình

Mở Terminal và chạy câu lệnh `pip install orchid-sensor` để cài đặt thư viện điều khiển. 

* *Lưu ý:* Giá trị ngưỡng độ ẩm mặc định được lưu trong biến `HUMIDITY_THRESHOLD`. Nếu cần hiển thị ký tự đặc biệt như mã thiết bị \#1 hay ký hiệu \*chú ý\*, ta sử dụng dấu escape `\`.

## 2. Mã nguồn điều khiển máy bơm (Python)

Đoạn code bên dưới tự động kích hoạt máy bơm khi độ ẩm xuống dưới 60%:

```python
import time
from sensor_library import HumiditySensor

sensor = HumiditySensor(pin=4)
HUMIDITY_THRESHOLD = 60.0

def check_and_pump():
    current_humidity = sensor.read()
    print(f"Độ ẩm hiện tại: {current_humidity}%")
    
    if current_humidity < HUMIDITY_THRESHOLD:
        print("Độ ẩm thấp! Đang bật máy bơm tưới lan...")
        # Lệnh bật máy bơm
    else:
        print("Độ ẩm đạt chuẩn. Tắt máy bơm.")

if __name__ == "__main__":
    check_and_pump()
```

## 3. Bảng so sánh Cảm biến Độ ẩm

| Tiêu chí | Cảm biến cũ (DHT11) | Cảm biến mới (Capacitive v1.2) |
| :--- | :--- | :--- |
| **Độ chính xác** | $\pm 5\%$ | $\pm 2\%$ |
| **Chống ăn mòn** | Kém (dễ gỉ sét) | Cao (Cảm ứng điện dung) |
| **Tuổi thọ** | 3 - 6 tháng | 12 - 24 tháng |
| **Giá thành** | Rẻ | Trung bình |

## 4. Danh sách công việc kiểm tra (Task List)

- [x] Kiểm tra nguồn điện 5V cấp cho cảm biến
- [x] Kết nối chân Signal vào cổng GPIO 4 của Raspberry Pi
- [ ] Chạy file script thử nghiệm `python test_sensor.py`
- [ ] Kiểm tra hệ thống van phun sương tự động
```
