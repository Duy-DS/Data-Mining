# Báo cáo Thực hành Lab 04: Classification & Feature Engineering

Kho chứa này bao gồm các bài tập thực hành (Lab 04) thuộc môn học Khai phá dữ liệu (Data Mining). Các notebook tập trung vào việc áp dụng các thuật toán phân loại (Classification), kỹ thuật trích chọn đặc trưng (Feature Engineering), xử lý dữ liệu thiếu (Missing Values) và trực quan hóa dữ liệu đa chiều.

## Mục lục

1. [Phân loại Iris với Naive Bayes](#1-phân-loại-iris-với-naive-bayes)
2. [Kỹ thuật đặc trưng (Feature Engineering)](#2-kỹ-thuật-đặc-trưng-feature-engineering)
3. [Phân loại chữ số viết tay (MNIST) với Logistic Regression](#3-phân-loại-chữ-số-viết-tay-mnist-với-logistic-regression)
4. [Xử lý dữ liệu thiếu (Missing Values) trên tập Titanic](#4-xử-lý-dữ-liệu-thiếu-missing-values-trên-tập-titanic)
5. [Phân loại Rượu vang với Decision Tree & Trực quan hóa](#5-phân-loại-rượu-vang-với-decision-tree--trực-quan-hóa)

---

### 1. Phân loại Iris với Naive Bayes
**File:** `Lab04/Ex1.1_Classification_Iris_NaiveBayes.ipynb`

Thực hiện phân loại 3 loài hoa Iris (Setosa, Versicolor, Virginica) dựa trên các đặc trưng về đài hoa và cánh hoa.

*   **Dữ liệu:** Iris dataset từ `sklearn.datasets`.
*   **Các bước thực hiện:**
    *   Tải và khám phá dữ liệu, chuyển đổi sang Pandas DataFrame.
    *   Chia tập dữ liệu thành tập huấn luyện (Train) và tập kiểm thử (Test) với tỷ lệ 80/20.
    *   Xây dựng mô hình **Gaussian Naive Bayes**.
    *   Đánh giá độ chính xác (Accuracy): Đạt ~97% trên tập train và 93% trên tập test.
    *   **Trực quan hóa:** Sử dụng PCA (Principal Component Analysis) để giảm chiều dữ liệu xuống 2D và vẽ biểu đồ phân tán (scatter plot) kết quả dự đoán.

### 2. Kỹ thuật đặc trưng (Feature Engineering)
**File:** `Lab04/ex1.1_FeatureEngineering.ipynb`

Nghiên cứu ảnh hưởng của các phương pháp biến đổi đặc trưng khác nhau đối với hiệu suất của mô hình phân loại (Random Forest) trên tập dữ liệu Iris.

*   **Các phương pháp áp dụng:**
    1.  **StandardScaler:** Chuẩn hóa dữ liệu (mean=0, variance=1).
    2.  **PCA (Principal Component Analysis):** Giảm chiều dữ liệu tuyến tính.
    3.  **ICA (Independent Component Analysis):** Tách các nguồn tín hiệu độc lập (sử dụng `FastICA`).
    4.  **Genetic Programming (GP):** Sử dụng `SymbolicTransformer` (thư viện `gplearn`) để tạo ra các đặc trưng phi tuyến tính mới thông qua tiến hóa di truyền.
*   **Kết quả:**
    *   So sánh độ chính xác của mô hình RandomForest trước và sau khi áp dụng các kỹ thuật biến đổi.
    *   Trực quan hóa không gian đặc trưng mới sau khi biến đổi.

### 3. Phân loại chữ số viết tay (MNIST) với Logistic Regression
**File:** `Lab04/Ex2.1_Classification_MNIS_Logistic_Regression.ipynb`

Xây dựng mô hình nhận diện chữ số viết tay (từ 0 đến 9) sử dụng tập dữ liệu MNIST (phiên bản nhỏ trong sklearn).

*   **Dữ liệu:** Digits dataset (ảnh 8x8 pixel).
*   **Các bước thực hiện:**
    *   Trực quan hóa các mẫu chữ số trong tập dữ liệu.
    *   Sử dụng PCA để trực quan hóa phân bố dữ liệu trong không gian 2D.
    *   Tiền xử lý: Làm phẳng (Flatten) hình ảnh từ ma trận 2D thành vector 1D.
    *   Huấn luyện mô hình **Logistic Regression** (với L2 penalty).
    *   **Đánh giá:**
        *   Hiển thị hình ảnh và nhãn dự đoán thực tế.
        *   Sử dụng `classification_report` (Precision, Recall, F1-score).
        *   Vẽ **Confusion Matrix** để phân tích các trường hợp dự đoán sai.

### 4. Xử lý dữ liệu thiếu (Missing Values) trên tập Titanic
**File:** `Lab04/ex2.1_MissingValues.ipynb`

Hướng dẫn cách xử lý dữ liệu bị khuyết (NaN) và mã hóa dữ liệu phân loại trên tập dữ liệu Titanic thực tế.

*   **Dữ liệu:** Titanic dataset tải từ OpenML.
*   **Các vấn đề xử lý:**
    *   Xác định các ký tự đại diện cho dữ liệu thiếu (ví dụ: '?').
    *   Loại bỏ các cột không quan trọng (name, ticket, boat, body...).
    *   Xử lý lỗi khi mô hình không thể chạy với dữ liệu chuỗi (String).
    *   Sử dụng **OrdinalEncoder** để mã hóa các cột phân loại (`sex`, `cabin`) trong khi vẫn giữ nguyên các giá trị `NaN` để phục vụ cho các bước bù khuyết (imputation) sau này.

### 5. Phân loại Rượu vang với Decision Tree & Trực quan hóa
**File:** `Lab04/ex3.1_eg_plot_3_features.ipynb` & `Lab04/Ex3.1_Ex3_Classification_Wine_DecisionTree.ipynb`

Phân loại 3 loại rượu vang dựa trên các thành phần hóa học và thực hiện trực quan hóa dữ liệu trong không gian 3 chiều.

*   **Dữ liệu:** Wine dataset.
*   **Trực quan hóa:**
    *   Vẽ biểu đồ Scatter plot 2D giữa các cặp đặc trưng.
    *   Vẽ biểu đồ **3D Scatter plot** sử dụng `matplotlib` để quan sát sự phân bố của 3 đặc trưng: *Total Phenols, Color Intensity, OD280/OD315*.
*   **Mô hình hóa:**
    *   Xây dựng mô hình **Decision Tree Classifier** (Cây quyết định).
    *   Thiết lập tham số `max_depth=4` để tránh overfitting.

---

## Yêu cầu cài đặt

Để chạy các notebook này, bạn cần cài đặt môi trường Python với các thư viện sau:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn gplearn plotly
