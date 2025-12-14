# Lab06 — K-Nearest Neighbors và Naive Bayes
Tác giả: Duy-DS  
Ngày: 2025-12-14

## Mô tả tổng quan
Thư mục Lab06 chứa mã nguồn, dữ liệu, tài liệu tham khảo và báo cáo liên quan đến hai thuật toán phân loại cơ bản: K-Nearest Neighbors (KNN) và Naive Bayes. Mục tiêu của lab là:
- Hiểu và hiện thực hoá KNN và Naive Bayes (từ đầu và/hoặc dùng thư viện).
- Làm tiền xử lý dữ liệu, lựa chọn đặc trưng, đánh giá và so sánh hiệu năng.
- Trình bày kết quả thí nghiệm và phân tích trong báo cáo.

## Cấu trúc thư mục và nội dung
- Lab06_BaoCao.docx  
  - Báo cáo tổng hợp của Lab06 (định dạng .docx). Chứa mô tả bài toán, phương pháp, kết quả và nhận xét/chốt luận.

- Lab_K_Nearest_Neighbors.pdf  
  - Báo cáo chi tiết dành cho phần KNN (định dạng PDF). Bao gồm mô tả thuật toán, các bước thực nghiệm, kết quả và biểu đồ liên quan.

- Lab_Naive_Bayes.pdf  
  - Báo cáo chi tiết dành cho phần Naive Bayes (định dạng PDF). Bao gồm mô tả các biến thể (Gaussian/Multinomial/Bernoulli nếu có), tiền xử lý và kết quả.

- KNN/  
  - data/  
    - Thư mục chứa tập dữ liệu dùng cho phần KNN (định dạng thường gặp: .csv, .xlsx, ...). Bao gồm dữ liệu gốc và có thể các file tiền xử lý sẵn.
  - workplace/  
    - Thư mục chứa mã nguồn thực nghiệm cho KNN: có thể là notebook (.ipynb), script (.py) hoặc các file hỗ trợ. Nội dung chính thường bao gồm:
      - Đọc dữ liệu và phân tích thăm dò (EDA).
      - Tiền xử lý: xử lý giá trị thiếu, chuẩn hoá/scale (Min-Max, Standard), mã hoá biến phân loại.
      - Cài đặt KNN (cả triển khai từ đầu và sử dụng sklearn.neighbors.KNeighborsClassifier).
      - Tìm tham số k tốt nhất (grid search hoặc cross-validation).
      - Đánh giá bằng accuracy, precision, recall, F1-score, confusion matrix; vẽ biểu đồ (accuracy theo k, ma trận nhầm lẫn...).
      - Lưu/ghi lại kết quả thí nghiệm.

- K_Nearest_Thamkhao/  
  - Thư mục tham khảo chứa tài liệu, code mẫu hoặc ghi chú bổ trợ liên quan tới KNN (ví dụ: bài báo, trang tham khảo, mã nguồn minh hoạ).

- LAB_NAIVE_BAYES/  
  - Thư mục chứa mã nguồn/note cho phần Naive Bayes. Nội dung chính thường bao gồm:
    - Thực hiện Naive Bayes (có thể cả triển khai tay và dùng sklearn.naive_bayes: GaussianNB, MultinomialNB, BernoulliNB).
    - Tiền xử lý dữ liệu phù hợp (chẳng hạn TF-IDF hoặc đếm từ cho MultinomialNB nếu dữ liệu dạng văn bản).
    - Áp dụng Laplace smoothing, kiểm thử các giả sử về phân phối (Gaussian vs Multinomial).
    - Đánh giá tương tự như phần KNN (accuracy, precision, recall, F1, confusion matrix).
    - So sánh kết quả giữa các biến thể và thảo luận ưu/khuyết điểm.

- Naive_Thamkhao/  
  - Thư mục tham khảo cho Naive Bayes (tài liệu, slides, code mẫu).

## Môi trường & phụ thuộc
Để chạy các file mã trong Lab06, nên có:
- Python 3.8+ (hoặc phiên bản tương thích)
- Thư viện thường dùng:
  - numpy, pandas
  - scikit-learn
  - matplotlib, seaborn
  - jupyter (nếu chạy notebook)
  - scipy (nếu cần)
Cách cài (ví dụ):
- Tạo virtual environment:
  - python -m venv venv
  - source venv/bin/activate (Linux/macOS) hoặc venv\Scripts\activate (Windows)
- Cài dependencies:
  - pip install numpy pandas scikit-learn matplotlib seaborn jupyter

(Gợi ý: nếu có file requirements.txt trong repo, chạy `pip install -r requirements.txt`.)

## Hướng dẫn chạy (ví dụ)
- Nếu có notebook (.ipynb):
  - Mở terminal tại thư mục Lab06 và chạy `jupyter notebook`, sau đó mở notebook trong `KNN/workplace` hoặc `LAB_NAIVE_BAYES`.
- Nếu có script Python:
  - Chạy: `python path/to/script.py`  
  - Các script thường có các tham số: đường dẫn dữ liệu, seed ngẫu nhiên, tham số k, v.v.
- Kiểm tra các file trong `KNN/data/` để biết tên file dữ liệu và đường dẫn cần dùng trong script/notebook.

## Các bước thực nghiệm (tóm tắt quy trình)
1. Khám phá dữ liệu (EDA): phân bố biến, tỷ lệ nhãn, phát hiện missing/outlier.
2. Tiền xử lý:
   - Xử lý giá trị thiếu (loại bỏ/điền giá trị).
   - Chuẩn hoá/scale (rất quan trọng với KNN).
   - Mã hoá biến phân loại (one-hot, label encoding).
   - Tách tập huấn luyện và kiểm thử (train/test split) hoặc sử dụng cross-validation.
3. Huấn luyện mô hình:
   - KNN: thử nhiều k, khoảng cách (Euclidean, Manhattan), cân nhắc trọng số lân cận.
   - Naive Bayes: chọn biến thể phù hợp (Gaussian cho dữ liệu liên tục, Multinomial cho dữ liệu đếm).
4. Tinh chỉnh tham số (grid search / cross-validation).
5. Đánh giá: accuracy, precision, recall, F1-score, ma trận nhầm lẫn; vẽ biểu đồ phục vụ phân tích.
6. Ghi nhận và phân tích kết quả trong báo cáo.

## Những điều đã làm (tóm tắt theo nội dung file)
- Thực hiện các bài tập/lab về KNN và Naive Bayes: cài đặt, thí nghiệm và so sánh.
- Lưu trữ dữ liệu mẫu dùng cho thí nghiệm trong `KNN/data`.
- Ghi lại các bước, kết quả và biểu đồ trong các notebook hoặc script trong `KNN/workplace` và `LAB_NAIVE_BAYES`.
- Soạn báo cáo chi tiết từng phần (PDF) và báo cáo tổng hợp (DOCX).

## Gợi ý đọc / tham khảo
- Nội dung tham khảo được đặt trong `K_Nearest_Thamkhao` và `Naive_Thamkhao` — bao gồm mã ví dụ, notes và tài liệu tham khảo học thuật hoặc trực tuyến.

## Ghi chú quan trọng
- Kết quả thí nghiệm có thể khác nhau nếu:
  - Có/không thực hiện chuẩn hoá dữ liệu (đặc biệt ảnh hưởng KNN).
  - Giá trị seed khác nhau dẫn tới phân chia train/test khác nhau.
  - Lựa chọn tham số k và loại khoảng cách.
- Để tái tạo chính xác kết quả trong báo cáo, kiểm tra phần cài đặt seed ngẫu nhiên (ví dụ: random_state trong scikit-learn) và thông tin tiền xử lý được nêu trong báo cáo PDF/DOCX.

## Liên hệ
Nếu cần tôi có thể:
- Hỗ trợ soạn README chi tiết hơn dựa trên nội dung cụ thể của các notebook/script (bạn có thể copy/paste nội dung chính hoặc cho phép tôi đọc các file cụ thể).
- Tạo file requirements.txt, hướng dẫn cụ thể để chạy từng notebook/script, hoặc tóm tắt kết quả chính từ báo cáo.

Chúc bạn thuận lợi với Lab06!
