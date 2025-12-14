# Bài tập Scientific Programming (Python cơ bản & Trực quan hóa dữ liệu)

Thư mục này chứa các bài tập thực hành cơ bản về lập trình Python, sử dụng Jupyter Notebook và các thư viện tính toán khoa học như `numpy` và `matplotlib`.

## Danh sách bài tập

### 1. Máy tính cơ bản (Basic Calculator)
*   **Files:** `ex1.calc.ipynb`, `ex1.calc.py`
*   **Mô tả:**
    *   Chương trình yêu cầu người dùng nhập vào hai số nguyên `a` và `b`.
    *   Thực hiện phép tính tổng `c = a + b`.
    *   In kết quả ra màn hình theo định dạng `c = a + b = [kết quả]`.
    *   File notebook thực thi script python thông qua lệnh `%run`.

### 2. Trực quan hóa dữ liệu ngẫu nhiên (Random Circles Visualization)
*   **Files:** `ex2_scientific.ipynb`, `ex2_scientific.html`
*   **Mô tả:**
    *   Sử dụng thư viện `numpy` để sinh ngẫu nhiên dữ liệu cho `N=50` hình tròn:
        *   Tọa độ tâm $(x, y)$ trong khoảng $[0, 1]$.
        *   Màu sắc ngẫu nhiên.
        *   Diện tích ngẫu nhiên dựa trên bán kính.
    *   Sử dụng thư viện `matplotlib` (hàm `scatter`) để vẽ biểu đồ bong bóng (bubble chart) biểu diễn các hình tròn này với độ trong suốt `alpha=0.5`.

### 3. Tính toán hình học (Circle Calculator)
*   **Files:** `ex3_circle.ipynb`, `ex3_circle.py`
*   **Mô tả:**
    *   Chương trình tính Chu vi và Diện tích hình tròn.
    *   Yêu cầu người dùng nhập vào bán kính `r`.
    *   Sử dụng hằng số `pi = 3.14`.
    *   Công thức:
        *   Chu vi = $2 * \pi * r$
        *   Diện tích = $\pi * r^2$

### 4. Vẽ đồ thị hàm số lượng giác (Sin & Cos Plotting)
*   **Files:** `ex4_scientific.ipynb`
*   **Mô tả:**
    *   Vẽ đồ thị hai hàm số $sin(x)$ và $cos(x)$ trên cùng một hệ trục tọa độ.
    *   **Dữ liệu:** Tạo 256 điểm dữ liệu $X$ trong khoảng $[-\pi, \pi]$ bằng `numpy.linspace`.
    *   **Trực quan hóa:**
        *   Đường Cosine: Màu xanh (blue), nét liền.
        *   Đường Sine: Màu đỏ (red), nét liền.
    *   **Tùy chỉnh trục:** Thay đổi nhãn trục hoành (x-axis) để hiển thị các giá trị $\pi$ ($-\pi$, $-\pi/2$, $0$, $+\pi/2$, $+\pi$) thay vì số thực đơn thuần.

## Công nghệ sử dụng
*   **Ngôn ngữ:** Python 3
*   **Môi trường:** Jupyter Notebook
*   **Thư viện:**
    *   `numpy`: Xử lý mảng và sinh số ngẫu nhiên.
    *   `matplotlib`: Vẽ đồ thị và trực quan hóa dữ liệu.
