# CS114.O21-21521809-21522608
## THÔNG TIN NHÓM
### MSSV-21521809
Họ và Tên: Nguyễn Quốc An  
Số buổi vắng: 1  
Số bài tập quá trình: 9  
Điểm WeCode:  

### MSSV-21522608
Họ và Tên:  
Số buổi vắng:  
Số bài tập quá trình:  
Điểm WeCode:  

## THÔNG TIN ĐỒ ÁN - THỰC HÀNH
### 1. Đồ án cuối kỳ: MotocycleClassification
Tổng số lượng ảnh đóng góp:   
Phương pháp rút trích đặc trưng sử dụng:  
Thuật toán học được sử dụng:  
Framework, thư viện sử dụng:  
Kết quả Accuracy:  
Xếp hạng:  

## 2. Danh sách các bài thực hành đã làm
Thống kê dữ liệu (CS114.Tool.DatasetStat.ipynb):  
Tạo các splits (CS114.Tool.CreateSplit.ipynb):  
Hiển thị các ảnh (CS114.Tool.DatasetViz.ipynb):  
Ứng dụng Clustering (CS114.Clustering.ipynb):  
Đánh giá Model (CS114.Evaluation.ipynb):  

## 3. Bài tập - Dự đoán điểm IT001
Thực hiện trích xuất 51 features từ dữ liệu thô ban đầu, gom nhóm dữ liệu theo username tương ứng mỗi username là 1 dòng gồm 51 features (1489 usernames) và lưu kết quả vào file data.csv.  
Tiếp theo lọc các username, nếu username có trong file public(th-public, qt-public,...) thì lưu vào train ngược lại thì lưu vào test.  
Thực hiện split data với tỉ lệ 8:2, train trên 2 model dành cho linear regression là RandomForestRegressor và ExtraTreesRegressor.  
Cuối cùng là thực hiện đánh giá trên tập validation và test để có được kết quả tốt nhất.  

## 4. Bài tập - Nhận dạng chữ số viết tay
Dữ liệu được thu thập bằng cách tự viết tay các số từ 1 đến 9 mỗi số có 3 ảnh khác nhau và được lưu vào các folder số tương ứng.  
### Đặc trưng của dữ liệu
Định dạng dữ liệu ảnh: Các ảnh trong MNIST là các ảnh chữ số viết tay từ 0 đến 9, có kích thước 28x28 pixels. Các ảnh này ban đầu là đơn sắc và được định dạng lại để có một kênh màu (greyscale).  

Chuẩn hóa dữ liệu: Dữ liệu ảnh được chuẩn hóa bằng cách chuyển đổi giá trị pixel từ kiểu số nguyên sang số thực và chia cho 255 để đưa giá trị về phạm vi từ 0 đến 1. Việc này giúp cải thiện hiệu quả huấn luyện của mạng nơ-ron bằng cách làm giảm sự chênh lệch độ lớn giữa các đặc trưng đầu vào.  

One-hot encoding: Nhãn của mỗi ảnh được biến đổi thành dạng one-hot vector, tức là một vector mà tất cả các thành phần đều bằng 0 trừ thành phần thể hiện nhãn đúng của ảnh, được đặt là 1. Điều này phù hợp cho bài toán phân loại nhiều lớp.  
### Thuật toán và mô hình học
Mô hình học sâu: Sử dụng một mạng nơ-ron tích chập đơn giản (CNN) với cấu trúc bao gồm:

  Lớp tích chập (Conv2D): Sử dụng 32 bộ lọc với kích thước 3x3, hàm kích hoạt ReLU, và khởi tạo trọng số He uniform, phù hợp cho mạng ReLU để giảm vấn đề biến mất gradient.  
  Lớp gộp tối đa (MaxPooling2D): Giảm chiều dữ liệu đầu ra từ lớp tích chập, giúp mô hình bớt nhạy cảm với vị trí của đặc trưng trong ảnh.  
  Lớp làm phẳng (Flatten) và các lớp kết nối đầy đủ (Dense): Chuyển đổi đầu ra từ dạng ma trận sang vector và áp dụng học có giám sát để phân loại ảnh.  
  Biên dịch mô hình: Sử dụng thuật toán tối ưu hóa Stochastic Gradient Descent (SGD) với hệ số học là 0.01 và động lượng 0.9, cùng với hàm mất mát là categorical_crossentropy, phù hợp cho bài toán phân loại nhiều lớp.  

Đánh giá mô hình: Sử dụng kỹ thuật kiểm định chéo k-fold để đánh giá độ chính xác của mô hình, đảm bảo mô hình hoạt động tốt trên nhiều tập dữ liệu kiểm thử khác nhau và không bị quá khớp.  

### Xử lý ảnh đầu vào
Để sử dụng trong mô hình đã huấn luyện, ảnh đầu vào cần được xử lý qua các bước làm mờ Gaussian, ngưỡng thích ứng, tìm và cắt khu vực chứa chữ số, thêm đệm, và cuối cùng là thay đổi kích thước về 28x28 pixels.  
