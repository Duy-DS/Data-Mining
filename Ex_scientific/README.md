# Bài tập khoa học (Ex_scientific)

Thư mục này chứa các bài tập Python cơ bản sử dụng các thư viện khoa học như NumPy và Matplotlib.

## Danh sách bài tập

### 1. Máy tính cơ bản (ex1.calc)
- **Tệp tin**: `ex1.calc.py`, `ex1.calc.ipynb`
- **Mô tả**: Chương trình máy tính đơn giản thực hiện phép cộng hai số nguyên
- **Chức năng**: 
  - Nhập hai số từ người dùng
  - Thực hiện phép cộng
  - Hiển thị kết quả

### 2. Vẽ hình tròn ngẫu nhiên (ex2_scientific)
- **Tệp tin**: `ex2_scientific.ipynb`
- **Mô tả**: Trực quan hóa các hình tròn ngẫu nhiên sử dụng NumPy và Matplotlib
- **Chức năng**:
  - Tạo dữ liệu ngẫu nhiên cho tọa độ x, y
  - Tạo kích thước và màu sắc ngẫu nhiên cho các hình tròn
  - Vẽ biểu đồ scatter plot với các hình tròn có độ trong suốt

### 3. Tính chu vi và diện tích hình tròn (ex3_circle)
- **Tệp tin**: `ex3_circle.py`, `ex3_circle.ipynb`
- **Mô tả**: Chương trình tính toán chu vi và diện tích hình tròn
- **Chức năng**:
  - Nhập bán kính r từ người dùng
  - Tính chu vi: 2 × π × r
  - Tính diện tích: π × r × r
  - Hiển thị kết quả

### 4. Vẽ đồ thị hàm Sin và Cos (ex4_scientific)
- **Tệp tin**: `ex4_scientific.ipynb`
- **Mô tả**: Vẽ đồ thị các hàm lượng giác Sin và Cos với trục tọa độ tùy chỉnh
- **Chức năng**:
  - Tạo dữ liệu x từ -π đến π (256 điểm sử dụng numpy.linspace)
  - Tính giá trị Sin(x) và Cos(x)
  - Vẽ đồ thị với màu sắc khác nhau
  - Tùy chỉnh các nhãn trục với ký hiệu toán học (π, -π/2, π/2...)

## Yêu cầu

Để chạy các bài tập này, bạn cần cài đặt:
- Python 3
- NumPy
- Matplotlib

## Cách sử dụng

1. Để chạy các tệp `.py`:
   ```bash
   python ex1.calc.py
   python ex3_circle.py
   ```

2. Để chạy các tệp `.ipynb`:
   - Mở Jupyter Notebook
   - Điều hướng đến thư mục Ex_scientific
   - Mở tệp notebook mong muốn
   - Chạy các ô code
