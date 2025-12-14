# Lab01b: Cơ bản và Nâng cao về Python & Numpy

Thư mục này chứa các bài thực hành và bài tập về ngôn ngữ lập trình Python, từ các cú pháp cơ bản đến các kỹ thuật nâng cao như xử lý file, lập trình hướng đối tượng (OOP) và tính toán khoa học với thư viện Numpy.

## Danh sách các file

### 1. `01_python_basic.ipynb`
File này giới thiệu các kiến thức nền tảng của Python:
- **Khai báo thư viện**: Cách `import` module.
- **Toán tử cơ bản**: Các phép toán số học và logic.
- **Kiểu dữ liệu**:
  - **List**: Các thao tác thêm, sửa, xóa, slicing, list comprehension.
  - **Tuple**: Khởi tạo và sử dụng tuple.
  - **String**: Các phương thức xử lý chuỗi phổ biến.
  - **Dictionary**: Lưu trữ dữ liệu dạng key-value, truy xuất an toàn với `get`.
  - **Set**: Các phép toán tập hợp (hợp, giao, hiệu).
- **Nhập/Xuất dữ liệu**: Sử dụng `input()` và `print()`.
- **Cấu trúc điều khiển**: Câu lệnh `if-else`, vòng lặp `for`, `while`.
- **Hàm (Functions)**: Định nghĩa hàm, tham số mặc định.
- **Xử lý ngoại lệ**: Cấu trúc `try-except`.

### 2. `02_python_advance.ipynb`
File này đi sâu vào các chủ đề nâng cao và thư viện Numpy:
- **Xử lý tập tin và thư mục**:
  - Sử dụng thư viện `os`, `shutil`, `glob`, `tempfile`.
  - Tạo, xóa, sao chép, di chuyển file/thư mục.
  - Duyệt cây thư mục với `os.walk`.
- **Lập trình hướng đối tượng (OOP)**:
  - Khái niệm Class, Object.
  - Tính kế thừa (Inheritance) và Đa hình (Polymorphism) qua ví dụ hình học (`Shape2D`, `Square`, `Disk`).
- **Numpy - Thư viện tính toán khoa học**:
  - Tạo mảng (array) từ list, tạo mảng đặc biệt (`zeros`, `ones`, `linspace`, `arange`).
  - Kiểm tra thuộc tính mảng (`shape`, `ndim`, `dtype`).
  - Biến đổi hình dạng (`reshape`, `flatten`, `ravel`, `transpose`).
  - Truy xuất và cắt lát mảng (Slicing, Fancy indexing, Boolean indexing).
  - Ghép mảng (`hstack`, `vstack`).

### 3. `03_exercise_01.ipynb`
Bài tập vận dụng kiến thức cơ bản của Python:
- **Nhập xuất & Tính toán**:
  - Tính giá trị hàm số $f(x)$.
  - Đổi giây sang giờ:phút:giây.
- **Cấu trúc lựa chọn**:
  - Giải phương trình bậc 1.
  - Kiểm tra và chuyển đổi ký số tiếng Anh sang tiếng Việt.
- **Vòng lặp**:
  - Tính tổng số chẵn.
  - Kiểm tra số nguyên tố.
- **Hàm & Xử lý ngoại lệ**:
  - Giải phương trình bậc 2 với kiểm tra đầu vào hợp lệ.
- **Cấu trúc dữ liệu nâng cao**:
  - Thao tác trên mảng số: sinh ngẫu nhiên, tính tổng chẵn/lẻ, tách mảng.
  - Xử lý chuỗi ký tự: đếm tần suất xuất hiện (dùng Dictionary), lọc ký tự không trùng (dùng Set).

### 4. `04_exercise_02.ipynb`
Bài tập thực hành kỹ thuật lập trình với Numpy và Matplotlib:
- **Thao tác trên dãy số**:
  - Bình phương, tìm min/max/mean.
  - Tính phương sai và độ lệch chuẩn.
  - Tính khoảng cách giữa các phần tử của hai dãy số.
  - Tìm khoảng cách nhỏ nhất giữa hai tập hợp (Broadcasting).
- **Sinh ngẫu nhiên & Vẽ đồ thị**:
  - Phân phối đều và đồ thị tần số.
  - Phân phối chuẩn $N(\mu, \sigma)$ và vẽ đồ thị hàm mật độ/tần suất.
- **Thao tác trên ma trận**:
  - Chuyển vị, trích xuất dòng/cột.
  - Các phép toán ma trận: cộng, trừ, nhân từng phần tử, tích vô hướng (dot product).
- **Giải hệ phương trình tuyến tính**: Sử dụng `np.linalg.solve`.
- **Bài tập áp dụng**:
  - Tính gần đúng số PI bằng phương pháp Monte Carlo.
