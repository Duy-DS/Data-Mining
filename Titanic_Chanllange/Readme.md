# Dự án: Titanic — Chuỗi Notebook xử lý, phân tích và dự đoán 
Mục tiêu của thư mục Titanic_Chanllange:
- Thực hiện toàn bộ pipeline từ khám phá dữ liệu (EDA), tiền xử lý (preprocessing), feature engineering, so sánh và tối ưu hóa mô hình, đến huấn luyện cuối cùng và tạo file submission phù hợp cho Kaggle (cột PassengerId + Survived).
- Lưu các bộ dữ liệu đã xử lý (Data_clean_v2 / v3 / v4) và lưu các file dự đoán (thư mục Pred_Result).

Nội dung chính trong thư mục
- train.csv / test.csv  
  Dữ liệu gốc chuẩn của bài toán Titanic (train có cột Survived).
- Titanic_EDA.ipynb  
  Notebook EDA: thống kê mô tả, trực quan hóa đơn biến và đa biến, kiểm tra missing values, nhận xét sơ bộ.
- Titanic_PreProcessing_v1.ipynb, _v2.ipynb, _v3.ipynb, _v4.ipynb  
  Các pipeline tiền xử lý và feature engineering với mức độ phức tạp tăng dần:
  - v1: các thao tác khám phá, đề xuất chiến lược.
  - v2: pipeline predictive imputation (dự đoán Age bằng RandomForestRegressor), tạo các feature (Title, FamilySize, HasCabin, Deck), One-Hot Encoding và lưu kết quả vào `Data_clean_v2`.
  - v3: feature engineering nâng cao (binning Age/Fare, interaction features, FarePerPerson, nhiều feature mới) và lưu vào `Data_clean_v3`.
  - v4: phiên bản "less is more" đơn giản hóa, chỉ giữ các đặc trưng cốt lõi, lưu vào `Data_clean_v4`.
  Mỗi phiên bản có logic, trade-off và thử nghiệm khác nhau — bạn có thể chọn version phù hợp để tiếp tục huấn luyện.
- Titanic_Model_Train_Lab_1(Duy's).ipynb, _v2.ipynb, _v3.ipynb, _v3 (various)  
  Các notebook huấn luyện mô hình:
  - Thực hiện so sánh nhiều thuật toán cơ bản (LogisticRegression, SVM, DecisionTree, RandomForest, GradientBoosting, KNN, NaiveBayes, v.v.), báo cáo accuracy / precision / recall / f1.
  - Vòng lọc: RFECV để chọn đặc trưng tốt, GridSearchCV để tinh chỉnh siêu tham số cho từng mô hình.
  - Kịch bản nâng cao sử dụng LightGBM + Optuna để tối ưu siêu tham số và huấn luyện cuối cùng (các notebook v2/v3 trình bày chi tiết Optuna + LightGBM).
  - Một số notebook lưu kết quả huấn luyện, in kết quả và lưu file dự đoán vào thư mục `Pred_Result` (ví dụ pred_result_Lab_1_v6, v7…).
- pred_result_survived_Lab_1.ipynb  
  Notebook cuối cùng thực hiện:
  1) Tải dữ liệu đã xử lý (Data_clean_v2 và file model_data.npz kết hợp X_train/X_validation/y_train/y_validation).  
  2) Tự động chọn mô hình (trong notebook hiện có BEST_MODEL_NAME = "LogisticRegression", đồng thời RFECV và GridSearchCV cũng được chạy giả lập với GradientBoosting để tìm feature/params).  
  3) Huấn luyện mô hình cuối cùng trên toàn bộ dữ liệu train.  
  4) Dự đoán trên test và lưu file submission (ví dụ pred_result_Lab_1_v5.csv).  
  5) Vẽ trực quan phân bố dự đoán so với phân bố thực tế trên train.
- Thư mục Pred_Result (không nằm trong repository trực tiếp trong notebook): chứa các file CSV submission được sinh (pred_result_Lab_1*.csv, pred_result_Lab_1_v2..v7.csv, advanced_submission.csv, final_submission.csv, ...).

Tóm tắt các bước xử lý & học máy đã thực hiện
1. Khám phá dữ liệu (EDA)
   - Kiểm tra shape, kiểu dữ liệu, missing values.
   - Nhận diện cột nhiều missing (Age, Cabin, Embarked) và mối liên hệ giữa các biến và target (Survived).

2. Tiền xử lý & Feature Engineering (nhiều phiên bản)
   - Điền missing:
     - Chiến lược đơn giản: Age -> median, Embarked -> mode, bỏ Cabin.
     - Feature engineering + group impute: thêm Title, HasCabin, Deck, Age theo median nhóm (Pclass, Sex, Title).
     - Predictive imputation / IterativeImputer / RandomForestRegressor: dự đoán Age bằng mô hình; phương pháp này cho kết quả tốt nhất trong thử nghiệm.
   - Tạo feature mới: FamilySize, IsAlone, Title, Deck, FareBin, AgeBin, Age*Class, FarePerPerson, v.v.
   - One-Hot Encoding cho các biến categorical (Sex, Embarked, Title, Deck, FareBin, AgeBin...).
   - Lưu data đầu ra chuẩn (train_cleaned.csv, test_cleaned.csv) vào Data_clean_v2 / v3 / v4 cùng file model_data.npz để tái sử dụng.

3. So sánh mô hình cơ bản
   - Đã chạy LogisticRegression, SVM, DecisionTree, RandomForest, GradientBoosting, KNN, NaiveBayes...
   - Lấy metrics: Accuracy, Precision, Recall, F1 (weighted) trên validation set; in ra bảng so sánh; vẽ biểu đồ so sánh.

4. Tối ưu hóa đặc trưng & siêu tham số
   - RFECV để chọn tập đặc trưng tốt nhất cho từng mô hình.
   - GridSearchCV để tinh chỉnh siêu tham số cho các mô hình (Logistic, SVM, GBM,...).
   - Optuna + LightGBM ở các notebook nâng cao (Titanic_Model_Train_Lab_1(Duy's)_v2/v3) để tìm siêu tham số tốt nhất (kết quả tối ưu được in ra trong notebook, ví dụ F1-score ~0.84356, accuracy ~0.84733 trong những thử nghiệm).

5. Huấn luyện cuối cùng & tạo submission
   - Huấn luyện mô hình tốt nhất (với tham số tối ưu) trên toàn bộ dữ liệu train đã xử lý.
   - Dự đoán trên test set và lưu file submission (PassengerId + Survived).
   - Lưu các phiên bản file predict vào Pred_Result (v5, v6, v7...).

Kết quả/ghi chú đã in trong notebook
- pred_result_survived_Lab_1.ipynb cho biết mô hình “tốt nhất” được xác định là LogisticRegression (setup nội bộ). Sau quá trình chọn feature và tuning (ví dụ có sử dụng RFECV + GridSearch với GradientBoosting làm tham chiếu), notebook đã lưu `pred_result_Lab_1_v5.csv` và hiển thị 5 dòng đầu của file.
- Các notebook LightGBM + Optuna in ra best_params và best_value (ví dụ: F1 ~0.84356; accuracy ~0.84733 ở một cấu hình) và lưu các file submission tương ứng (pred_result_Lab_1_v6, v7...).

Hướng dẫn chạy lại (gợi ý thứ tự)
1. Chuẩn bị môi trường Python với các thư viện:
   - pandas, numpy, scikit-learn, matplotlib, seaborn, lightgbm, optuna, joblib
   - pip install -r requirements.txt (nếu bạn tạo file requirements)
2. Chạy Notebook tiền xử lý theo phiên bản mong muốn:
   - `Titanic_PreProcessing_v2.ipynb` → tạo Data_clean_v2
   - hoặc `Titanic_PreProcessing_v3.ipynb` → tạo Data_clean_v3 (FE nâng cao)
   - hoặc `Titanic_PreProcessing_v4.ipynb` → Data_clean_v4 (phiên bản tối giản)
3. Chạy notebook huấn luyện tương ứng:
   - notebook so sánh mô hình (Titanic_Model_Train_Lab_1(Duy's).ipynb) để tìm mô hình tốt và các tham số cơ bản.
   - notebook Optuna + LightGBM (v2 / v3) nếu muốn tối ưu siêu tham số chuyên sâu.
4. Chạy `pred_result_survived_Lab_1.ipynb` (hoặc notebook tạo submission tương ứng) để huấn luyện mô hình cuối cùng trên toàn bộ train và tạo file submission (lưu vào Pred_Result).


