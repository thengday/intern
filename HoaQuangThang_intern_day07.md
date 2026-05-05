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
<p><b>Sticky sessions </b>Tính năng này cho phép giữ nguyên kết nối của một người dùng đến cùng một backend server trong suốt phiên làm việc. HAProxy hỗ trợ thực hiện sticky session dựa trên cookie hoặc IP client, giúp bảo đảm trạng thái phiên cho các ứng dụng cần lưu trữ dữ liệu tạm thời ở backend mà không làm gián đoạn trải nghiệm người dùng.</p>
<p>Health Check: HAProxy liên tục kiểm tra trạng thái của các backend server thông qua health check. Khi phát hiện máy chủ gặp sự cố hoặc phản hồi bất thường, HAProxy sẽ tự động loại bỏ server đó khỏi vòng cân bằng tải và chỉ chuyển request tới các node còn hoạt động, giúp hệ thống duy trì khả năng phục vụ và giảm nguy cơ downtime.</p>
<p>HAProxy Stats: HAProxy cung cấp trang stats cho phép quản trị viên giám sát hệ thống realtime ngay trên trình duyệt. Giao diện này hiển thị các chỉ số quan trọng về tình trạng server, số lượng kết nối, lưu lượng, trạng thái backend/frontend và nhiều thông tin vận hành khác. Qua đó, việc quản lý, phát hiện sớm bất thường và bảo trì hệ thống trở nên dễ dàng, chủ động hơn.</p>

## Các kiểu load balancing
<p><b>No Load Balancing (Không có cân bằng tải): </b>Đây là mô hình đơn giản nhất, trong đó toàn bộ lưu lượng truy cập được gửi trực tiếp đến một web server duy nhất mà không có bất kỳ lớp trung gian phân phối nào. Giải pháp này thường chỉ sử dụng cho môi trường phát triển, thử nghiệm hoặc khi số lượng truy cập thấp. Tuy nhiên, hình thức này không phù hợp cho sản xuất thực tế vì dễ gây quá tải, không có khả năng mở rộng hoặc đảm bảo dự phòng khi server xảy ra lỗi.</p>
<p><b>Cân bằng tải tầng 4 (Layer 4 – Transport): </b>Đây là hình thức cân bằng tải dựa trên giao thức TCP hoặc UDP, hoạt động ở tầng vận chuyển của mô hình OSI. HAProxy đọc header TCP/UDP để phân phối các kết nối đến backend server, mà không cần quan tâm đến nội dung gói tin ứng dụng. Phương pháp này cho tốc độ xử lý nhanh, tiêu tốn ít tài nguyên và dễ triển khai cho các dịch vụ như web, email, database hoặc game server sử dụng TCP/UDP. Đây cũng là lớp căn bản bảo đảm hiệu năng trong các hệ thống lớn cần đáp ứng nhiều kết nối đồng thời.</p>
<p><b>Cân bằng tải tầng 7 (Layer 7 – Application): </b>Cân bằng tải ở tầng ứng dụng cho phép HAProxy xem xét nội dung HTTP/HTTPS (hoặc các giao thức ứng dụng khác như gRPC, FastCGI). HAProxy có thể xử lý các rule phức tạp như chuyển hướng, phân nhánh lưu lượng dựa vào URL, host, cookie, path, header,… để điều phối request đến backend phù hợp. Nhờ hiểu được logic ứng dụng, loại cân bằng tải tầng 7 được áp dụng nhiều cho các web application, RESTful API và microservices, nơi yêu cầu routing động và kiểm soát linh hoạt nội dung truy cập.</p>

## Các thuật toán load balancing
<p>Round Robin: Đây là thuật toán mặc định và phổ biến nhất, phân phối các kết nối tuần tự lần lượt cho từng backend server. Nhờ đó, các request được xử lý đồng đều và đơn giản, phù hợp với hệ thống có các server đồng nhất về cấu hình và hiệu năng</p>
<p>Weighted Round Robin: Biến thể của Round Robin, cho phép thiết lập trọng số cho từng backend. Server có trọng số cao sẽ nhận nhiều kết nối hơn, thích hợp khi các server có hiệu suất không đồng đều hoặc cần gán ưu tiên cho máy chủ mạnh hơn</p>
<p>Least Connection: Thuật toán sẽ phân phối kết nối mới tới server đang có ít kết nối nhất tại thời điểm hiện tại. Cách này giúp cân bằng tải tốt hơn với các dịch vụ có thời gian xử lý mỗi kết nối khác nhau, hạn chế tình trạng nghẽn tại một server nhất định</p>
<p>Source (IP Hash): Căn cứ theo địa chỉ IP nguồn của client, thuật toán này định tuyến tất cả các request từ cùng một địa chỉ IP về cùng một backend server. Giải pháp này giúp duy trì session liên tục cho người dùng, thích hợp khi cần triển khai sticky session</p>
<p>URL Hash: Trình cân bằng tải sử dụng hash của URL yêu cầu để xác định máy chủ. Điều này đảm bảo rằng một URL cụ thể sẽ luôn được phục vụ bởi cùng một máy chủ, điều này hữu ích trong các trường hợp như việc chia sẻ nội dung từ một máy chủ đến máy chủ khác.</p>

## Tìm hiểu file cấu hình HAProxy
<p>file cấu hình của HAProxy nằm ở /etc/haproxy/haproxy.cfg.</p>
<p><b>global</b>: Phần này định nghĩa các tham số ở mức hệ điều hành và áp dụng cho toàn bộ tiến trình HAProxy. Các cấu hình trong đây thường liên quan đến bảo mật, hiệu năng và logging.</p>
<p>log: Định nghĩa nơi gửi log (thường là rsyslog).</p>
<p>maxconn: Số lượng kết nối tối đa mà HAProxy có thể xử lý cùng lúc.</p>
<p>user / group: Chạy tiến trình HAProxy dưới quyền user/group nào (thường là haproxy).</p>
<p>daemon: Chạy HAProxy dưới dạng background process (tiến trình chạy ngầm).</p>

<p><b>defaults (Cấu hình mặc định) </b>: Phần này chứa các tham số mặc định sẽ được áp dụng cho các phần frontend, backend và listen nằm phía dưới nó, giúp bạn không phải lặp lại cấu hình. Bạn có thể ghi đè (override) các tham số này ở từng phần cụ thể.</p>
<p>mode: Chế độ hoạt động (thường là http cho web hoặc tcp cho database/các giao thức khác).</p>
<p>timeout connect: Thời gian tối đa để kết nối đến backend server.</p>
<p>timeout client: Thời gian chờ client phản hồi trước khi ngắt kết nối.</p>
<p>timeout server: Thời gian chờ server phản hồi trước khi ngắt kết nối.</p>

<p><b>frontend (Đầu vào nhận traffic): </b>Đây là phần định nghĩa cách HAProxy nhận các yêu cầu từ client. Nó quyết định cổng (port) nào đang lắng nghe và các quy tắc (ACL - Access Control List) để điều hướng traffic đi đâu.</p>
<p>bind: Chỉ định IP và Port mà HAProxy sẽ lắng nghe (ví dụ: bind *:80).</p>
<p>acl: Định nghĩa các quy tắc để lọc traffic (ví dụ: nhận diện tên miền, đường dẫn).</p>
<p>use_backend: Quyết định đẩy traffic đến backend nào dựa trên các quy tắc ACL đã định nghĩa.</p>
<p>default_backend: Backend mặc định nếu không có ACL nào khớp.</p>

<p><b>backend (Máy chủ xử lý): </b>Phần này định nghĩa nhóm các máy chủ (servers) thực tế sẽ nhận và xử lý yêu cầu từ HAProxy đẩy xuống, cùng với thuật toán cân bằng tải.</p>
<p>balance: Thuật toán cân bằng tải (ví dụ: roundrobin - xoay vòng, leastconn - ưu tiên server có ít kết nối nhất, source - dựa trên IP client).</p>
<p>server: Định nghĩa từng máy chủ đích với Tên, IP, Port và các tham số khác như check (bật health check)</p>

<p><b>listen (Kết hợp frontend và backend): </b>là một phiên bản gộp chung cả frontend và backend vào một khối duy nhất. Nó thường được dùng cho các cấu hình đơn giản (như TCP proxy) hoặc để cấu hình trang Thống kê (HAProxy Stats page).</p>

## Cài đặt, triển khai Haproxy + Keepalive cho Apache trên Ubuntu 22.04

<p>Mô hình gồm 4 máy. 2 máy phụ trách backend server và 2 máy chạy load balancer để triển khai keepalive</p>
<p>Máy web1: 10.130.10.137</p>
<p>Máy web2: 10.130.10.138</p>
<p>Cài apache cho 2 máy Web</p>
<p>Cài apache cho máy Web 1</p>
<img width="861" height="650" alt="image" src="https://github.com/user-attachments/assets/ab5a8a4b-f539-4bc6-889c-32eeba8b8324" />
<img width="862" height="107" alt="image" src="https://github.com/user-attachments/assets/0442244a-e73e-44a9-bfda-7be8a4683765" />
<img width="840" height="148" alt="image" src="https://github.com/user-attachments/assets/cc09cd14-3b8c-493d-aaa0-f50958c58f6f" />

<p>Cài apache cho máy Web 2</p>
<img width="854" height="225" alt="image" src="https://github.com/user-attachments/assets/d9e301d9-92a7-46ba-80e6-ab16a1247fdc" />
<img width="864" height="124" alt="image" src="https://github.com/user-attachments/assets/b923f6f7-e453-4f83-8805-9835e2481780" />
<img width="858" height="121" alt="image" src="https://github.com/user-attachments/assets/d47a2821-f549-4744-ba88-3a0264b73b12" />

<p>Load Balancer 1: 10.130.10.132</p>
<p>Load Balancer 2: 10.130.10.139</p>

<p>Cài HAProxy trên LB1</p>
<img width="968" height="150" alt="image" src="https://github.com/user-attachments/assets/b20ad2b0-a90d-4f3a-8345-e469458589a9" />
<p>Cấu hình Kernel cho phép IP ảo</p>
<img width="926" height="88" alt="image" src="https://github.com/user-attachments/assets/2850f184-c47a-4812-83af-04abe9c4c3b0" />
<p>Tạo file cấu hình HAProxy</p>
<img width="973" height="526" alt="image" src="https://github.com/user-attachments/assets/fa2b7525-ec31-4ea0-ad0e-75867d41cd25" />
<p>Tạo file cấu hình Keepalived</p>
<img width="1062" height="785" alt="image" src="https://github.com/user-attachments/assets/df6bdf69-9a5b-48d7-98cf-216c9771c82c" />
<img width="1073" height="689" alt="image" src="https://github.com/user-attachments/assets/df700c14-ae2c-42cf-8839-0d933369d3d7" />

<p>Cài HAProxy trên LB2</p>
<img width="989" height="186" alt="image" src="https://github.com/user-attachments/assets/ae4c77ae-f3d5-478d-a772-5fae06412082" />
<p>Cấu hình Kernel cho phép IP ảo</p>
<img width="712" height="89" alt="image" src="https://github.com/user-attachments/assets/428026bf-d80c-4903-9a9c-d46eaf925e27" />
<p>Tạo file cấu hình HAProxy</p>
<img width="1005" height="390" alt="image" src="https://github.com/user-attachments/assets/0855005e-361c-4342-9c5a-0200ad7b13b4" />
<p>Tạo file cấu hình Keepalived</p>
<img width="862" height="337" alt="image" src="https://github.com/user-attachments/assets/c229f78b-3331-4052-919d-2bd5c307437d" />
<img width="877" height="149" alt="image" src="https://github.com/user-attachments/assets/ce4b6560-607d-412e-8187-b08d4cb95caa" />
<p>Set địa chỉ VIP IP là 10.130.10.140</p>
<img width="963" height="162" alt="image" src="https://github.com/user-attachments/assets/3a4babf0-619b-4e7a-a664-077bf769653b" />
<img width="917" height="217" alt="image" src="https://github.com/user-attachments/assets/b9c32c13-d70c-40ea-8dfa-9358371e2e7b" />
<p>Tiến hành tắt máy LB1 </p>
<img width="175" height="112" alt="image" src="https://github.com/user-attachments/assets/5711cffa-a8ed-45b2-900a-417de7b317ce" />
<p>Kiểm tra xem VIP IP còn chạy không</p>
<img width="802" height="182" alt="image" src="https://github.com/user-attachments/assets/4317dbcb-08ad-48d6-a85a-34a49ef205ad" />
<img width="802" height="170" alt="image" src="https://github.com/user-attachments/assets/a13d7c07-9968-453d-b180-39e558bed949" />

