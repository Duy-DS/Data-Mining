# Lab 03: Thực hành Thống kê Mô tả và Khám phá Dữ liệu

Thư mục này chứa các bài thực hành (Jupyter Notebooks) tập trung vào kỹ thuật **Thống kê mô tả (Descriptive Statistics)** và các bước đầu tiên trong quy trình **Tiền xử lý dữ liệu (Data Preprocessing)**.

Mục tiêu chính là hiểu rõ cấu trúc dữ liệu, kiểm tra tính toàn vẹn (dữ liệu thiếu, trùng lặp) và trực quan hóa cơ bản trên 4 bộ dữ liệu khác nhau.

## Danh sách các bài thực hành

### 1. Phân tích dữ liệu COVID-19 (`1.1.2.1_covid_data.ipynb`)
**Dữ liệu:** `covid_data.csv`
**Nội dung thực hiện:**
*   **Khởi tạo:** Import các thư viện cần thiết (`pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy`).
*   **Tải và xem tổng quan:** Đọc dữ liệu, hiển thị kích thước (shape), kiểu dữ liệu (`dtypes`), 5 dòng đầu/cuối.
*   **Kiểm tra tính toàn vẹn:**
    *   Kiểm tra dữ liệu trùng lặp: Không phát hiện dòng trùng lặp.
    *   Kiểm tra dữ liệu thiếu (Null/NaN): Phát hiện số lượng lớn dữ liệu thiếu (~50k dòng chứa null).
*   **Trực quan hóa:** Sử dụng **Heatmap** (biểu đồ nhiệt) của Seaborn để hiển thị vị trí các giá trị bị khuyết thiếu.
*   **Lựa chọn đặc trưng:** Tạo bản sao và chỉ giữ lại các cột quan trọng (`code`, `continent`, `country`, `date`, `total_cases`, `new_cases`).
*   **Thống kê:** Hiển thị các chỉ số thống kê cơ bản (mean, std, min, max, quartiles) cho các cột dữ liệu số.

### 2. Phân tích Chiến dịch Tiếp thị (`1.1.2.2_marketing_campaign.ipynb`)
**Dữ liệu:** `marketing_campaign.csv`
**Nội dung thực hiện:**
*   **Tải và xem tổng quan:** Đọc dữ liệu khách hàng, kiểm tra kích thước (2240 dòng, 29 cột) và kiểu dữ liệu.
*   **Kiểm tra tính toàn vẹn:**
    *   Kiểm tra trùng lặp: Không có dữ liệu trùng lặp.
    *   Kiểm tra dữ liệu thiếu: Phát hiện 24 giá trị thiếu, tập trung chủ yếu ở cột `Income` (Thu nhập).
*   **Thao tác:** Hiển thị chi tiết các dòng chứa dữ liệu thiếu để phục vụ việc xử lý sau này.

### 3. Phân tích Chất lượng Rượu vang Đỏ (`1.1.3_winequality.ipynb`)
**Dữ liệu:** `winequality-red.csv`
**Nội dung thực hiện:**
*   **Tải và xem tổng quan:** Đọc dữ liệu về các chỉ số hóa học của rượu vang (1599 dòng, 12 cột).
*   **Tiền xử lý:** Đổi tên các cột (Rename columns) để loại bỏ khoảng trắng, giúp việc truy xuất dữ liệu dễ dàng hơn (ví dụ: `fixed acidity` -> `fixed_acidity`).
*   **Kiểm tra tính toàn vẹn:**
    *   **Phát hiện trùng lặp:** Tìm thấy **460 dòng** dữ liệu trùng lặp (chiếm tỷ lệ lớn), cho thấy thực tế chỉ có khoảng 1139 mẫu rượu duy nhất.
    *   **Phát hiện dữ liệu thiếu:** Chỉ có 2 giá trị thiếu ở cột `citric_acid`.
*   **Trực quan hóa:** Sử dụng Heatmap để xem vị trí dữ liệu thiếu (dù số lượng rất ít).

### 4. Phân tích Dữ liệu Bệnh Tiểu đường (`1.1.4_diabetes.ipynb`)
**Dữ liệu:** `diabetes.csv`
**Nội dung thực hiện:**
*   **Tải và xem tổng quan:** Đọc dữ liệu y tế (770 dòng, 9 đặc trưng).
*   **Kiểm tra tính toàn vẹn:**
    *   **Phát hiện trùng lặp:** Tìm thấy 4 dòng dữ liệu bị trùng lặp.
    *   **Phát hiện dữ liệu thiếu:** Có 10 dòng chứa giá trị Null, phân bố ở các cột `BloodPressure`, `SkinThickness`, `Insulin`, và `BMI`.
*   **Trực quan hóa:**
    *   Sử dụng **Biểu đồ cột (Bar chart)** để so sánh số lượng giá trị thiếu giữa các đặc trưng, cho thấy `Insulin` là cột thiếu nhiều dữ liệu nhất trong nhóm bị thiếu.

---

## Môi trường và Thư viện
Dự án sử dụng Python và các thư viện phân tích dữ liệu tiêu chuẩn:
*   **Pandas:** Xử lý và thao tác DataFrame.
*   **NumPy:** Tính toán số học.
*   **Matplotlib & Seaborn:** Trực quan hóa dữ liệu (Vẽ biểu đồ Heatmap, Bar chart).
*   **SciPy:** Hỗ trợ các tính toán khoa học/thống kê.

## Tác giả
*   **Github:** [Duy-DS](https://github.com/Duy-DS)
