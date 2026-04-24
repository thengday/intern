# Triển khai ứng dụng mail server MDaemon
## Cài đặt email server MDaemon trên windows server 2019 (hoặc 2022)
<img width="566" height="385" alt="image" src="https://github.com/user-attachments/assets/4c01f362-fbda-4ee7-bc2b-1fcd7a8e1200" />
<img width="578" height="378" alt="image" src="https://github.com/user-attachments/assets/3a52f612-c449-4dd8-90de-fa8b893792c0" />


## Truy cập admin và enduser
<p>Giao diện enduser truy cập vào đường dẫn http://10.130.10.131:3000/</p>
<img width="1717" height="709" alt="image" src="https://github.com/user-attachments/assets/861a8780-49ec-4efd-99d7-3ad37f32a08a" />
<img width="1725" height="782" alt="image" src="https://github.com/user-attachments/assets/fa739306-4348-4017-b92a-c7fee489f205" />
<p>Giao diện admin</p>
<img width="1663" height="769" alt="image" src="https://github.com/user-attachments/assets/32332d4a-d8e5-4482-a316-1f47a07f615a" />
<img width="1695" height="812" alt="image" src="https://github.com/user-attachments/assets/27087116-c700-41f0-a45a-7896c19ba2c4" />

## Các port cần thiết được sử dụng trên email server MDaemon
<img width="809" height="395" alt="image" src="https://github.com/user-attachments/assets/c3ff67f9-b6d9-462c-b37f-194adb0324f9" />
<p>SMTP: Port 25, POP3: Port 110, IMAP: Port 143, Webmail: Port 3000, XMPP: Port 5222 và 5223</p>

## Khởi tạo domain, user, group, Alias, Mailing lists email
<p>Đã tạo domain nhanhoa.local</p><img width="1664" height="151" alt="image" src="https://github.com/user-attachments/assets/f7c36598-63df-4b52-96a5-b234874dab44" />
<p>Khởi tạo user. Vào account manager->NEW</p>
<img width="1677" height="213" alt="image" src="https://github.com/user-attachments/assets/1d2879c7-4aa6-4877-bbd5-63c30ca7c96c" />
<img width="1084" height="720" alt="image" src="https://github.com/user-attachments/assets/0fe83629-67db-42b0-846d-274693d3658c" />
<img width="1702" height="244" alt="image" src="https://github.com/user-attachments/assets/b3448bdc-411b-49b9-abd1-bdc074023d9b" />
<img width="1702" height="244" alt="image" src="https://github.com/user-attachments/assets/0eafc6f1-0e5e-4951-9cd2-1ce82a23e24c" />
<p>Group</p>
<img width="1699" height="365" alt="image" src="https://github.com/user-attachments/assets/e8d92903-711b-4efd-9e0b-4010db5a29ac" />
<img width="1250" height="812" alt="image" src="https://github.com/user-attachments/assets/1c484706-7975-4177-91be-ef06d098817a" />
<img width="1207" height="816" alt="image" src="https://github.com/user-attachments/assets/507805d6-545b-4f06-9fcd-fbd3c398adc2" />
<img width="955" height="815" alt="image" src="https://github.com/user-attachments/assets/b58f058a-2591-4751-af51-88871c464307" />

<p>Alias</p>
<img width="1701" height="371" alt="image" src="https://github.com/user-attachments/assets/db49a21a-c7f7-4ce4-ac74-06a3e3cafeea" />
<img width="933" height="665" alt="image" src="https://github.com/user-attachments/assets/ff623984-3dfa-454a-a06d-f214a889a985" />
<img width="954" height="695" alt="image" src="https://github.com/user-attachments/assets/fa7644ec-dfc0-4f57-8e26-2c0dfe5c9b07" />
<img width="1665" height="255" alt="image" src="https://github.com/user-attachments/assets/71bdefb4-602f-4787-b162-6f333420306d" />

<p>Mali list</p>
<img width="1686" height="739" alt="image" src="https://github.com/user-attachments/assets/08f9027b-3db2-4885-b4f7-dbeb51ba8806" />
<img width="1032" height="782" alt="image" src="https://github.com/user-attachments/assets/32990c22-f4ac-4fee-a0e6-e7922d5e32b2" />
<img width="961" height="769" alt="image" src="https://github.com/user-attachments/assets/0e78c3a4-45bc-41db-a73e-3dc1a6b16516" />


## Thiết lập chính sách về mật khẩu account email
<img width="1639" height="729" alt="image" src="https://github.com/user-attachments/assets/0071158c-1edc-4bcd-a8af-c58eeb33e190" />

##Thiết lập chữ ký email
<p>Thiết lập Chữ ký chung toàn hệ thống</p>
<img width="1709" height="818" alt="image" src="https://github.com/user-attachments/assets/2143967e-0c8c-48e5-bdaa-45e9c575e559" />

<p>Thiết lập Chữ ký cá nhân trên Webmail</p>
<img width="1707" height="874" alt="image" src="https://github.com/user-attachments/assets/177b9e34-52bf-4659-b936-503ee1c3416c" />

<img width="720" height="594" alt="image" src="https://github.com/user-attachments/assets/6e05d6f0-d92f-4ac1-9a4b-d9efa73a23fd" />

## Thiết lập forward email
<p>Enable Forwading</p>
<img width="1716" height="811" alt="image" src="https://github.com/user-attachments/assets/460fad07-b1f7-4e83-a0ef-74b9005175d6" />
<img width="1725" height="774" alt="image" src="https://github.com/user-attachments/assets/aebdf1b7-2e36-44d0-be5e-167dace685f7" />

## Tìm hiểu về Content Filter: Spam, Antivirus, Attach Filters, Message Filters
<p>Spam Filter: Bộ lọc này chịu trách nhiệm phân tích xem một email đến có phải là thư quảng cáo rác, lừa đảo (phishing) hay không. MDaemon sử dụng hệ thống chấm điểm. Mỗi email khi đi qua sẽ bị soi xét các yếu tố: từ khóa trong nội dung. Địa chỉ IP của người gửi có nằm trong danh sách đen quốc tế</p>
<p>Antivirus Antivirus quét mã độc thực tế. MDaemon thường tích hợp với các engine diệt virus. Khi một email có chứa tệp đính kèm hoặc các đoạn mã HTML khả nghi, hệ thống sẽ chặn lại ở hàng đợi, bung file ra và quét chữ ký virus xem có khớp với các loại mã độc đã biết hay không</p>
<p>Attachment Filters: Lọc dựa trên định dạng (phần mở rộng - extension) của tệp hoặc kích thước tệp. Các bộ lọc thông minh thậm chí có thể quét sâu vào cấu trúc file để biết người dùng có đang cố tình đổi tên file để qua mặt hệ thống hay không</p>
<p>Message Filters: Lọc dựa trên thông tin Header (Người gửi, Người nhận, Tiêu đề) hoặc Body (Nội dung bên trong).</p>

## Đổi mật khẩu account admin global, admin domain
<p>Global Administrator (Quản trị viên toàn cục): Có toàn quyền kiểm soát toàn bộ máy chủ MDaemon, bao gồm tất cả các tên miền, cấu hình bảo mật, cổng mạng và dịch vụ. Thường mặc định là tài khoản postmaster@tenmien_chinh.com</p>
<p>Domain Administrator (Quản trị viên tên miền): Chỉ có quyền quản lý (tạo, xóa, sửa tài khoản) trong phạm vi một tên miền cụ thể được giao. Không có quyền can thiệp vào cài đặt cốt lõi của máy chủ</p>
<img width="1091" height="853" alt="image" src="https://github.com/user-attachments/assets/b197c444-f75a-402b-9761-70f39627e7f9" />

## Phân quyền cho tài khoản thành admin của domain
<img width="1707" height="798" alt="image" src="https://github.com/user-attachments/assets/ef356d2a-56d4-4822-814f-f73672df909a" />
<img width="1085" height="793" alt="image" src="https://github.com/user-attachments/assets/a3dcb071-334e-4483-bbfc-025f3a74005e" />
<img width="1069" height="615" alt="image" src="https://github.com/user-attachments/assets/345bf536-64b2-43cf-a7ea-efacb633fbd9" />

## Kiểm tra log gửi/nhận email (đặc biệt chú ý)
<img width="1695" height="564" alt="image" src="https://github.com/user-attachments/assets/12b08b1e-e2cf-4c57-a0de-9d88e745ecb2" />
<img width="1715" height="194" alt="image" src="https://github.com/user-attachments/assets/a448e973-4339-4839-8f8d-a8cdb3f1dc9d" />

## Tìm hiểu thêm về Dynamic screening trong Security của MDaemon
<p>Mục đích chính của tính năng này là chống lại các cuộc tấn công Brute-force (Dò mật khẩu) và Dictionary Attack (Tấn công từ điển). Khi hacker dùng phần mềm tự động thử hàng ngàn mật khẩu khác nhau để hack vào một tài khoản email, Dynamic Screening sẽ phát hiện sự bất thường và chặn đứng chúng trước khi chúng kịp tìm ra mật khẩu đúng</p>

## Tìm hiểu Backup/restore email (nếu được)
<p>Backup Copy file mdaemon ra một ổ cứng bên ngoài </p>
<img width="761" height="613" alt="image" src="https://github.com/user-attachments/assets/d735c9dc-bf1f-4187-9d1f-7e54c024ce36" />
<p>Khôi phục toàn bộ hệ thống chỉ cần Paste vào file mdaemon đã cài và khởi động lại mdaemon</p>
