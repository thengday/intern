# HTTP / HTTPS — Cơ chế request/response & status codes 
## Nghiên cứu vòng đời của một HTTP request
```
[Client]
  │
  ├─ 1. Tạo HTTP Request (method, URL, headers, body)
  ├─ 2. DNS Lookup (domain → IP)
  ├─ 3. TCP Handshake (3-way)
  ├─ 4. TLS Handshake (nếu HTTPS)
  │
[Network / Internet]
  │
  ├─ 5. Load Balancer (phân phối traffic)
  ├─ 6. Reverse Proxy (SSL termination, cache, compression)
  ├─ 7. API Gateway (auth, rate limit, routing)
  │
[Backend Server]
  │
  ├─ 8. Web Server nhận, cấp thread/event
  ├─ 9. Middleware chain (auth, logging, tracing)
  ├─ 10. Controller (parse, validate request)
  ├─ 11. Service Layer (business logic)
  ├─ 12. Cache check (Redis, Memcached)
  ├─ 13. Database query (SQL/NoSQL)
  ├─ 14. Transaction (nếu cần)
  ├─ 15–16. Internal service calls (sync/async)
  │
[Response]
  │
  ├─ 17. Serialize (object → JSON)
  ├─ 18. Compress (gzip/brotli)
  ├─ 19. Đi ngược lại toàn bộ hành trình về client
  └─ 20. Browser parse và render
```
<p>1. Phân giải DNS: Dịch tên miền (ví dụ: example.com) thành địa chỉ IP để máy tính có thể nhận diện được máy chủ.</p>

<p>2. Thiết lập kết nối TCP: Tạo một kênh giao tiếp đáng tin cậy giữa trình duyệt và máy chủ thông qua quá trình "bắt tay 3 bước".</p>

<p>3. Bảo mật TLS/SSL: Mã hóa đường truyền dữ liệu (áp dụng với HTTPS) để đảm bảo thông tin không bị đánh cắp.</p>

<p>4. Gửi HTTP Request: Trình duyệt đóng gói yêu cầu (gồm đường dẫn, tiêu đề, và dữ liệu nếu có) rồi gửi tới máy chủ.</p>

<p>5. Xử lý tại Server: Máy chủ tiếp nhận yêu cầu, thực thi logic (có thể truy vấn cơ sở dữ liệu) và chuẩn bị kết quả.</p>

<p>6. Trả HTTP Response: Máy chủ gửi lại phản hồi cho trình duyệt, bao gồm mã trạng thái (ví dụ: 200 OK) và nội dung trang web.</p>

<p>7. Trình duyệt hiển thị: Trình duyệt phân tích dữ liệu nhận được (HTML, CSS, JS), tải thêm tài nguyên phụ và vẽ giao diện lên màn hình cho bạn xem.</p>

## Phân tích cấu trúc HTTP request (method, URI, headers, body) 
<p>Một HTTP request bao gồm:</p>

</p>Request line</p>
</p>Body request ( có thể có hoặc không)</p>

<p><b>Request line</b> là dòng đầu tiên trong HTTP request. Nó bao gồm 3 phần:</p>
<img width="470" height="104" alt="image" src="https://github.com/user-attachments/assets/04bcbee4-8e7a-4790-bf82-904914f78d74" />

<p>Phương thức HTTP được sử dụng</p>
<p>URI( Uniform Resource Identifier) giúp xác định các tài nguyên mà client yêu cầu.</p>
<p>Phiên bản của giao thức HTTP</p>
<p>Một request line sẽ có định dạng như sau: GET /BookStore/v1/Books HTTP/1.1</p>

<p><b>Request header</b></p>
<p>Request header giúp client có thể gửi yêu cầu lên server. Mỗi yêu cầu sẽ kèm theo các thông số, và các thông số đó được gọi là Header Parameters. Trình duyệt và server sẽ dựa vào các thông số header này để trả dữ liệu và hiển thị dữ liệu cho phù hợp.</p>
<p>Các thông số có thể gặp khá thường xuyên như:</p>
<img width="310" height="70" alt="image" src="https://github.com/user-attachments/assets/7d57d7cc-090b-4d1b-862e-d83be251e942" />

<p>User-Agent: cho phép server xác định ứng dụng, hệ điều hành, nhà cung cấp và phiên bản.</p>
<p>Connection: kiểm soát kết nối mạng. Nói cách khác, cho phép dừng hoặc tiếp tục kết nối sau khi server thực hiện xong yêu cầu.</p>
<p>Cache-Control: chỉ định chính sách bộ nhớ đệm của trình duyệt.</p>
<p>Accept-Language: cho biết tất cả các ngôn ngữ (tự nhiên) mà client có thể hiểu được.</p>

<p><b>Request body</b></p>
<p>Cho phép client gừi đến yêu cầu bổ sung cần server thực hiện như: tạo mới hoặc cập nhật dữ liệu mà không thể truyền trên Header Parameters.</p>

<p>Request body thường được sử dụng trong các phương thức Post, Put, Patch.</p>
<img width="448" height="57" alt="image" src="https://github.com/user-attachments/assets/a5a67492-1884-435f-9ab3-b7914f9257ab" />

## Lập bảng phân loại đầy đủ status codes (1xx, 2xx, 3xx, 4xx, 5xx) kèm ý nghĩa thực tế và kịch bản gặp phải.
| Nhóm / Mã | Tên Trạng Thái | Ý nghĩa | Kịch bản thực tế gặp phải |
| :--- | :--- | :--- | :--- |
| **1xx** | **Thông tin (Informational)** | **Yêu cầu đã được nhận, quá trình đang tiếp tục.** | Rất ít khi hiển thị trực tiếp cho người dùng. |
| 100 | Continue | Máy chủ đã nhận phần đầu và client có thể tiếp tục gửi phần thân. | Client gửi file lớn, kiểm tra trước với server xem có được phép tải lên không. |
| 101 | Switching Protocols | Máy chủ đồng ý đổi giao thức giao tiếp theo yêu cầu. | Nâng cấp từ kết nối HTTP thông thường lên WebSockets. |
| **2xx** | **Thành công (Successful)** | **Yêu cầu đã được nhận, hiểu và xử lý thành công.** | Trạng thái lý tưởng của mọi ứng dụng. |
| 200 | OK | Thành công tiêu chuẩn cho GET, POST. | Truy cập web tải thành công; gửi form đăng nhập thành công. |
| 201 | Created | Yêu cầu thành công và một tài nguyên mới vừa được tạo. | Đăng ký tài khoản mới, tạo bài viết mới (POST/PUT). |
| 204 | No Content | Yêu cầu xử lý thành công nhưng không có nội dung trả về. | Xóa bình luận, không cần trả về giao diện gì thêm. |
| **3xx** | **Chuyển hướng (Redirection)** | **Cần thực hiện thêm hành động để hoàn thành yêu cầu.** | Thường dùng cho SEO hoặc thay đổi cấu trúc web. |
| 301 | Moved Permanently | Tài nguyên đã được chuyển vĩnh viễn sang URL mới. | Đổi tên miền, Google sẽ cập nhật link này. |
| 302 | Found (Temporary) | Tài nguyên đang tạm thời nằm ở URL khác. | Trang web bảo trì, tạm chuyển hướng sang trang thông báo. |
| 304 | Not Modified | Dữ liệu không đổi từ lần tải cuối. Dùng bản lưu Cache. | Tải lại trang vừa vào 5 phút trước, tiết kiệm băng thông. |
| **4xx** | **Lỗi Máy Khách (Client Error)** | **Yêu cầu chứa cú pháp sai hoặc không thể thực hiện.** | Lỗi do phía người dùng hoặc trình duyệt (bạn làm sai). |
| 400 | Bad Request | Máy chủ không hiểu yêu cầu do cú pháp sai. | Gửi API thiếu trường bắt buộc, định dạng JSON sai. |
| 401 | Unauthorized | Cần xác thực (đăng nhập) để truy cập. | Vào trang quản trị nhưng chưa đăng nhập hoặc hết session. |
| 403 | Forbidden | Đã xác thực nhưng không có quyền truy cập. | Nhân viên truy cập vào báo cáo dành riêng cho giám đốc. |
| 404 | Not Found | Không tìm thấy tài nguyên được yêu cầu. | Gõ sai URL hoặc bài viết đã bị xóa. |
| 405 | Method Not Allowed | Phương thức không được phép với đường dẫn này. | Gửi dữ liệu (POST) vào endpoint chỉ cho đọc (GET). |
| 429 | Too Many Requests | Gửi quá nhiều yêu cầu trong thời gian ngắn. | Spam liên tục, bị hệ thống Rate Limiting chặn lại. |
| **5xx** | **Lỗi Máy Chủ (Server Error)** | **Máy chủ không thể thực hiện một yêu cầu hợp lệ.** | Lỗi do phía Backend, DevOps (họ làm sai). |
| 500 | Internal Server Error | Lỗi chung chung khi máy chủ gặp sự cố bất ngờ. | Mã nguồn Backend lỗi (chia cho 0, gọi biến không tồn tại). |
| 502 | Bad Gateway | Proxy/Gateway nhận phản hồi không hợp lệ từ máy chủ chính. | Proxy chạy bình thường nhưng Backend (Node.js) đằng sau sập. |
| 503 | Service Unavailable | Máy chủ không thể xử lý yêu cầu (quá tải/bảo trì). | Bị DDoS cạn kiệt tài nguyên, hoặc server đang nâng cấp. |
| 504 | Gateway Timeout | Máy chủ trung gian không nhận được phản hồi kịp thời. | Backend xử lý quá lâu khiến kết nối ngắt do hết giờ. |

```
Persistent Connection (Kết nối bền bỉ)
Đây là khác biệt lớn nhất và ảnh hưởng trực tiếp nhất đến tốc độ tải trang.

HTTP/1.0 (Mặc định là Short-lived Connections):

Mỗi khi trình duyệt muốn tải một tài nguyên (ví dụ: 1 file HTML, 1 file CSS, 1 hình ảnh), nó phải mở một kết nối TCP mới, thực hiện "bắt tay 3 bước" (3-way handshake), gửi request, nhận response, và sau đó đóng kết nối ngay lập tức.

Nhược điểm: Vô cùng lãng phí tài nguyên và thời gian. Nếu một trang web có 50 hình ảnh, mạng sẽ phải thực hiện 50 lần mở/đóng kết nối TCP, gây ra độ trễ (latency) rất cao.

HTTP/1.1 (Mặc định là Persistent Connections):

HTTP/1.1 mặc định giữ cho kết nối TCP luôn mở (Connection: keep-alive).

Ưu điểm: Trình duyệt có thể tái sử dụng một kết nối TCP duy nhất để gửi/nhận hàng chục tài nguyên liên tiếp. Điều này giúp loại bỏ hoàn toàn thời gian hao phí cho các lần bắt tay TCP/TLS thừa thãi, giảm tải cho CPU của máy chủ và tăng tốc độ duyệt web đáng kể.

Pipelining
Pipelining là một nỗ lực của HTTP/1.1 để tối ưu hóa hơn nữa luồng dữ liệu trên các kết nối TCP đã được giữ mở.
HTTP/1.0 (Tuần tự nghiêm ngặt):
Hoạt động theo cơ chế Ping-Pong. Trình duyệt gửi Request A $\rightarrow$ Chờ nhận xong Response A $\rightarrow$ Mới được gửi tiếp Request B. Quá trình này tạo ra nhiều khoảng thời gian "chết" trên đường truyền.
HTTP/1.1 (Hỗ trợ Pipelining):
Trình duyệt có thể "bắn" liên tục nhiều Request (A, B, C) vào cùng một kết nối TCP mà không cần phải chờ Server trả về.Nhược điểm chí mạng (Head-of-Line Blocking): Mặc dù Client có thể gửi nhiều Request cùng lúc, Server HTTP/1.1 bắt buộc phải trả về Response theo đúng thứ tự đã nhận (Response A $\rightarrow$ Response B $\rightarrow$ Response C). Nếu Request A là một truy vấn cơ sở dữ liệu rất nặng và mất 5 giây để xử lý, thì B và C dù đã xử lý xong trong 0.1 giây vẫn phải xếp hàng chờ A gửi đi xong. Do hạn chế này, Pipelining hiếm khi được bật mặc định trên các trình duyệt hiện đại (sau này HTTP/2 ra đời dùng cơ chế Multiplexing để giải quyết triệt để lỗi này).

Chunked Transfer Encoding (Truyền tải phân mảnh)
Tính năng này thay đổi cách máy chủ đóng gói dữ liệu để gửi về cho người dùng, đặc biệt quan trọng đối với các web động (dynamic web).
HTTP/1.0 (Bắt buộc phải biết trước dung lượng):
Theo chuẩn, máy chủ phải tính toán xong toàn bộ nội dung phản hồi để biết kích thước chính xác và điền vào Header Content-Length, sau đó mới được gửi đi.

Nhược điểm: Nếu bạn truy xuất một báo cáo dữ liệu lớn từ Database, Server sẽ phải giữ kết nối, "kìm hãm" không gửi gì cả cho đến khi nó render xong toàn bộ báo cáo đó. Người dùng sẽ thấy màn hình trắng trong thời gian dài.
HTTP/1.1 (Sử dụng Chunked Transfer Encoding):

HTTP/1.1 giới thiệu header Transfer-Encoding: chunked. Máy chủ không cần biết trước tổng kích thước của Response nữa.

Ưu điểm: Máy chủ có thể chia nhỏ dữ liệu thành các "khối" (chunks) và gửi dần về cho trình duyệt ngay khi khối đó được xử lý xong. Trình duyệt sẽ nhận và hiển thị từng phần của trang web (ví dụ: hiển thị header trước, rồi đến nội dung bài viết, rồi đến footer) giúp cải thiện trải nghiệm người dùng rất nhiều. Nó cũng là nền tảng cho việc truyền phát video/audio (streaming).
```

## Thực hành: dùng curl -v để quan sát raw headers của ít nhất 5 website khác nhau
<img width="1321" height="598" alt="image" src="https://github.com/user-attachments/assets/576d41a9-7f20-423f-a822-d74774360ff4" />
<img width="1345" height="638" alt="image" src="https://github.com/user-attachments/assets/a25d1743-9e3f-4d27-9b37-ed88edbb752d" />
<img width="903" height="337" alt="image" src="https://github.com/user-attachments/assets/e80f4947-3ee5-4d76-8d31-540dc8f436ce" />
<img width="1382" height="698" alt="image" src="https://github.com/user-attachments/assets/c30d4caf-2509-4765-846e-0914840e0f3d" />
<img width="902" height="408" alt="image" src="https://github.com/user-attachments/assets/6793bf57-c533-42f0-90f6-6914c1809eb0" />
