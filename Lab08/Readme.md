# Mô tả dự án: Phân cụm K-Means (Lab08)

Tài liệu này mô tả chi tiết những gì đã thực hiện trong thư mục Lab08/K-Mean của repository. Tất cả nội dung, notebook và dữ liệu liên quan đều nằm trong thư mục con như: `Bai tap mau`, `Bai tap thuc hanh 1`, `Bai tap thuc hanh 2`, mỗi bài có notebook và file dữ liệu kèm theo.

---

Mục lục
- Giới thiệu chung
- Yêu cầu môi trường
- Cách chạy các notebook
- Mô tả chi tiết từng bài tập / file
  - Bai tap mau / iris-data
  - Bai tap mau / Mall-Customer
  - Bai tap thuc hanh 1 (penguins)
  - Bai tap thuc hanh 2 (Online Retail)
- Ghi chú, vấn đề đã gặp và đề xuất cải tiến

---

Giới thiệu chung
- Mục tiêu: Thực hành kỹ thuật phân cụm không giám sát (K-Means) trên nhiều bộ dữ liệu phổ biến (Iris, Mall Customers, Penguins, Online Retail). Các bước chính bao gồm khảo sát dữ liệu (EDA), tiền xử lý, chuẩn hóa (scaling), chọn số cụm tối ưu (Elbow, Silhouette), huấn luyện K-Means, gán nhãn cluster và phân tích kết quả (mô tả đặc trưng của từng cluster).
- Thư viện chính sử dụng: numpy, pandas, matplotlib, seaborn, plotly, scikit-learn (KMeans, MinMaxScaler, StandardScaler, LabelEncoder, silhouette_score).

---

Yêu cầu môi trường
- Python 3.x
- Thường dùng các package:
  - numpy, pandas
  - matplotlib, seaborn
  - plotly
  - scikit-learn
- Cài đặt ví dụ:
  - pip install numpy pandas matplotlib seaborn plotly scikit-learn

Cách chạy
- Mở Jupyter Notebook / JupyterLab.
- Chuyển working directory về đúng thư mục chứa notebook (hoặc sử dụng đường dẫn tương đối tới file dữ liệu như trong notebook).
- Chạy từng cell theo thứ tự. Một số notebook thực hiện hiển thị tương tác bằng plotly; để hiển thị tốt nên chạy trong môi trường hỗ trợ output đồ họa.

---

Mô tả chi tiết từng bài tập / file

1) Bai tap mau / iris-data
- Files:
  - `Iris.csv` — bộ dữ liệu Iris (các cột: Id, SepalLengthCm, SepalWidthCm, PetalLengthCm, PetalWidthCm, Species)
  - `main.ipynb` — notebook thực hiện phân cụm K-Means trên dữ liệu Iris
- Nội dung notebook:
  - Đọc dữ liệu: `pd.read_csv("Iris.csv")`
  - Loại bỏ cột `Id` (không dùng để phân cụm).
  - Tạo `X` (features) = 4 thuộc tính đầu (Sepal/Petal) và `y` = nhãn Species (chỉ để trực quan, không dùng để huấn luyện).
  - EDA cơ bản: hiển thị head, bảng tần suất nhãn.
  - (Dự kiến/đã sử dụng) chuẩn hóa bằng MinMax/Standard khi cần để cải thiện phân cụm.
  - Dùng KMeans để chạy phân cụm (range k có thể thử), có thể dùng Elbow và Silhouette để đánh giá.
  - Visualize kết quả (scatter / plotly) và so sánh clustering label với label gốc (Species) để đánh giá trực quan.
- Ghi chú:
  - Vì Iris có 3 lớp thực tế, thường kỳ vọng K = 3; notebook dùng KMeans và trực quan hóa để kiểm tra độ phù hợp.

2) Bai tap mau / Mall-Customer
- Files:
  - `Mall_Customers.csv` — dữ liệu khách hàng (CustomerID, Gender, Age, Annual Income (k$), Spending Score (1-100))
  - `main.ipynb` — notebook phân cụm K-Means cho Mall Customers
- Nội dung notebook:
  - Đọc dữ liệu và chuyển `Gender` thành giá trị số (Male = 1, Female = 0).
  - Chuẩn bị dữ liệu `X` = các cột cuối (ví dụ Age, Annual Income, Spending Score, Gender).
  - Thực hiện nhiều lần KMeans với k trong khoảng 3..9, lưu lại `inertia` (Elbow) và `silhouette_score`.
  - Vẽ biểu đồ Elbow (inertia vs k) và Silhouette scores để chọn k tối ưu.
  - Trong notebook đã chọn K = 6 (ví dụ) để gán nhãn cho từng sample:
    - Thêm cột `Label` vào dataset.
    - In mô tả thống kê (describe) cho từng cluster: count/mean/std/min/25%/50%/75%/max cho Age, Annual Income, Spending Score để hiểu đặc tính mỗi cluster.
- Ghi chú:
  - Notebook trình bày rõ quy trình lựa chọn số cụm và phân tích đặc tính từng cluster giúp rút ra insight (ví dụ: nhóm trẻ có thu nhập thấp nhưng điểm chi tiêu cao, v.v).

3) Bai tap thuc hanh 1 (penguins)
- Files:
  - `penguins.csv` — dữ liệu chim cánh cụt (các cột: culmen_length_mm, culmen_depth_mm, flipper_length_mm, body_mass_g, sex)
  - `main.ipynb` — notebook mô tả EDA, xử lý missing và phân cụm
- Nội dung notebook:
  - Đọc dữ liệu `penguins.csv`, hiển thị head/tail và thống kê sơ bộ.
  - Kiểm tra giá trị thiếu (NaN): phát hiện có 9 dòng chứa NaN, trong đó một vài dòng là toàn bộ NaN (dòng "rác") và các dòng chỉ thiếu cột `sex`.
  - Hiển thị các dòng có NaN và in ra số lượng NaN theo cột:
    - culmen_length_mm, culmen_depth_mm, flipper_length_mm, body_mass_g: thiếu vài dòng (2 dòng toàn NaN).
    - sex: thiếu nhiều hơn (9 giá trị).
  - Trực quan hóa phân bố giá trị 'sex' (pie chart) để quan sát tỷ lệ.
  - Hướng xử lý đã thực hiện / gợi ý:
    - Xóa những dòng toàn NaN.
    - Với cột `sex` bị thiếu: tùy mục tiêu (nếu dùng `sex` làm feature thì cần impute hoặc loại bỏ dòng; nếu không, chỉ sử dụng các feature số).
  - Tiền xử lý tiếp theo:
    - Mã hóa `sex` nếu sử dụng (LabelEncoder / map).
    - Chuẩn hóa các biến số bằng MinMaxScaler hoặc StandardScaler trước khi chạy KMeans.
  - Chạy KMeans, dùng Elbow/Silhouette để chọn k, sau đó trực quan hóa kết quả.
- Ghi chú đặc biệt:
  - File `penguins.csv` chứa một vài giá trị bất thường/không chuẩn (ví dụ "NA", các giá trị âm hiếm hoặc ký tự lạ '.'), cần làm sạch thủ công nếu xuất hiện. Notebook đã phát hiện và chỉ rõ các dòng và giá trị thô để xử lý.

4) Bai tap thuc hanh 2 (Online Retail)
- Files:
  - `OnlineRetail.csv` — dữ liệu giao dịch bán lẻ (InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country)
  - `main.ipynb` — notebook phân tích và chuẩn bị dữ liệu cho phân cụm khách hàng (RFM) và KMeans
- Nội dung notebook:
  - Đọc dữ liệu lớn (~541,909 dòng). Hiển thị head/tail, in `data.info()`.
  - EDA và kiểm tra missing:
    - Phát hiện `CustomerID` thiếu rất nhiều (135,080 giá trị NaN). Đây là vấn đề lớn vì phân cụm khách hàng (customer-level clustering) cần ID để nhóm giao dịch theo khách.
  - Kiểm tra các dòng null và hiển thị heatmap vị trí null để trực quan hóa.
  - Kiểm tra bản sao (duplicates) — phát hiện và thống kê các dòng trùng.
  - Những bước xử lý đã thực hiện / gợi ý trong notebook:
    - Loại bỏ các dòng không có `CustomerID` nếu mục tiêu là phân tích hành vi từng khách (RFM).
    - Loại bỏ giao dịch có `Quantity <= 0` hoặc `UnitPrice <= 0` (đơn hàng trả lại hoặc dữ liệu lỗi) trước khi tính `Monetary`.
    - Chuyển `InvoiceDate` từ chuỗi sang datetime (parse), cần thiết để tính `Recency`.
    - Tính các chỉ số RFM (Recency, Frequency, Monetary):
      - Recency: thời gian kể từ giao dịch cuối đến ngày tham chiếu.
      - Frequency: số giao dịch (hoặc số lần mua) cho mỗi CustomerID.
      - Monetary: tổng giá trị mua (Quantity * UnitPrice).
    - Chuẩn hóa RFM (MinMax/Standard) và dùng KMeans để phân cụm khách hàng.
    - Sử dụng Elbow và Silhouette để chọn số cụm.
  - Ghi chú:
    - Vì dataset lớn, cần cân nhắc hiệu năng (sampling, phân mảnh, hoặc sử dụng compute resource phù hợp).
    - Sau khi tính RFM, có thể dùng trực quan (boxplot, radar chart) để mô tả cluster.

---

Ghi chú, vấn đề đã gặp và đề xuất cải tiến
- Vấn đề data quality:
  - `penguins.csv` có các giá trị "NA", ".", -132 (giá trị bất thường), một vài dòng toàn NA -> cần làm sạch.
  - `OnlineRetail.csv` có nhiều dòng thiếu `CustomerID` (~25% dữ liệu) — cần quyết định giữ hay bỏ tùy bài toán.
  - `OnlineRetail.csv` có các hàng duplicate, cần deduplicate khi hợp lý.
- Về tiền xử lý:
  - Luôn parse `InvoiceDate` sang datetime trước khi tính Recency.
  - Lọc `Quantity <= 0` và `UnitPrice <= 0` để tránh tính Monetary sai.
  - Khi dùng biến categorical (ví dụ Gender, sex), cần mã hóa nhất quán; cân nhắc one-hot hoặc label encoding tùy trường hợp.
  - Chuẩn hóa feature (StandardScaler/MinMaxScaler) trước KMeans để tránh bias từ scale.
- Về lựa chọn số cụm:
  - Sử dụng kết hợp Elbow (inertia) và Silhouette Score; đối với bài toán thực tế, cũng nên đánh giá tính ý nghĩa của cluster bằng thống kê mô tả và trực quan.
- Về tái tạo kết quả:
  - Nên đặt `random_state` khi khởi tạo KMeans để kết quả có thể tái tạo.
- Đề xuất cải tiến thêm:
  - Lưu model và scaler (joblib/pickle) để dùng lại.
  - Viết script/đơn vị chức năng (module .py) để tái sử dụng pipeline tiền xử lý & phân cụm.
  - Tự động hóa lựa chọn k (ví dụ: gap statistic, silhouette max search).
  - Đối với Online Retail, cân nhắc phân tích theo từng quốc gia (Country) hoặc chỉ lấy khách UK nếu cần.

---

Kết luận ngắn
- Các notebook trong Lab08 trình bày quy trình thực hành chuẩn để xây dựng mô hình K-Means: EDA → Xử lý dữ liệu thiếu / bất thường → Chuẩn hóa → Lựa chọn k → Huấn luyện KMeans → Phân tích kết quả.
- Mỗi bài tập có những điểm nhấn riêng: Iris (bài mẫu cơ bản), Mall-Customer (phân khúc khách đơn giản), Penguins (xử lý missing và dữ liệu dạng thực nghiệm), Online Retail (bài toán thực tế yêu cầu RFM và xử lý dữ liệu lớn).

Nếu bạn muốn, tôi có thể:
- Tạo file README này trong repository (thêm vào root hoặc thư mục Lab08) — tôi sẽ chuẩn bị nội dung và mở pull request.
- Hoặc tạo file requirements.txt / environment.yml cho môi trường tương thích.
- Hoặc tinh chỉnh README để thêm hướng dẫn từng bước chạy cụ thể cho mỗi notebook.
