# Tổng quan về giải pháp HAProxy:
## Thuật ngữ sử dụng trong HAProxy 
<p><b>Proxy (máy chủ ủy quyền)</b> là máy chủ trung gian đứng giữa thiết bị của người dùng và Internet, hoạt động như một cầu nối để chuyển tiếp thông tin</p>
<p>Đặc điểm của proxy: Yêu cầu của người dùng được gửi đến proxy, sau đó proxy gửi đến website và nhận lại dữ liệu</p>
<p>Chức năng: Tăng tốc độ duyệt web, bảo mật mạng doanh nghiệp và che giấu danh tính</p>
<p>Phân loại Transparent Proxy (Trong suốt): Không ẩn IP, dùng để lọc nội dung trong môi trường công sở/trường học.</p>
<p>Anonymous Proxy (Ẩn danh): Che giấu IP thật nhưng vẫn lộ việc sử dụng Proxy</p>
<p>High Anonymity Proxy (Ẩn danh cao): Bảo mật cao nhất, giấu hoàn toàn IP và danh tính.</p>

<p><b>ACL</b>(Access Control List) Danh sách kiểm soát truy cập. Đây là một cơ chế cực kỳ linh hoạt cho phép kiểm tra các điều kiện của một request (ví dụ: địa chỉ IP nguồn, tên miền truy cập, đường dẫn URL, hoặc HTTP header). Dựa vào kết quả của ACL, HAProxy có thể quyết định chặn (block), chuyển hướng (redirect), hoặc đẩy request đó đến một backend cụ thể</p>
<p><b>Backend</b> là một tập hợp các máy chủ (server) ứng dụng nhận yêu cầu được chuyển tiếp từ proxy để xử lý</p>
<p><b>Frontend </b>là thành phần định nghĩa cách thức nhận và xử lý các yêu cầu (request) từ phía người dùng (client) trước khi chuyển tiếp tới backend</p>
<p><b>Global</b>: Phần cấu hình tổng quát nằm đầu file cấu hình, gồm các thiết lập chung cho toàn hệ thống như maxconn (số kết nối tối đa), log (đường dẫn file log), số tiến trình,… Đây là nơi định nghĩa các thông số quan trọng để đảm bảo hiệu năng và bảo mật cho tất cả dịch vụ do HAProxy quản lý.</p>
<p><b>Default</b> Cụm cấu hình mặc định dùng cho cả frontend và backend phía dưới. Thiết lập trong defaults sẽ được tự động áp dụng trừ khi bị ghi đè bởi cấu hình chi tiết hơn ở frontend hoặc backend. Các tham số phổ biến như mode (chọn TCP hay HTTP proxy), maxconn, log, timeout,… giúp đơn giản hóa và chuẩn hóa nhiều cấu hình.</p>
<p><b>Listen </b> Khối cấu hình kết hợp cả frontend và backend, tinh gọn cho các trường hợp không yêu cầu phân chia rõ ràng giữa điểm vào và điểm ra. Hàm listen thường dùng để cấu hình các dịch vụ nội bộ hoặc đơn giản hóa các trường hợp đặc biệt, khai báo cả IP/port lắng nghe và nhóm backend xử lý trong cùng một block</p>
<p><b>stats: </b>Công cụ thống kê, cho phép cấu hình trang hiển thị các thông số hoạt động của HAProxy. Các tham số như stats uri (đường dẫn truy cập stats), stats refresh (tần suất làm mới), stats admin (giới hạn truy cập), stats auth (chứng thực truy cập) giúp quản trị viên theo dõi hiệu suất thời gian thực cũng như bảo mật thông tin vận hành hệ thống.</p>
<p><b>sticky sessions </b>là kỹ thuật cân bằng tải đảm bảo tất cả các yêu cầu từ một người dùng cụ thể luôn được gửi đến cùng một máy chủ backend trong suốt phiên làm việc</p>
