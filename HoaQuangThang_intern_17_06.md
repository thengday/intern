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
