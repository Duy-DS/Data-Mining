# Mô tả chi tiết nội dung Lab07 (Bayes, Decision Trees, SVM)

Tài liệu này ghi lại những gì đã làm trong các file và notebook nằm trong thư mục Lab07 của repository. Mục tiêu: minh họa quy trình phân tích dữ liệu và xây dựng mô hình phân loại với các thuật toán Naive Bayes, Decision Tree / Random Forest và Support Vector Machine. Tất cả mô tả viết bằng tiếng Việt.

Mục lục
- Tổng quan
- Yêu cầu môi trường
- Cấu trúc thư mục & mô tả file
- Chi tiết từng bài toán / notebook
  - Bayes (Naive Bayes)
  - Decision Trees (Cây quyết định & rừng ngẫu nhiên)
  - Support Vector Machine (SVM)
- Hướng dẫn chạy
- Ghi chú & kết luận ngắn

---

## Tổng quan
Trong Lab07, tác giả thực hiện các bước cơ bản của một pipeline Machine Learning cho nhiều bộ dữ liệu khác nhau:
1. Khám phá dữ liệu (EDA)
2. Tiền xử lý (cleaning, mã hóa, scaling, xử lý missing, feature engineering)
3. Tách train/test (thường stratify khi cần)
4. Huấn luyện mô hình (Naive Bayes, Decision Tree/RandomForest, SVM)
5. Đánh giá (accuracy, classification report, confusion matrix, ROC/AUC khi phù hợp)
6. Tối ưu / tuning (GridSearchCV / RandomizedSearchCV ở một vài notebook)

---

## Yêu cầu môi trường
Các notebook sử dụng phổ biến:
- Python 3.x
- pandas, numpy
- matplotlib, seaborn
- scikit-learn
- graphviz (dùng để vẽ cây)
- joblib (trong một vài pipeline)
Cài đặt ví dụ:
pip install -r requirements.txt
(trong trường hợp không có file requirements, cài thủ công các gói ở trên)

---

## Cấu trúc thư mục & mô tả file chính
(Lấy các file/note chính trong cuộc làm việc)

- Lab07/
  - bayes/
    - data/
      - Customer_Behaviour.csv
      - mushrooms.csv
    - CustomeBehaviour.ipynb
    - mushrooms.ipynb
  - Decision Trees/
    - Bài làm mẫu/
      - default_of_credit_card_clients.csv
      - main.ipynb
    - Bài tập thực hành 1/
      - Data_clean/
        - train_cleaned.csv
        - test_cleaned.csv
      - main.ipynb
      - Titanic_EDA.ipynb
      - Titanic_PreProcessing_v1.ipynb
    - Bài tập thực hành 2/
      - Data_clean/
        - data_cleaned.csv
      - EDA.ipynb
      - Pre_processing.ipynb
      - main.ipynb
  - Support Vector Machine/
    - bai_mau1/
      - bai_mau.ipynb
    - bai_mau2/
      - bai_mau.ipynb
    - bai_thuc_hanh_1/
      - bai_thuc_hanh_1.ipynb
    - bai_thuc_hanh_2/
      - bai_thuc_hanh_2.ipynb

Mỗi file / notebook có mô tả ngắn ở phần dưới.

---

## Chi tiết nội dung từng phần

### A. Bayes (thư mục `Lab07/bayes`)
1. Dữ liệu
   - Customer_Behaviour.csv
     - 400 dòng, 5 cột: User ID, Gender, Age, EstimatedSalary, Purchased (target)
     - Mục tiêu: dự đoán Purchased (0/1)
   - mushrooms.csv
     - Dữ liệu nấm chuẩn (UCI-like): ~8124 dòng, 23 cột (đều là categorical)
     - Target: class (edible `e` / poisonous `p`)

2. Notebooks
   - CustomeBehaviour.ipynb
     - Mô tả/hành động:
       - Load dữ liệu Customer_Behaviour.csv
       - EDA: kích thước, head, info, describe, phân bố target Purchased
       - Visualization: histogram Age, EstimatedSalary, phân bố Gender, scatter Age vs EstimatedSalary theo Purchased
       - Tiền xử lý:
         - Drop `User ID`
         - Map `Gender` (Male=1, Female=0)
         - Tách X/y
         - Train/test split (80/20) với stratify
         - StandardScaler cho features
       - Mô hình:
         - Gaussian Naive Bayes (GaussianNB)
         - Huấn luyện trên tập train
         - Đánh giá: accuracy trên train ≈ 0.8906 và test ≈ 0.8750; in classification report (precision/recall/f1)
       - Ghi chú: quy trình minh họa cơ bản cho Naive Bayes với dữ liệu có biến số liên tục.
   - mushrooms.ipynb
     - Mô tả/hành động:
       - Load mushrooms.csv, kiểm tra kích thước (8124 x 23)
       - EDA: kiểm tra missing, giá trị unique từng cột (nhiều categorical)
       - Visualization: phân bố class (edible/poisonous), phân bố một số feature quan trọng (odor, gill-color, spore-print-color, population,...)
       - Tiền xử lý:
         - Xử lý giá trị đặc biệt (ví dụ cột `stalk-root` chứa '?')
         - Mã hóa categorical (LabelEncoder / OneHot/Ordinal tùy nơi)
       - Mô hình:
         - Sử dụng MultinomialNB hoặc CategoricalNB (notebook có import cả hai); phù hợp cho dữ liệu dạng rời rạc/hạng mục.
       - Ghi chú: dataset này phù hợp cho Naive Bayes phân loại, do toàn bộ features là hạng mục.

### B. Decision Trees (thư mục `Lab07/Decision Trees`)
Mục tiêu: minh họa xây dựng cây quyết định, rừng ngẫu nhiên và các bước tiền xử lý cần thiết cho các bài toán thực hành (credit default, Titanic, diabetes).

1. Bài làm mẫu (Credit card default)
   - default_of_credit_card_clients.csv
     - Dữ liệu lớn, nhiều feature liên quan lịch sử thanh toán, bill amounts, pay amounts,...
   - main.ipynb (Bài làm mẫu)
     - Load file default_of_credit_card_clients.csv
     - Lựa chọn feature (loại bỏ ID, một số PAY_x, v.v.)
     - Chia train/test
     - Xây dựng DecisionTreeClassifier (cấu hình, vẽ cây bằng graphviz)
     - Mục tiêu là dự đoán `default payment next month`.

2. Bài tập thực hành 1 (Titanic)
   - Data_clean/train_cleaned.csv và test_cleaned.csv
     - Đã là các file tiền xử lý (features: Pclass, Age, Fare, FamilySize, IsAlone, HasCabin, one-hot cho Title, Deck, Embarked,...)
   - Titanic_EDA.ipynb
     - EDA chi tiết: thống kê, missing values (Age, Cabin nhiều missing), trực quan các biến ảnh hưởng đến Survived
   - Titanic_PreProcessing_v1.ipynb
     - Các chiến lược xử lý missing (baseline: median/mode; nâng cao: iterative imputer; feature engineering: hàm HasCabin, Deck,...)
     - Hàm hỗ trợ evaluate_strategy (dùng cross-val để đánh giá các chiến lược)
   - main.ipynb (Bài tập)
     - Dùng train_cleaned.csv, tách train/validation, huấn luyện DecisionTreeClassifier (ví dụ max_depth=2)
     - In kết quả accuracy mẫu: ví dụ "Độ chính xác (Accuracy) của cây mặc định: 0.7989"
     - Vẽ cây bằng graphviz, hiển thị confusion/accuracy.

3. Bài tập thực hành 2 (Diabetes)
   - Data_clean/data_cleaned.csv
     - Dữ liệu diabetes (diabetes_prediction_dataset): các biến như gender, age, hypertension, heart_disease, smoking_history, bmi, HbA1c_level, blood_glucose_level, diabetes(target)
     - Trong preprocessing: phát hiện duplicate (ví dụ đã loại một số bản ghi trùng), mã hóa categorical (LabelEncoder/OneHot), scaling, xử lý imbalance nếu cần.
   - EDA.ipynb, Pre_processing.ipynb
     - EDA toàn diện, xử lý duplicate, mã hóa, scaling. Ví dụ: sau tiền xử lý lưu npz/model_data.npz, phần main.ipynb thông báo: "Tải dữ liệu thành công. Kích thước X_train: (70000, 8), X_test: (30000, 8)"
   - main.ipynb
     - Dùng dữ liệu đã xử lý, xây dựng các mô hình phân loại (DecisionTree, RandomForest, các thuật toán khác có thể thử)
     - Đánh giá bằng accuracy, classification_report, confusion_matrix, cross-validation, grid search.

Ghi chú chung cho Decision Trees:
- Các notebook minh hoạ đầy đủ pipeline: EDA → tiền xử lý → chia dữ liệu → training → đánh giá → vẽ cây.
- Một vài notebook lưu file cleaned CSV phục vụ cho việc tái sử dụng.

### C. Support Vector Machine (thư mục `Lab07/Support Vector Machine`)
1. bai_mau1/bai_mau.ipynb
   - Dùng dataset Iris (sklearn.datasets.load_iris)
   - Tách train/test rồi xây dựng SVM cơ bản
   - Mục đích: minh hoạ SVM trên bộ dữ liệu nhỏ, hiển thị thông tin dataset.

2. bai_mau2/bai_mau.ipynb
   - Dữ liệu digits (sklearn.datasets.load_digits), nhận diện chữ viết tay (0-9)
   - Xây dựng SVM (SVC gamma=0.001, C=100), huấn luyện trên phần dữ liệu, kiểm tra performance
   - In classification_report: ví dụ accuracy ≈ 0.95 (từ báo cáo trong notebook)

3. bai_thuc_hanh_1/bai_thuc_hanh_1.ipynb
   - Dữ liệu lớn (diabetes dataset trong Lab07/Decision Trees) được sử dụng để thực hành:
   - Tiền xử lý: OneHotEncoder cho categorical (gender, smoking_history), StandardScaler cho numeric
   - X_train/X_test chia bằng stratify
   - Xây dựng pipeline preprocess → SVC
   - GridSearchCV phần tham số bị bỏ qua do dữ liệu lớn (ghi chú trong notebook)
   - Huấn luyện SVC cuối cùng và đánh giá.

4. bai_thuc_hanh_2/bai_thuc_hanh_2.ipynb
   - Bài toán phân loại (ví dụ dataset animal symptoms) — task multicategorical → nhãn Dangerous (Yes/No)
   - Dùng ColumnTransformer + OneHotEncoder cho tất cả các feature chuỗi
   - Pipeline + RandomizedSearchCV để tối ưu hyperparameters (C, gamma, kernel)
   - Kết quả: best CV Accuracy ví dụ ~0.987 và test accuracy bằng 1.0 (notebook có in kết quả)
   - Lưu ý: dataset này rất imbalance / nhỏ về số lượng một nhãn trong test → cần cân nhắc interpret kết quả (notebook có phần nhận xét quan trọng).

---

## Một số kết quả tiêu biểu (từ outputs trong notebook)
- Naive Bayes trên Customer_Behaviour:
  - Train accuracy ≈ 0.8906 (89.06%)
  - Test accuracy ≈ 0.8750 (87.50%)
  - Classification report in ra precision/recall/f1 cho cả 2 lớp
- Mushrooms:
  - Kích thước: (8124, 23)
  - Phân bố target: edible 4208, poisonous 3916 (~52%/48%)
- Decision Tree (Titanic example):
  - Một cây với max_depth=2 có accuracy trên validation ~0.7989 (ví dụ minh họa)
- SVM:
  - Digits classification (bai_mau2): classification report hiển thị accuracy ~0.95
  - Bai_thuc_hanh_2: RandomizedSearchCV đạt Best CV Accuracy ~0.987, test accuracy in notebook = 1.0 (lưu ý dataset test nhỏ/imbalance)

---

## Hướng dẫn chạy
1. Cài đặt các thư viện cần thiết:
   - pandas, numpy, scikit-learn, matplotlib, seaborn, graphviz, joblib, jupyter
   - ví dụ: pip install pandas numpy scikit-learn matplotlib seaborn graphviz joblib jupyter
2. Mở Jupyter Notebook: jupyter notebook
3. Duyệt tới folder Lab07 và chạy từng notebook theo trình tự:
   - Đối với từng notebook: chạy từng cell từ đầu (Run All)
   - Lưu ý:
     - Một số notebook đọc file CSV từ đường dẫn tương đối (ví dụ `../data/...`), hãy đảm bảo bạn mở notebook từ đúng thư mục gốc hoặc điều chỉnh đường dẫn.
     - graphviz: nếu muốn vẽ cây, cần cài phần mềm graphviz (OS package) + pip package `graphviz`. Trên Windows/Linux: cài binary graphviz trước.
4. Nếu dữ liệu đã tiền xử lý có sẵn (ví dụ `Data_clean/*.csv`) bạn có thể mở trực tiếp các notebook main để chạy phần modeling.

---

## Ghi chú / đề xuất cải tiến
- Kiểm tra imbalance nhãn (các dataset như Titanic hay diabetes có thể imbalance) → thử oversampling (SMOTE), class_weight, balanced metrics.
- Với datasets lớn (ví dụ diabetes gốc 100k), khi chạy GridSearch/RandomizedSearch có thể tốn nhiều thời gian; dùng RandomizedSearch hoặc giảm kích thước tập để thử nghiệm ban đầu.
- Lưu kết quả (model, scaler, encoder) bằng joblib để tái sử dụng.
- Thêm phần kiểm tra ROC/AUC cho các bộ nhị phân để có cái nhìn sâu hơn ngoài accuracy.
- Viết script / pipeline tái sử dụng (Python scripts) thay vì chỉ notebooks để dễ sản xuất hoá.

---

## Kết luận ngắn
Các notebook trong Lab07 minh họa quy trình end-to-end cho bài toán phân loại: từ EDA, tiền xử lý, mô hình hóa đến đánh giá. Tệp dữ liệu điển hình gồm Customer Behaviour (ví dụ GaussianNB), Mushrooms (Naive Bayes với dữ liệu categorical), Titanic/Credit Card (Decision Tree / Random Forest), Diabetes (Decision Trees/ensembles), và nhiều minh hoạ SVM trên Iris / Digits / các bộ dữ liệu thực hành. Những notebook này phù hợp để học hiểu các bước thiết yếu và có thể mở rộng/ tinh chỉnh cho các dự án thực tế.

Nếu bạn muốn, tôi có thể:
- Tạo file requirements.txt tự động từ các notebook,
- Viết script chạy tự động để train + evaluate,
- Hoặc viết README tiếng Anh tương đương.
