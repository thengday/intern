# Tổng quan ModSecurity
## Khái niệm
<p>ModSecurity là một bộ công cụ tường lửa ứng dụng web (Web Application Firewall – WAF) mã nguồn mở, được thiết kế để cung cấp các chức năng bảo mật và bảo vệ cho các ứng dụng web. Hoạt động bằng cách kiểm tra các yêu cầu HTTP và phản hồi giữa trình duyệt và máy chủ để phát hiện và ngăn chặn các cuộc tấn công nhằm vào các lỗ hổng bảo mật trong ứng dụng web.</p>

<p>Ngoài ra, bản thân ModSecurity là bộ công cụ giúp theo dõi hoạt động và truy cập website theo thời gian thực. Với ModSecurity, bạn có thể làm những gì mình muốn bằng cách chọn đúng các tính năng sẵn có thay vì tuân thủ nghiêm ngặt một khuôn khổ nhất định.</p>

## Cách hoạt động
<p>Modsecurity hoạt động như một hệ thống phát hiện và ngăn chặn xâm nhập (IDPS – Intrusion Detection and Prevention System). Trong quá trình phát hiện xâm nhập, Modsecurity giám sát luồng dữ liệu HTTP, HTTPS khi đi vào (Request) hoặc ra khỏi Web Server (Response), phân tích chúng để tìm kiếm các dấu hiệu của sự kiện bất thường.</p>

<p>Điều này bao gồm việc phát hiện các vi phạm hoặc đe dọa sắp xảy ra đối với chính sách an ninh, chính sách truy cập, hoặc hoạt động không tuân thủ chính sách chuẩn của máy chủ web. Sự kiện bất thường có thể xuất phát từ nhiều nguyên nhân, bao gồm cả việc kẻ tấn công lợi dụng lỗ hổng SQL injection để truy cập hệ thống một cách trái phép và người dùng hợp pháp lạm dụng quyền hoặc cố gắng thêm vào các quyền mà họ không được phép.</p>

<p>Modsecurity thực hiện phát hiện tấn công thông qua hai phương pháp:</p>

<p>Dựa vào các mẫu</p>
<p>Dựa vào các dấu hiệu bất thường</p>
<p>Một trong những cách để phát hiện các cuộc tấn công là sử dụng phương pháp dựa trên mẫu (Pattern) và dấu hiệu (Signature) trong request gửi đến Web server. Các dấu hiệu và mẫu nguy hiểm của các loại tấn công được cấu hình sẵn trong rule. Khi luồng dữ liệu HTTP được kiểm tra và phát hiện chứa các dấu hiệu, mẫu nguy hiểm này, nó sẽ bị cấm. Các hành động kèm theo, như ghi log và mô tả rõ ràng về loại tấn công của request này cũng được thực hiện.</p>

<p>Các mẫu này cụ thể là các ký tự trong các gói tin request hoặc Response, chẳng hạn như request URI, host, user-agent, access-encoding, và cookie. Hầu hết các dạng tấn công đã biết có thể dễ dàng thu thập mẫu thông qua quá trình Capture. Những mẫu đặc biệt trong các kiểu tấn công này sẽ được tích hợp vào các rule.</p>

<p>Từ các thông báo lỗi, người quản trị cũng có thể nhanh chóng khắc phục với sự hỗ trợ của Modsecurity. Các lỗi sẽ hiện ra màn hình dưới sự kiểm soát của Modsecurity, do đó, hacker gặp khó khăn khi cố gắng biết và khai thác các hệ thống này.</p>

<p>Với lỗi trên, chúng ta có thể thực hiện phục hồi tạm thời bằng cách sử dụng rule sau, dựa trên các dấu hiệu đặc thù và nguy hiểm như “ODBC Error Code”:</p>

<p>SecRule RESPONSE BODY “ODBC Error code” Deny,log,status:503,phase:4,msg:”Database Error Message Detected”</p>

<p>Dạng thứ hai của việc phát hiện tấn công là dựa trên các dấu hiệu bất thường. Ngoài các dạng tấn công được liệt kê cụ thể, còn tồn tại nhiều dạng tấn công khác. Các dấu hiệu bất thường bao gồm “bad user-agent”. Ví dụ về một “bad user-agent” có thể được mô tả như sau:</p>

<p>(.|\s|\n)?(script|about|applet|activex|chrome|object)(.|\s|\n)?>.*<(.|\s|\n)?(script|about|applet|activex|chrome|object)</p>
  
## Phân biệt network firewall vs WAF.

| Tiêu chí | Network Firewall (Tường lửa mạng) | WAF (Web Application Firewall) |
| :--- | :--- | :--- |
| **Tầng hoạt động (OSI)** | Tầng mạng và giao vận (**Layer 3 & Layer 4**) | Tầng ứng dụng (**Layer 7**) |
| **Đối tượng bảo vệ** | Toàn bộ hạ tầng mạng, máy chủ và thiết bị nội bộ | Riêng biệt cho các ứng dụng Web (HTTP/HTTPS) và API |
| **Cơ chế lọc traffic** | Dựa trên **IP nguồn/đích, Cổng (Port)** và Giao thức | Dựa trên **Nội dung request**, Headers, Cookies và Payload |
| **Mối đe dọa ngăn chặn** | Quét cổng (Port scanning), DDoS hạ tầng, truy cập trái phép | Lỗ hổng web (OWASP Top 10) như **SQL Injection, XSS** |
| **Vị trí triển khai** | Cửa ngõ hệ thống (Gateway), giữa Internet và mạng nội bộ | Đứng trước Web Server (sau Load Balancer/Reverse Proxy) |

# OWASP Core Rule Set (CRS)
## Nghiên cứu rule chuẩn hóa
### Khái niệm và Mục tiêu của Chuẩn hóa
<p>Chuẩn hóa dữ liệu (hay trong ModSecurity/Coraza gọi là Transformation Functions) là quá trình biến đổi dữ liệu thô từ HTTP Request (GET/POST parameters, Headers, Cookies...) về một dạng chuẩn duy nhất (Canonical Form) trước khi đưa qua bộ lọc Regular Expression (Regex).</p>

<p>Hacker thường sử dụng các kỹ thuật làm nhiễu hoặc mã hóa chuỗi nhằm qua mặt các Signature (dấu hiệu nhận diện) tĩnh của WAF. Nếu không có bước chuẩn hóa, WAF sẽ bị "mù" trước các biến thể này.</p>

### Cấu trúc tập luật

<p>Theo tài liệu kỹ thuật về OWASP CRS và ModSecurity, cấu trúc tập luật được sử dụng trong công cụ này có cú pháp “SecRule VARIABLES OPERATOR [ACTIONS]” và được diễn giải tóm tắt như sau:

<p>- SecRule: Là từ khóa bắt đầu một luật trong ModSecurity.</p>

<p>- VARIABLES: Là biến hoặc tham số mà ModSecurity sẽ kiểm tra trong yêu cầu hoặc phản hồi HTTP. Các biến có thể là:</p>

<p>%{REQUEST_URI}: Địa chỉ URL của yêu cầu.</p>

<p>%{QUERY_STRING}: Chuỗi truy vấn của URL.</p>

<p>%{HTTP_USER_AGENT}: Thông tin trình duyệt của người dùng.</p>

<p>%{REQUEST_BODY}: Nội dung của yêu cầu HTTP.</p>

<p>Các biến khác liên quan đến HTTP headers, cookies...</p>

<p>- OPERATOR: Là toán tử dùng để so sánh hoặc kiểm tra. Các toán tử phổ biến bao gồm:</p>

<p>==: Kiểm tra sự bằng nhau.</p>

<p>@contains: Kiểm tra sự tồn tại của một chuỗi con.</p>

<p>@rx: kiểm tra với một biểu thức chính quy.</p>

<p>@startswith: kiểm tra nếu chuỗi bắt đầu bằng một giá trị cụ thể.</p>

<p>[ACTIONS]: các hành động cần thực hiện khi điều kiện luật được kích hoạt. Các hành động thường gặp là:</p>

<p>deny: Chặn yêu cầu.</p>

<p>allow: Cho phép yêu cầu.</p>

<p>log: Ghi lại thông tin yêu cầu.</p>

<p>alert: Cảnh báo về sự kiện.</p>

<p>redirect: Chuyển hướng yêu cầu đến một URL khác.</p>

<p>Ví dụ luật trong ModSecurity là “SecRule REQUEST_URI "@contains /wp-login.php" "deny,log" thì nghĩa là nó sẽ chặn (deny) và ghi lại (log) mọi yêu cầu có chứa đoạn mã “/wp-login.php” trong URL.</p>

### Thuật toán so khớp
<p>Các thành phần sau trong mỗi yêu cầu (request) từ máy khách được so khớp với tập luật:</p>

<p>- msc_process_request_headers: kiểm tra header của luồng dữ liệu http khi thực hiện request.</p>

<p>- msc_process_request_body: kiểm tra nội dung body của luồng dữ liệu http khi thực hiện request.</p>

<p>- msc_process_response_headers: kiểm tra header của luồng dữ liệu http khi thực hiện response.</p>

<p>- msc_process_response_body: kiểm tra nội dung body của luồng dữ liệu http khi thực hiện response.</p>

<p>Quá trình so khớp này thường được thực hiện dựa trên thuật toán Boyer-Moore-Horspool theo cách thức như sau:</p>
<img width="528" height="435" alt="image" src="https://github.com/user-attachments/assets/608231fb-694c-4aba-8596-4fbb9dffce51" />
