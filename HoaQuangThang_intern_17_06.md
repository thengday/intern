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

### Cơ chế chuẩn hóa dữ liệu
<p>Trước khi kiểm tra một Request có phải là tấn công hay không, CRS phải đưa dữ liệu về dạng "chuẩn" nhất. Kẻ tấn công thường sử dụng các kỹ thuật Obfuscation như encode URL, chèn khoảng trắng, đổi chữ hoa/chữ thường để qua mặt WAF.</p>
<p>CRS sử dụng các hàm chuyển đổi của ModSecurity để giải quyết vấn đề này:</p>
<p>Giải mã: Chuyển đổi các định dạng mã hóa về văn bản thô.</p>
<p>t:urlDecode: Giải mã URL-encoded (ví dụ: %27 thành ').</p>

<p>t:htmlEntityDecode: Giải mã các thực thể HTML (ví dụ: &#x27; thành ').</p>

<p>t:base64Decode: Giải mã chuỗi Base64.</p>

<p>Xử lý chuỗi (String Manipulation): * t:lowercase: Chuyển toàn bộ thành chữ thường để so sánh chuẩn (ví dụ: sElEcT thành select).</p>

<p>t:compressWhitespace: Thu gọn nhiều khoảng trắng liên tiếp hoặc ký tự xuống dòng thành một khoảng trắng duy nhất nhằm phá vỡ các kỹ thuật bypass bằng khoảng trắng.</p>
<p>Quy trình hoạt động: Một Input đầu vào có thể được áp dụng chuỗi nhiều hàm chuyển đổi (ví dụ: t:urlDecode,t:htmlEntityDecode,t:lowercase) trước khi đối sánh với Regex của Rule.</p>

### Cách CRS phân loại

<p>911xxx (Method Enforcement): Kiểm tra và chặn các HTTP Method lạ hoặc nguy hiểm (không phải GET, POST, PUT...).</p>

<p>913xxx (Scanner Detection): Phát hiện các công cụ quét lỗ hổng tự động (như Acunetix, Nikto, sqlmap, Nmap) dựa trên hành vi hoặc User-Agent.</p>

<p>920xxx (Protocol Violations): Phát hiện hành vi vi phạm giao thức HTTP chuẩn (thiếu header bắt buộc, sai Content-Length, HTTP smuggling...).</p>

<p>921xxx (HTTP Request Smuggling): Các quy tắc chuyên biệt chống lại tấn công thao túng Request giữa Proxy và Backend.</p>

<p>930xxx (Local File Inclusion - LFI): Ngăn chặn nỗ lực duyệt thư mục để đọc file hệ thống (như ../../etc/passwd).</p>

<p>931xxx (Remote File Inclusion - RFI): Chặn việc chèn link độc hại từ bên ngoài vào câu lệnh include của ứng dụng.</p>

<p>932xxx (Remote Code Execution - RCE): Phát hiện việc thực thi các lệnh hệ điều hành (như id, whoami, powershell) qua input.</p>

<p>933xxx (PHP Injection): Phát hiện việc chèn và thực thi mã PHP độc hại (các hàm eval(), system()).</p>

<p>941xxx (Cross-Site Scripting - XSS): Phát hiện mã script (JavaScript, HTML) độc hại chèn vào ứng dụng nhằm tấn công trình duyệt người dùng.</p>

<p>942xxx (SQL Injection - SQLi): Phát hiện từ khóa, hàm hoặc biểu thức logic SQL để thao túng cơ sở dữ liệu.</p>

<p>943xxx (Session Fixation): Phát hiện các nỗ lực giả mạo hoặc cố định Session ID trong Cookie hoặc URL.</p>

### Cơ chế chặn 

<p>CRS nổi tiếng với việc không sử dụng cơ chế chặn ngay lập tức khi gặp một rule khớp, mà sử dụng cơ chế Tính điểm bất thường</p>
<p>Mỗi khi một Request vi phạm một Rule, nó chưa bị chặn ngay mà sẽ bị cộng một số điểm "bất thường" dựa trên mức độ nghiêm trọng của Rule đó:</p>
<p>CRITICAL (Điểm = 5): Khả năng cao là tấn công thực sự (ví dụ: SQLi, RCE thành công).</p>

<p>ERROR (Điểm = 4): Lỗi nghiêm trọng, thường là rò rỡ thông tin hoặc vi phạm giao thức nặng.</p>

<p>WARNING (Điểm = 3): Các hành vi đáng ngờ (ví dụ: thiếu một số header phổ biến).</p>

<p>NOTICE (Điểm = 2): Các vi phạm giao thức chuẩn nhỏ.</p>

<p>Quy trình chặn qua hai giai đoạn: </p>
<p>Phase 2 (Request Check): Khi Request đi qua, các rule từ 910 đến 944 sẽ kiểm tra. Nếu vi phạm, điểm số sẽ được cộng dồn vào biến TX:anomaly_score.</p>

<p>Rule 949110 (Inbound Blocking Rule): Nằm ở cuối Phase 2. Quy tắc này sẽ kiểm tra xem tổng điểm TX:anomaly_score có vượt quá ngưỡng cấu hình (Inbound Anomaly Score Threshold - mặc định là 5) hay không. Nếu bằng hoặc vượt quá, WAF sẽ thực hiện hành động chặn (thường trả về lỗi HTTP 403 Forbidden).</p>

<p>Phase 4 (Response Check) là giai đoạn WAF kiểm tra dữ liệu phản hồi từ máy chủ (Backend) trước khi trả về cho người dùng.</p>

<p>Nhiệm vụ chính:</p>

<p>Chống rò rỉ dữ liệu (DLP): Chặn việc lộ số thẻ tín dụng, thông tin cá nhân, mã nguồn.</p>

<p>Giấu lỗi hệ thống: Chặn các thông báo lỗi chi tiết của Database (MySQL, Oracle...) hoặc mã PHP/Apache để kẻ tấn công không thể dò tìm lỗ hổng.</p>

<p>Phát hiện Webshell: Chặn dữ liệu trả về nếu phát hiện dấu hiệu máy chủ đã bị chiếm quyền và đang thực thi lệnh độc hại.</p>

<p>Cơ chế chặn: Nếu tổng điểm vi phạm ở phản hồi (TX:outbound_anomaly_score) vượt ngưỡng cấu hình (mặc định là 4), Rule 959110 sẽ chặn đứng và trả về lỗi HTTP 500, ngăn không cho dữ liệu nhạy cảm thoát ra ngoài.</p>

### Cài đặt và cấu hình trên Apache: bật module, cấu hình SecRuleEngine, tích hợp OWASP CRS.
<p>Cài đặt Apache</p>
<img width="820" height="317" alt="image" src="https://github.com/user-attachments/assets/2efa8593-ae81-4b9d-ab40-022e8614ec12" />

<img width="823" height="480" alt="image" src="https://github.com/user-attachments/assets/ea47d40f-f4c5-4403-a56c-1ad358ac833e" />
<p>Bật module</p>
<img width="599" height="122" alt="image" src="https://github.com/user-attachments/assets/1f1d155d-af27-4537-b192-e2a52f5023d1" />

#### Cấu hình SecRuleEngine tích hợp OWASP CRS.
<p>Tạo file cấu hình</p>
<img width="911" height="42" alt="image" src="https://github.com/user-attachments/assets/17eb1a1e-fe33-4dba-bd75-e8ef44f6d24e" />
<p>Mở file để chỉnh sửa</p>
<p>Bật SecruleEngine</p>
<img width="767" height="460" alt="image" src="https://github.com/user-attachments/assets/4dccdfe3-527a-49e5-bdda-45cb69c3ce6c" />
<p>Tải bộ luật CRS</p>
<img width="826" height="493" alt="image" src="https://github.com/user-attachments/assets/99e39a92-10f4-451a-b592-689e9394ac68" />
<p>Kiểm tra cú pháp</p>
<img width="935" height="93" alt="image" src="https://github.com/user-attachments/assets/4501f351-6981-4102-a14f-51019f741029" />
<p>Kiểm tra SQLi và đọc file hệ thống</p>
<img width="798" height="236" alt="image" src="https://github.com/user-attachments/assets/90edf975-2d17-420b-871a-57f5f1174436" />
<p>Check log hệ thống hiển thị lỗi 403</p>
<img width="1044" height="501" alt="image" src="https://github.com/user-attachments/assets/67df66a4-5e38-4f5b-81b5-4cdcea43e514" />

## Cài đặt ModSecurity 3 (connector) trên Nginx: biên dịch hoặc dùng dynamic module, cấu hình modsecurity.conf.
### Cài Nginx 
<img width="913" height="433" alt="image" src="https://github.com/user-attachments/assets/4e38a167-185a-4bb8-87e1-f5d792c7772a" />
<p>CÀI ĐẶT CÁC THƯ VIỆN PHỤ THUỘC</p>
<img width="1043" height="409" alt="image" src="https://github.com/user-attachments/assets/54c16236-fc22-4098-8664-14699b724ed1" />
<p>CÀI ĐẶT LIBMODSECURITY</p>
<img width="1034" height="534" alt="image" src="https://github.com/user-attachments/assets/2af34efe-335c-4503-8692-1220e1b474e3" />
<img width="916" height="612" alt="image" src="https://github.com/user-attachments/assets/12f20709-089d-4125-a91b-c4e90a98f666" />
<p>Tải mã nguồn bộ kết nối Nginx Connector:</p>
<img width="899" height="617" alt="image" src="https://github.com/user-attachments/assets/02c176bf-f17c-42ff-af04-98e9a20734d5" />
<p>Biên dịch module</p>
<img width="818" height="622" alt="image" src="https://github.com/user-attachments/assets/21f7564d-c21b-4260-a575-65361bc5ad10" />
<img width="932" height="111" alt="image" src="https://github.com/user-attachments/assets/b921b29a-e167-4aed-85ec-1803ca2821d9" />

<p>Khai báo nạp Module và cấu hình modsecurity.conf</p>
<img width="519" height="192" alt="image" src="https://github.com/user-attachments/assets/19b6e8fa-2ceb-48e3-acbe-88879378d63a" />
