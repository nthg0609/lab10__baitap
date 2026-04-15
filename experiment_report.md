# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-XXXX
**Name:** (Dien ten cua ban)
**Date:** (Dien ngay thuc hien)

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Based on my data, the best choice is Laptop at $1200. | 10 | |
| Garbage Data (`garbage_data.csv`) | Based on my data, the best choice is Nuclear Reactor at $999999. | 1 | |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi Agent phải xử lý tập dữ liệu rác (Garbage Data), kết quả trả về thường sai lệch hoặc hệ thống bị lỗi (crash) vì những nguyên nhân cốt lõi sau:
- Null Values (Dữ liệu trống): Nếu các cột quan trọng như doanh thu hoặc số lượng bị thiếu, Agent khi thực hiện các phép toán tổng hợp (Sum, Average) sẽ bị bỏ sót dữ liệu hoặc báo lỗi tính toán (Ví dụ: lỗi chia cho 0 hoặc lỗi NullReference).
- Duplicate IDs (Trùng lặp mã định danh): Mã ID là duy nhất để định danh một bản ghi (như một hóa đơn hay một người dùng). Khi ID bị trùng, Agent có thể đếm đúp (double-counting) doanh thu hoặc nhận diện sai khách hàng, dẫn đến kết quả tổng hợp bị thổi phồng một cách vô lý.
- Wrong Data Types (Sai kiểu dữ liệu): Một cột yêu cầu định dạng số (Integer/Float) nhưng lại chứa ký tự chữ (String) hoặc ngày tháng không hợp lệ. Khi Agent cố gắng áp dụng các hàm toán học lên cột chuỗi, hệ thống sẽ ném ra lỗi (Type Error) và dừng hoạt động.
- Outliers (Dữ liệu ngoại lai): Những giá trị lớn/nhỏ bất thường (ví dụ: tuổi = 999 hoặc số lượng mua = -5) làm sai lệch nghiêm trọng các chỉ số thống kê trung bình, khiến Agent đưa ra kết luận kinh doanh sai lầm, mất đi tính thực tế.

---

## 3. Ket luan

**Quality Data > Quality Prompt?**

Hoàn toàn đồng ý (Yes).
Trong hệ thống Data AI, "Garbage In, Garbage Out" (GIGO) là nguyên tắc bất di bất dịch. Một Prompt xuất sắc đến mấy cũng chỉ là bộ hướng dẫn tư duy; nếu Data đầu vào đã sai lệch, trùng lặp hoặc chứa nhiễu, thì kết luận đầu ra chắc chắn không thể chính xác. Chất lượng dữ liệu (Quality Data) mới là nền tảng quyết định độ tin cậy của bất kỳ mô hình AI nào, trong khi Quality Prompt chỉ giúp AI biểu đạt hoặc truy xuất dữ liệu đó tốt hơn mà thôi.
