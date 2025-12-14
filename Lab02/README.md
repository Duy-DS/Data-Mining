# Phân tích Dữ liệu Bệnh Đái tháo đường Pima Indians (Lab 02)

Dự án này thực hiện phân tích khám phá dữ liệu (Exploratory Data Analysis - EDA) trên bộ dữ liệu **Pima Indians Diabetes**. Mục tiêu là tìm hiểu các đặc điểm dữ liệu, kiểm tra tính toàn vẹn và xác định mối tương quan giữa các chỉ số y tế với khả năng mắc bệnh tiểu đường.

## 📂 Cấu trúc thư mục

*   **`pima-indians-diabetes.csv`**: Bộ dữ liệu gốc chứa các chỉ số sức khỏe của 768 phụ nữ người Pima Indian.
*   **`pima-indians-diabetes.ipynb`**: Jupyter Notebook chứa toàn bộ mã nguồn Python dùng để xử lý, phân tích và trực quan hóa dữ liệu.

## 📊 Thông tin về bộ dữ liệu

*   **Nguồn dữ liệu**: Viện Quốc gia về Bệnh Đái tháo đường và Tiêu hóa và Bệnh Thận.
*   **Đối tượng**: Phụ nữ từ 21 tuổi trở lên, thuộc dòng dõi Pima Indian.
*   **Kích thước**: 768 dòng (mẫu) và 9 cột (đặc trưng).

### Các thuộc tính (Features):
1.  **Pregnancies**: Số lần mang thai.
2.  **Glucose**: Nồng độ đường huyết sau 2 giờ uống dung dịch glucose.
3.  **BloodPressure**: Huyết áp tâm trương (mm Hg).
4.  **SkinThickness**: Độ dày nếp gấp da cơ tam đầu (mm).
5.  **Insulin**: Nồng độ insulin huyết thanh trong 2 giờ (mu U/ml).
6.  **BMI**: Chỉ số khối cơ thể (cân nặng tính bằng kg / (chiều cao tính bằng m)^2).
7.  **DiabetesPedigreeFunction**: Chức năng phả hệ bệnh tiểu đường (di truyền).
8.  **Age**: Tuổi (năm).
9.  **Class (Target)**: Biến mục tiêu (0: Không bị tiểu đường, 1: Bị tiểu đường).

## 🛠️ Các bước thực hiện trong Notebook

### 1. Chuẩn bị môi trường
*   Khai báo các thư viện cần thiết cho phân tích dữ liệu và học máy:
    *   `pandas`, `numpy`: Xử lý bảng dữ liệu và toán học.
    *   `matplotlib`, `seaborn`: Trực quan hóa dữ liệu.
    *   `sklearn`: Các công cụ tiền xử lý (MinMaxScaler, StandardScaler...).

### 2. Nạp và kiểm tra sơ bộ dữ liệu
*   Đọc dữ liệu từ file CSV.
*   Gán tên cột chính xác cho DataFrame.
*   Hiển thị kích thước (`shape`), kiểu dữ liệu (`dtypes`) và xem trước 5 dòng đầu/cuối để nắm cấu trúc bảng.

### 3. Kiểm tra tính toàn vẹn dữ liệu (Data Integrity)
*   **Kiểm tra trùng lặp**: Xác nhận không có dòng dữ liệu nào bị trùng lặp.
*   **Kiểm tra giá trị thiếu**: Xác nhận không có giá trị `Null` hoặc `NaN` trong bộ dữ liệu.
    *   *Kết quả*: Dữ liệu sạch về mặt kỹ thuật, không cần xử lý điền khuyết hay loại bỏ dòng trùng.

### 4. Thống kê mô tả (Descriptive Statistics)
*   Tính toán các chỉ số thống kê cơ bản cho các biến số:
    *   Đếm (Count), Trung bình (Mean), Độ lệch chuẩn (Std).
    *   Giá trị nhỏ nhất (Min), lớn nhất (Max).
    *   Các điểm phân vị (25%, 50% - Median, 75%).

### 5. Phân tích phân lớp (Class Distribution)
*   Kiểm tra sự phân bố của biến mục tiêu `class`.
*   *Kết quả*:
    *   Lớp 0 (Không tiểu đường): 500 mẫu.
    *   Lớp 1 (Tiểu đường): 268 mẫu.
    *   => Có sự mất cân bằng dữ liệu (imbalance) nhưng ở mức độ vừa phải.

### 6. Phân tích tương quan (Correlation Analysis)
*   Sử dụng hệ số tương quan **Pearson** để đánh giá mối quan hệ tuyến tính giữa các biến.
*   Trực quan hóa bằng biểu đồ nhiệt (**Heatmap**).
*   *Nhận định quan trọng*:
    *   **Glucose** là yếu tố quan trọng nhất, có tương quan cao nhất với biến mục tiêu (`class`).
    *   **BMI**, **Age**, **Pregnancies** cũng có ảnh hưởng đáng kể.
    *   Có sự chồng chéo (đa cộng tuyến) giữa `SkinThickness`, `BMI` và `Insulin`.

## 🚀 Hướng dẫn sử dụng
Để chạy notebook này, bạn cần cài đặt môi trường Python với các thư viện sau:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

Sau đó mở file notebook:
```bash
jupyter notebook pima-indians-diabetes.ipynb
```
