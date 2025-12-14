# Dự án: Phân loại loài hoa Iris (Lab05)

Ngôn ngữ: Tiếng Việt  
Mục tiêu: Xây dựng và so sánh các mô hình học máy để dự đoán loài hoa Iris dựa trên 4 đặc trưng số (sepal-length, sepal-width, petal-length, petal-width).

---

## Tổng quan các tệp chính trong thư mục Lab05

- `Iris_Oct15th.ipynb`  
  Notebook chuẩn bị dữ liệu và phân tích khám phá dữ liệu (EDA).
- `Iris_Model_01.ipynb`  
  Notebook thử nghiệm các mô hình phân loại đa lớp, so sánh hiệu năng (baseline và phiên bản chuẩn hoá).
- `Iris_Model_02.ipynb`  
  Template/placeholder cho các thử nghiệm mô hình hồi quy / các mô hình bổ sung (hiện tại còn thiếu phần hoàn thiện).

Ngoài ra các file kết quả (được lưu trong thư mục `exp/` theo notebook):
- `exp/data.npz`  — chứa các mảng numpy: X_train, X_test, y_train, y_test
- `exp/df_clean.csv` — DataFrame đã làm sạch lưu lại
- `exp/class_encoder.joblib` — bộ mã hoá nhãn lớp (LabelEncoder hoặc tương đương)

---

## Môi trường và thư viện cần thiết

Tốt nhất sử dụng Python 3 (notebook được chạy với kernel Python 3). Các thư viện chính:
- numpy
- pandas
- scikit-learn
- matplotlib
- seaborn
- joblib
- PIL (để tải ảnh minh họa)
- ipython (jupyter)

Phiên bản cụ thể không bắt buộc nhưng notebook sử dụng các API chuẩn của scikit-learn (LogisticRegression, KFold, cross_val_score, Pipeline, StandardScaler, v.v.).

---

## Chi tiết nội dung thực hiện trong từng notebook

### 1) Iris_Oct15th.ipynb — Chuẩn bị & EDA
Nội dung chính:
- Đọc dữ liệu từ `iris.csv` với các cột: `sepal-length, sepal-width, petal-length, petal-width, class`.
- Hiển thị thông tin cơ bản:
  - Shape: (150, 5)
  - Kiểm tra kiểu dữ liệu, hiển thị head/tail, df.info().
- Kiểm tra dữ liệu thiếu (NaN/Null) — KẾT LUẬN: không có giá trị thiếu.
- Kiểm tra hàng trùng lặp — phát hiện một số dòng trùng lặp (ví dụ: hàng 9/34/37 giống nhau; 101/142 giống nhau) và hiển thị chi tiết các bản ghi trùng.
- Thống kê mô tả (describe) cho các đặc trưng số: mean, std, min/max, percentiles.
- Phân phối lớp mục tiêu:
  - Ba lớp cân bằng: mỗi lớp 50 mẫu (Iris-setosa, Iris-versicolor, Iris-virginica).
- Ma trận tương quan Pearson giữa các đặc trưng:
  - petal-length và petal-width có tương quan rất cao (~0.963).
  - sepal-length tương quan cao với petal-length (~0.872) và petal-width (~0.818).
- Hiển thị ảnh minh họa của 3 loài Iris (sử dụng file ảnh địa phương).

Ý nghĩa & hành động:
- Dữ liệu sạch, không thiếu, phân lớp cân bằng — thuận lợi cho huấn luyện mô hình.
- Một vài bản ghi trùng lặp được phát hiện (tùy chọn có thể loại bỏ).
- Tương quan cao giữa petal-length và petal-width cho thấy các đặc trưng này rất phân biệt các loài.

---

### 2) Iris_Model_01.ipynb — Thử nghiệm mô hình phân loại (Baseline và Standardization)
Nội dung chính:
- Phục hồi (load) các artifact đã lưu:
  - `exp/data.npz` → X_train, X_test, y_train, y_test  
    (Ví dụ trong đầu ra: X_train shape (102, 4), X_test shape (45, 4) — tức chia train/test theo tỉ lệ đã được tạo trước)
  - `exp/df_clean.csv` → DataFrame đã làm sạch
  - `exp/class_encoder.joblib` → bộ mã hoá nhãn; hiển thị các lớp: ['Iris-setosa', 'Iris-versicolor', 'Iris-virginica']
- Khai báo các thư viện và mô hình thử nghiệm.
- Thiết lập cấu hình đánh giá:
  - Cross-validation: KFold với n_splits = 10, shuffle=True, seed=7
  - Metric: `accuracy`
- Spot-check (Baseline): thử nhiều mô hình không chuẩn hoá/special pipelines:
  - Logistic Regression (LOGR)
  - Linear Discriminant Analysis (LDA)
  - Gaussian Naive Bayes (GNB)
  - MLPClassifier (NEU)
  - KNeighborsClassifier (KNN)
  - DecisionTreeClassifier (CART)
  - SVC (SVM)
  - RandomForestClassifier (RF)
- Kết quả cross-validation (ví dụ in ra):
  - LOGR: 0.960000 (0.048990)
  - LDA: 0.960909 (0.047941)
  - GNB: 0.930909 (0.089738)
  - NEU: 0.960909 (0.047941)
  - KNN: 0.950909 (0.066457)
  - CART: 0.930909 (0.089738)
  - SVC: 0.950000 (0.067082)
  - RF: 0.930909 (0.063662)
- Hiển thị biểu đồ so sánh (boxplot) phân phối điểm CV của từng mô hình.
- Standardization: xây dựng Pipeline thêm bước StandardScaler cho từng mô hình tương ứng (tên pipelines bắt đầu bằng "Scaled...").
- Kết quả sau chuẩn hoá:
  - ScaledLOGR: ~0.941
  - ScaledLDA: ~0.961
  - ScaledGNB: ~0.931
  - ScaledKNN: ~0.941
  - ScaledCART: ~0.941
  - ScaledSVC: ~0.941
  - ScaledNEU: ~0.931
  - ScaledRF: ~0.941
- Hiển thị boxplot so sánh các pipeline đã chuẩn hoá.

Ghi chú về kết quả:
- Một số mô hình tuyến tính và MLP hoạt động rất tốt với accuracy ~96% trên cross-validation (trong tập huấn luyện).
- Chuẩn hoá ảnh hưởng tích cực đến 1 vài mô hình (ví dụ KNN, SVC, LogisticRegression), còn LDA giữ ổn định.
- RandomForest và DecisionTree đạt thấp hơn so với các mô hình tuyến tính trong thử nghiệm này.

Hành động tiếp theo (đề xuất trong notebook / nên thực hiện):
- Tinh chỉnh siêu tham số cho các mô hình tốt (GridSearchCV/RandomizedSearchCV).
- Huấn luyện lại trên toàn bộ tập train với siêu tham số tối ưu và đánh giá trên tập test (X_test, y_test).
- Lưu mô hình tốt nhất (joblib.dump) để triển khai.
- Thêm các metrics khác (confusion matrix, precision, recall, F1) để phân tích chi tiết hơn.

---

### 3) Iris_Model_02.ipynb — Template cho các thử nghiệm khác
Nội dung hiện tại:
- Tập hợp các import cho nhiều mô hình hồi quy và các thuật toán ensemble/regressor (LinearRegression, Lasso, ElasticNet, DecisionTreeRegressor, KNeighborsRegressor, SVR, RandomForestRegressor, GradientBoostingRegressor, ExtraTreesRegressor, AdaBoostRegressor, v.v.)
- Một số dòng import bị thừa/khuyết (notebook này hiện chưa hoàn thiện). Dường như là template để chạy các thử nghiệm hồi quy hoặc so sánh tương tự cho bài toán hồi quy (không phù hợp trực tiếp với bài toán phân loại Iris) — có thể là bản mẫu tái sử dụng.

Khuyến nghị:
- Hoàn thiện notebook này nếu muốn thử nghiệm biến đổi bài toán (chẳng hạn dự đoán một đặc trưng số thay vì phân lớp).
- Nếu không dùng cho hồi quy, có thể xoá hoặc chuyển đổi các import sang các mô hình phân loại bổ sung.

---

## Hướng dẫn chạy lại (Reproduce)

1. Mở `Iris_Oct15th.ipynb`:
   - Chạy toàn bộ cell để thực hiện EDA, xử lý sơ bộ dữ liệu, và (nếu có) lưu file `exp/df_clean.csv`, `exp/data.npz` và `exp/class_encoder.joblib` (lưu ý: trong repo hiện tại các file `exp/...` đã tồn tại theo đầu ra notebook).
2. Mở `Iris_Model_01.ipynb`:
   - Chạy cell đầu để load `exp/data.npz` và các artifacts.
   - Chạy các cell tiếp theo để thực hiện spot-check, chuẩn hoá và so sánh mô hình.
3. (Tùy chọn) Mở/hoàn thiện `Iris_Model_02.ipynb` nếu cần thử nghiệm thêm.

---

## Kết luận rút ra từ các thử nghiệm hiện tại

- Dữ liệu Iris là dữ liệu tiêu chuẩn, sạch, và cân bằng — phù hợp cho thử nghiệm thuật toán phân loại.
- Các mô hình tuyến tính (Logistic Regression, LDA) và MLP đạt kết quả rất tốt (≈96% accuracy trên cross-validation).
- Chuẩn hoá (StandardScaler) giúp cải thiện/ổn định hiệu năng cho các mô hình nhạy với quy mô đặc trưng (KNN, SVC, Logistic).
- Cần tiến hành tối ưu hoá siêu tham số và đánh giá chi tiết hơn (confusion matrix, precision/recall/F1, kiểm tra trên tập test) trước khi chọn mô hình cuối cùng để triển khai.
- Notebook `Iris_Model_02.ipynb` chưa hoàn chỉnh và có thể là template cho thử nghiệm thêm.

---

## Đề xuất cải tiến / bước tiếp theo

- Thực hiện GridSearchCV / RandomizedSearchCV cho các mô hình tốt (LogisticRegression, LDA, MLP, SVC, KNN) để tìm siêu tham số tối ưu.
- Huấn luyện mô hình tối ưu trên toàn bộ tập huấn luyện, đánh giá trên tập test (X_test/y_test) và thu báo cáo đầy đủ (accuracy, F1-score, confusion matrix).
- Lưu mô hình và các artifacts liên quan (encoder, scaler, model) vào `exp/` để phục vụ triển khai.
- Thử nghiệm ensemble hoặc stacking để xem có cải thiện so với mô hình tốt nhất đơn lẻ hay không.
- Xem xét loại bỏ bản ghi trùng lặp hoặc giữ lại tùy mục tiêu; nếu xóa trùng có thể huấn luyện lại và so sánh kết quả.

---

Nếu bạn muốn, tôi có thể:
- Viết thêm cell lưu mô hình tốt nhất tự động (joblib.dump).
- Hoàn thiện `Iris_Model_02.ipynb` để thử nghiệm thêm hoặc chuyển nó thành notebook so sánh thêm các mô hình phân loại.
- Tạo script Python reproducible (train.py) để chạy từ command line.
