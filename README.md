# CS114.O21.KHCL-21521809-21522608
## THÔNG TIN NHÓM
### MSSV-21521809
+ Họ và Tên: Nguyễn Quốc An  
+ Số buổi vắng: 1  
+ Số bài tập quá trình: 9  
+ Điểm WeCode: 2675 

### MSSV-21522608
+ Họ và Tên: Lê Phương Thảo
+ Số buổi vắng: 1
+ Số bài tập quá trình: 9
+ Điểm WeCode:  1735

## THÔNG TIN ĐỒ ÁN - THỰC HÀNH
## 1. Đồ án cuối kỳ: MotocycleClassification
+ Tổng số lượng ảnh đóng góp: 229 = 54(Honda/) + 60(Yamaha) + 45(Suzuki) + 45(Vinfast) + 25(Other)
+ Phương pháp rút trích đặc trưng sử dụng:  Sử dụng ResNet50
+ Thuật toán học được sử dụng:  FCNN
+ Framework, thư viện sử dụng:  
+ Kết quả Accuracy:  
+ Xếp hạng:  

## 2. Danh sách các bài thực hành đã làm:
+ Thống kê dữ liệu (CS114.Tool.DatasetStat.ipynb):  6 June
+ Tạo các splits (CS114.Tool.CreateSplit.ipynb):  8 June
+ Hiển thị các ảnh (CS114.Tool.DatasetViz.ipynb):  8 June
+ Ứng dụng Clustering (CS114.Clustering.ipynb):  10 June
+ Huấn luyện Model (CS114.Train.ipynb): 13 June
+ Đánh giá Model (CS114.Evaluation.ipynb):  13 June

## 3. Bài tập - Dự đoán điểm IT001
### Quá trình xử lý dữ liệu
Đặc trưng rút trích:
+ Số lượng bài tập duy nhất mỗi người dùng đã làm (num_unique_assignments): Sử dụng nunique() để đếm số lượng bài tập duy nhất mà mỗi người dùng đã thực hiện.
+ Số bài toán duy nhất trong mỗi bài tập (num_unique_problems): Nhóm dữ liệu theo username và assignment_id và tính số lượng duy nhất của problem_id.
+ Tổng và trung bình số bài toán cho mỗi username: Tính tổng và trung bình số bài toán mà mỗi người dùng đã làm.
+ Số lần nộp bài cuối cùng cho mỗi người dùng (sum_is_final): Sử dụng sum() để đếm số lần nộp bài được đánh dấu là cuối cùng.
+ Số lượng và trung bình lần nộp bài không phải cuối cùng theo bài tập và bài toán (num_final_0_problem, average_final_0_problem): Tính số lần và trung bình số lần nộp bài không phải là cuối cùng.
+ Số lượng và trung bình của SCORE và Compilation Error theo người dùng, bài tập và bài toán: Đếm số lượng và tính trung bình cho các trạng thái này.
+ Phân tích pre_score: Tính số lần và trung bình điểm trước là 0 và không phải 0, cũng như tổng và trung bình tổng điểm trước không phải 0.
+ Số ngôn ngữ lập trình khác nhau mỗi người dùng đã sử dụng.
+ Số ngày và giờ khác nhau mà người dùng làm bài: Tách cột created_at và phân tích theo ngày và giờ.
+ Số lần coefficient khác 100.
+ Phân tích các thống kê liên quan đến times, mems, verdicts: Tính tổng, trung bình và số lượng khi các giá trị này bằng 0 hoặc khác 0.
  
Phương pháp:
+ Nhóm dữ liệu: Sử dụng groupby() để nhóm dữ liệu theo các biến khác nhau như username, assignment_id, problem_id.
+ Tính toán thống kê: Sử dụng các hàm như sum(), mean(), count(), và nunique() để tính toán các thống kê cần thiết.
+ Lọc dữ liệu: Sử dụng điều kiện lọc để tính toán thống kê cho các bộ phận dữ liệu cụ thể.

Quản lý và Lưu trữ Kết quả:
+ DataFrame Kết quả: Tất cả các kết quả đặc trưng được lưu trữ trong một DataFrame result.
+ Xuất dữ liệu: Sử dụng to_csv() để lưu kết quả vào một file CSV có tên là data.csv.

### Quá trình huấn luyện và đánh giá
Xử lý Dữ Liệu:
+ Dữ liệu được tải từ tệp CSV 'train.csv'. Sau đó, các giá trị thiếu trong tập dữ liệu được thay thế bằng 0.
+ Mục tiêu dự đoán (cột 'Target') được tách ra thành biến target.
+ Cột 'username' và cột 'Target' bị loại bỏ khỏi các đặc trưng để huấn luyện.
  
Phân Chia Dữ Liệu:
+ Dữ liệu được chia thành tập huấn luyện và tập kiểm thử với tỉ lệ 80% dữ liệu cho huấn luyện và 20% cho kiểm thử.
  
Khảo Sát Dữ Liệu:
+ Biểu đồ histogram được vẽ để thể hiện phân phối của biến mục tiêu trong tập kiểm thử.

Huấn Luyện Mô Hình:
+ Mô hình RandomForestRegressor và ExtraTreesRegressor được huấn luyện trên tập dữ liệu huấn luyện.
+ Dự đoán trên tập kiểm thử và tính điểm số r2_score để đánh giá hiệu quả của mô hình.

Xử Lý Dữ Liệu Kiểm Thử:
+ Dữ liệu kiểm thử từ tệp 'test.csv' được tải và xử lý tương tự như tập huấn luyện (thay thế giá trị thiếu và loại bỏ cột 'username').

Dự Đoán và Xuất Kết Quả:
+ Cả hai mô hình được sử dụng để dự đoán trên tập dữ liệu kiểm thử. 
+ Các dự đoán được ghi vào tệp CSV để tạo file nộp bài.

## 4. Bài tập - Nhận dạng chữ số viết tay
Dữ liệu được thu thập bằng cách tự viết tay các số từ 1 đến 9 mỗi số có 3 ảnh khác nhau và được lưu vào các folder số tương ứng.  
### Đặc trưng của dữ liệu
Định dạng dữ liệu ảnh: Các ảnh chữ số viết tay từ 0 đến 9, có kích thước 28x28 pixels. Các ảnh này ban đầu là đơn sắc và được định dạng lại để có một kênh màu (greyscale).  

Chuẩn hóa dữ liệu: Dữ liệu ảnh được chuẩn hóa bằng cách chuyển đổi giá trị pixel từ kiểu số nguyên sang số thực và chia cho 255 để đưa giá trị về phạm vi từ 0 đến 1. Việc này giúp cải thiện hiệu quả huấn luyện của mạng nơ-ron bằng cách làm giảm sự chênh lệch độ lớn giữa các đặc trưng đầu vào.  

One-hot encoding: Nhãn của mỗi ảnh được biến đổi thành dạng one-hot vector, tức là một vector mà tất cả các thành phần đều bằng 0 trừ thành phần thể hiện nhãn đúng của ảnh, được đặt là 1. Điều này phù hợp cho bài toán phân loại nhiều lớp.  

### Thuật toán và mô hình học
Mô hình học sâu: Sử dụng một mạng nơ-ron tích chập đơn giản (CNN) với cấu trúc bao gồm:

 + Lớp tích chập (Conv2D): Sử dụng 32 bộ lọc với kích thước 3x3, hàm kích hoạt ReLU, và khởi tạo trọng số He uniform, phù hợp cho mạng ReLU để giảm vấn đề biến mất gradient.  
 + Lớp gộp tối đa (MaxPooling2D): Giảm chiều dữ liệu đầu ra từ lớp tích chập, giúp mô hình bớt nhạy cảm với vị trí của đặc trưng trong ảnh.  
 + Lớp làm phẳng (Flatten) và các lớp kết nối đầy đủ (Dense): Chuyển đổi đầu ra từ dạng ma trận sang vector và áp dụng học có giám sát để phân loại ảnh.
   
Biên dịch mô hình: Sử dụng thuật toán tối ưu hóa Stochastic Gradient Descent (SGD) với hệ số học là 0.01 và động lượng 0.9, cùng với hàm mất mát là categorical_crossentropy, phù hợp cho bài toán phân loại nhiều lớp.  

Đánh giá mô hình: Sử dụng kỹ thuật kiểm định chéo k-fold để đánh giá độ chính xác của mô hình, đảm bảo mô hình hoạt động tốt trên nhiều tập dữ liệu kiểm thử khác nhau và không bị quá khớp.  

### Xử lý ảnh đầu vào
Để sử dụng trong mô hình đã huấn luyện, ảnh đầu vào cần được xử lý qua các bước làm mờ Gaussian, ngưỡng thích ứng, tìm và cắt khu vực chứa chữ số, thêm đệm, và cuối cùng là thay đổi kích thước về 28x28 pixels.  
