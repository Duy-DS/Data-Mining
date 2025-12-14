# Tổng hợp Hành Trình Khai Phá Dữ Liệu — Duy-DS

Chào mừng! Đây là bản tổng hợp chi tiết về những gì tôi (Duy-DS) đã làm, học và thực hành trong quá trình học Khai phá Dữ liệu (Data Mining / Data Science). Mục đích của file này là giúp người mới mở repo ngay lập tức nắm được cấu trúc, nội dung chính, kỹ năng đã học và cách tái hiện các thí nghiệm.

---

## Mục lục
- Giới thiệu chung
- Mục tiêu học tập
- Công nghệ & thư viện chính
- Cấu trúc repository & mô tả ngắn các thư mục/chủ đề
- Tóm tắt nội dung theo Lab / Bài tập
- Kết quả tiêu biểu & nhận xét
- Hướng dẫn tái tạo (run / môi trường)
- Đề xuất tiếp theo / Hướng phát triển
- Liên hệ

---

## Giới thiệu chung
Kho này là nhật ký thực hành của một hành trình học Khai phá Dữ liệu bằng Python, bao gồm nhiều lab và bài tập thực tế: từ Python cơ bản, trực quan hóa, phân tích mô tả (EDA), xử lý dữ liệu, tới các thuật toán phân loại, phân cụm và tối ưu hóa mô hình (LightGBM + Optuna). Hầu hết bài làm được triển khai bằng Jupyter Notebook, kèm theo dữ liệu mẫu và một số file báo cáo.

Mục tiêu: luyện tay với pipeline end-to-end — EDA → tiền xử lý → đặc trưng → huấn luyện mô hình → đánh giá → tối ưu → lưu artifact (model, encoder, scaler).

---

## Mục tiêu học tập
- Nắm vững Python cơ bản (cú pháp, cấu trúc dữ liệu, I/O).
- Sử dụng NumPy, pandas để xử lý bảng dữ liệu.
- Trực quan hóa với matplotlib, seaborn, plotly.
- Thực hiện EDA, phát hiện giá trị thiếu, outlier và duplicate.
- Tiền xử lý (imputation, encoding, scaling).
- Kỹ thuật Feature Engineering (interaction features, binning, RFM...).
- Áp dụng thuật toán ML: KNN, Naive Bayes, Logistic Regression, LDA, SVM, Decision Tree, Random Forest, Gradient Boosting (LightGBM), MLP, K-Means.
- Đánh giá mô hình (accuracy, precision, recall, F1, confusion matrix, ROC/AUC, cross-validation).
- Tinh chỉnh siêu tham số (GridSearchCV, RandomizedSearchCV, Optuna).
- Lưu và tái sử dụng artifact (joblib, npz, csv).

---

## Công nghệ & thư viện chính
- Ngôn ngữ: Python 3.x
- Notebook: Jupyter
- Xử lý & số học: pandas, numpy
- Trực quan: matplotlib, seaborn, plotly
- Học máy: scikit-learn, lightgbm, gplearn (symbolic transformer)
- Hỗ trợ: scipy, joblib, optuna (tối ưu), graphviz (vẽ cây)
- Tài liệu & báo cáo: Markdown, PDF, DOCX

---

## Cấu trúc repository (tóm tắt)
(Dưới đây là danh sách các thư mục chính và nội dung nổi bật — xem từng thư mục để có notebook và dữ liệu chi tiết)

- Ex_scientific/  
  Bài tập Python cơ bản & trực quan hóa (máy tính cơ bản, vẽ sin/cos, vẽ bubble chart, tính chu vi/diện tích hình tròn).

- Lab01b/  
  Python cơ bản → nâng cao, giới thiệu Numpy, File handling, OOP, các bài tập thực hành.

- Lab02/  
  Phân tích bộ dữ liệu Pima Indians Diabetes — EDA, correlation, heatmap, tiền xử lý cơ bản.

- Lab03/  
  Thống kê mô tả & EDA trên nhiều bộ dữ liệu (COVID-19, marketing campaign, wine quality, diabetes).

- Lab04/  
  Classification & Feature Engineering: Iris, MNIST (digits), xử lý Titanic, Decision Tree cho wine dataset; áp dụng PCA, ICA, StandardScaler, genetic programming.

- Lab05/  
  Dự án Iris — so sánh nhiều mô hình, chuẩn hóa, cross-validation, lưu artifact (exp/).

- Lab06/  
  K-Nearest Neighbors & Naive Bayes — notebooks, báo cáo PDF/DOCX, mã thực nghiệm cho KNN/Naive Bayes.

- Lab07/  
  Bayes, Decision Trees, SVM — gồm nhiều bài thực hành: customer behaviour, mushrooms, Titanic, credit default, digits, nhiều notebook chuyên sâu.

- Lab08/  
  K-Means clustering — Iris, Mall-Customer, Penguins, Online Retail (RFM). Thực hành Elbow, Silhouette, tiền xử lý dữ liệu thực tế.

- Titanic_Chanllange/  
  Thư viện notebook xử lý và dự đoán bài toán Titanic — nhiều phiên bản tiền xử lý (v2/v3/v4), RFECV, GridSearch, LightGBM + Optuna, scripts lưu kết quả submission.

---

## Tóm tắt nội dung theo Lab / Bài tập (chi tiết hơn)

- Ex_scientific
  - Bài tập thực hành Python cơ bản: viết script, chạy qua Jupyter, in kết quả; trực quan hóa sin/cos và scatter bubble chart với numpy/matplotlib.

- Lab01b
  - Tổng hợp kiến thức Python: kiểu dữ liệu, list comprehension, dict/set, exception, OOP, thao tác file, numpy arrays, reshape, slicing, fancy indexing.

- Lab02 (Pima Indians)
  - EDA: dữ liệu sạch, phân bố lớp (imbalanced nhẹ), Glucose/BMI/Age quan trọng; trực quan heatmap tương quan.

- Lab03
  - Thực hành descriptive statistics & missing data visualization (heatmap); xử lý nhiều dataset như COVID (nhiều missing), winequality (nhiều duplicate), marketing campaign.

- Lab04
  - Classification experiments: so sánh nhiều mô hình, pipeline có/không StandardScaler, áp dụng PCA, ICA, SymbolicTransformer (gplearn) cho feature engineering; vẽ scatter 2D/3D, lưu artifacts.

- Lab05
  - Hệ thống notebook cho Iris: data cleaning, detection duplicate, spot-check models, pipelines tiêu chuẩn hóa, cross-val và boxplot so sánh.

- Lab06
  - KNN & Naive Bayes: code thử nghiệm KNN (k tuning), đánh giá metric đầy đủ; Naive Bayes cho dữ liệu continuous (Gaussian) và categorical (Multinomial/Categorical).

- Lab07
  - Bayes/Mushrooms: xử lý categorical, imputation cho `stalk-root`.
  - Decision Trees: credit default, Titanic (pipeline preprocessing, Deck/Title/IsAlone), diabetes.
  - SVM: experiments trên digits, Iris, pipeline với OneHot + StandardScaler, RandomizedSearch.

- Lab08
  - K-Means clustering: chuẩn hóa features, Elbow & Silhouette để chọn K, RFM cho Online Retail, xử lý dữ liệu lớn, đề xuất sampling và filtering (loại transactions không hợp lệ, CustomerID missing).

- Titanic_Chanllange
  - Một trong các project lớn nhất trong repo: nhiều phiên bản preprocess, feature engineering nâng cao (Age imputation bằng predictive models), RFECV, GridSearch/Optuna + LightGBM, tạo submission file, so sánh model.

---

## Kết quả tiêu biểu & một số con số (tham khảo từ notebook)
- Pima Indians: phân bố class — 500 (class 0) vs 268 (class 1).
- Iris: Accuracy cross-val nhiều mô hình đạt ~93–96%; Logistic/LDA/MLP thường tốt nhất.
- Naive Bayes (Customer Behaviour): train ~89%, test ~87.5% (ví dụ minh họa).
- Mushrooms: dataset ~8124 x 23, phân bố edible/poisonous gần cân bằng.
- SVM (digits): accuracy ~0.95 (tùy cấu hình).
- Titanic (LightGBM + Optuna): best F1 ~0.84 (ví dụ từ notebook), kết quả thay đổi theo feature set & seed.

Lưu ý: các con số trên là kết quả từng thí nghiệm trong notebook, có thể khác khi chạy lại do việc chia data/seed/tiền xử lý.

---

## Những kỹ năng cụ thể đã đạt được
- Xử lý dữ liệu thực tế: phát hiện và xử lý missing values, duplicate, outlier.
- Feature engineering: tạo interactions, binning, RFM cho phân tích hành vi khách hàng.
- Pipelines reproducible: tách preprocessing / model, lưu scaler/encoder/model.
- Đánh giá mô hình có hệ thống: cross-validation, confusion matrix, classification report.
- Hyperparameter tuning: GridSearchCV, RandomizedSearchCV, Optuna.
- Trực quan hóa kết quả phân tích & mô hình: heatmap, boxplot, scatter, 3D plot, Elbow & Silhouette cho clustering.
- Lập báo cáo thực nghiệm (PDF/DOCX) và viết README mô tả lại workflow.

---

## Hướng dẫn tái tạo (Quickstart)
1. Clone repo:
   - git clone https://github.com/Duy-DS/Data-Mining.git

2. Tạo môi trường và cài dependencies (ví dụ pip):
   - python -m venv venv
   - source venv/bin/activate  (Linux/macOS) hoặc venv\Scripts\activate (Windows)
   - pip install -r requirements.txt  (nếu có)
   - Nếu không có requirements.txt, cài gói cơ bản:
     - pip install numpy pandas matplotlib seaborn scikit-learn jupyter joblib lightgbm optuna plotly gplearn

3. Mở Jupyter:
   - jupyter notebook
   - Chọn folder/lab mong muốn và chạy từng cell từ trên xuống. Đảm bảo đặt working directory đúng (một số notebook dùng đường dẫn tương đối).

4. Lưu ý khi chạy:
   - Một số notebook cần cài graphviz (cài hệ thống + pip install graphviz) để vẽ cây quyết định.
   - Datasets lớn (OnlineRetail) có thể cần nhiều bộ nhớ; xem xét sampling.
   - Đặt random_state khi muốn kết quả tái lập.

---

## Tài liệu & artifact lưu trữ
- Một số notebook lưu artifacts vào thư mục `exp/` (ví dụ data.npz, df_clean.csv, class_encoder.joblib).
- Các báo cáo tóm tắt được lưu ở dạng PDF/DOCX trong Lab06 / Lab07.
- Nếu bạn muốn tôi có thể tạo file `requirements.txt` tự động từ notebook/imports hoặc một script `train.py` reproducible.

---

## Đề xuất tiếp theo / Hướng phát triển
- Tạo file requirements.txt / environment.yml để dễ tái tạo môi trường.
- Viết script dòng lệnh (train.py / evaluate.py) để chuyển từ notebook sang pipeline reproducible.
- Thêm unit tests cho các hàm tiền xử lý chính.
- Triển khai mô hình tốt nhất (ví dụ Iris/Titanic) dạng service nhỏ (Flask/FastAPI) để demo.
- Chuẩn hóa lưu artifact (model + metadata + version) và ghi README nhỏ cho từng notebook quan trọng.
- Bổ sung phần chú giải ngắn cho mỗi notebook (purpose, inputs, outputs, expected runtime).

---

## Ghi chú cuối
Kho này là nhật ký học tập — có nhiều notebook là bản thí nghiệm, bản demo hoặc template. Mục tiêu chính là học tập và minh họa quy trình Data Science. Nếu bạn dùng repo để tham khảo, chú ý đọc phần header của từng notebook để biết assumptions, đường dẫn dữ liệu và các bước cần chạy.

---

## Liên hệ
- Github: https://github.com/Duy-DS  
Nếu bạn muốn tôi giúp:
- Tạo requirements.txt,
- Viết script reproducible (train/evaluate),
- Hoặc gom lại các artifact quan trọng và tạo một README ngắn cho từng lab — cứ mở issue hoặc gửi message.

Cảm ơn bạn đã ghé qua hành trình học của tôi — chúc bạn có nhiều khám phá thú vị với dữ liệu!
