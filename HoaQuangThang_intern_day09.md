# Tìm hiểu về Hosting Control panel
<p>Hosting control panel (hay Bảng điều khiển Hosting) là bộ công cụ quan trọng giúp người quản trị dễ dàng điều hành và kiểm soát các dịch vụ hosting của họ. Thông qua control panel, có thể thực hiện nhiều tác vụ khác nhau như quản lý email accounts, FTP accounts, file management functions, create backups,… một cách tập trung và thuận tiện. Hỗ trợ quản lý tất cả các thành phần liên quan đến dịch vụ hosting</p>

## Các chức năng của Hosting Control panel
<p><b> Quản lý Tên miền (Domain & DNS): </b>Người dùng có thể thêm tên miền mới (Addon Domain), tạo tên miền con (Subdomain) để chạy các dự án phụ, hoặc cấu hình chuyển hướng (Redirect). Đặc biệt, trình quản lý DNS Zone cho phép trỏ tên miền về địa chỉ IP, cấu hình hồ sơ MX cho email một cách nhanh chóng.</p>

<p><b>Quản lý Tập tin (File Manager & FTP): </b>Thay vì phải sử dụng phần mềm bên thứ ba như FileZilla, đa số Control Panel hiện đại đều tích hợp sẵn File Manager trên trình duyệt. Bạn có thể tải lên (upload), tải xuống, giải nén, chỉnh sửa mã nguồn (code) và phân quyền truy cập tập tin ngay trên giao diện web. Giao thức FTP (File Transfer Protocol) cũng được quản lý chặt chẽ tại đây, cho phép tạo nhiều tài khoản FTP cho nhân viên với các quyền hạn khác nhau.</p>

<p><b>Quản lý Cơ sở dữ liệu (Database): </b>Website động (như WordPress, Joomla) không thể hoạt động thiếu cơ sở dữ liệu. Control Panel cung cấp công cụ để tạo mới, xóa hoặc sửa Database (thường là MySQL hoặc MariaDB). Công cụ phpMyAdmin thường được tích hợp sẵn để người dùng thao tác sâu hơn vào dữ liệu mà không cần biết các câu lệnh SQL phức tạp.</p>

<p><b>Quản lý Email Doanh nghiệp: </b>Với các doanh nghiệp, việc sở hữu email theo tên miền (ví dụ: lienhe@interdata.vn) là yếu tố bắt buộc để tạo sự chuyên nghiệp. Control Panel cho phép:
</p>
<p>Tạo/xóa tài khoản email.</p>
<p>Thay đổi mật khẩu.</p>
<p>Thiết lập chuyển tiếp email (Forwarder).</p>
<p>Cấu hình bộ lọc thư rác (Spam Filter) và trả lời tự động (Autoresponder).</p>
<p><b>Cài đặt ứng dụng tự động (Softaculous): </b>Đây là tính năng được nhóm người dùng mới (Newbie) ưa chuộng nhất. Thông qua các trình cài đặt tự động như Softaculous, bạn có thể cài đặt mã nguồn WordPress, Joomla, Drupal... chỉ với 1 cú click chuột. Hệ thống sẽ tự động tải mã nguồn, tạo database, kết nối chúng lại với nhau và bàn giao thông tin đăng nhập cho bạn trong vòng chưa đầy 1 phút.</p>

<p><b>Bảo mật và Sao lưu: </b>An toàn dữ liệu là ưu tiên hàng đầu. Control Panel cung cấp các công cụ:</p>
<p>Cài đặt SSL: Kích hoạt giao thức HTTPS giúp website bảo mật và tốt cho SEO.</p>
<p>Backup/Restore: Lên lịch sao lưu dữ liệu định kỳ và khôi phục lại khi website gặp sự cố.</p>
<p>IP Blocker: Chặn các địa chỉ IP độc hại hoặc spam.</p>

# Các loại Hosting Control panel
<p><b>Nhóm Control Panel Thương Mại: </b>Nhóm này thường được sử dụng trong các hệ thống doanh nghiệp lớn hoặc bởi các nhà cung cấp dịch vụ lưu trữ chuyên nghiệp nhờ tính ổn định và hệ sinh thái hỗ trợ mạnh mẽ.</p>
<p>cPanel & WHM</p>
<p>DirectAdmin (DA)</p>
<p>Plesk</p>

<p><b>Nhóm Control Panel Miễn Phí</b></p>
<p>Đây là những lựa chọn tuyệt vời để tiết kiệm chi phí, triển khai các môi trường thử nghiệm (lab), hoặc xây dựng các hệ thống đòi hỏi sự linh hoạt, cá nhân hóa cao.</p>
<p>CyberPanel</p>
<p>aaPanel</p>
<p>CloudPanel</p>
<p>HestiaCP / VestaCP</p>

## Tìm hiểu về DirectAdmin
### Cài đặt 
<p>Thiết lập Hostname</p>
<img width="563" height="53" alt="image" src="https://github.com/user-attachments/assets/3fbd9bc9-899e-45e9-9b66-02cbf7871e48" />
<p>Sửa file /etc/hosts </p>
<img width="797" height="205" alt="image" src="https://github.com/user-attachments/assets/0d619b1f-82e6-4cf1-9a0b-5ffbf3621c08" />
<img width="990" height="659" alt="image" src="https://github.com/user-attachments/assets/2677fc2d-6225-4299-a16b-633a2dc1de6f" />
<img width="1140" height="924" alt="image" src="https://github.com/user-attachments/assets/7f95a8ce-f4c6-4f33-8cfa-f60f51d8f471" />

<p>Tạo tên miền</p>
<img width="889" height="503" alt="image" src="https://github.com/user-attachments/assets/91afdf04-6342-4b3a-81d4-13125f8bfafb" />
<p>Upload file</p>
<img width="1473" height="686" alt="image" src="https://github.com/user-attachments/assets/5ea5de8c-30d6-4ff5-8382-f9d55f9efdd0" />

<img width="1916" height="997" alt="image" src="https://github.com/user-attachments/assets/eefa1111-d029-43bf-a85f-a557c53f9df1" />

### Backup Restore
<p>Chọn mục Backup/Restore Backups</p>
<img width="1245" height="888" alt="image" src="https://github.com/user-attachments/assets/fead7204-e177-43cc-9ef9-a8de4adc24b5" />

<p>Create backups</p>
<img width="1082" height="841" alt="image" src="https://github.com/user-attachments/assets/2167e2a3-17cd-4e87-bb2d-078e8b9ca335" />
<img width="755" height="258" alt="image" src="https://github.com/user-attachments/assets/d21d371b-0399-4d3b-bb00-c0c5b68ec0e6" />
<img width="1594" height="437" alt="image" src="https://github.com/user-attachments/assets/0496d541-6b5b-481a-9997-3569ff24a12d" />

<p>Restore</p>
<img width="775" height="169" alt="image" src="https://github.com/user-attachments/assets/4b81c63c-7b07-4114-87bd-c5e4b7879c6d" />
<img width="1187" height="733" alt="image" src="https://github.com/user-attachments/assets/fa52dddb-f2c2-419a-936a-6225af109445" />
<img width="985" height="390" alt="image" src="https://github.com/user-attachments/assets/f1e184ef-c4c2-4b74-8afd-1c2f6c19db35" />

### SSL
<p>SSL Certificate</p>
<img width="793" height="308" alt="image" src="https://github.com/user-attachments/assets/9a674603-9726-4351-a87a-ca3f91826e5b" />
<img width="1196" height="815" alt="image" src="https://github.com/user-attachments/assets/33046ccc-8a12-47da-af9c-6ef488ec2449" />
<img width="1016" height="392" alt="image" src="https://github.com/user-attachments/assets/dfe8e6f5-76eb-4165-8e66-831e3f5d7145" />
<img width="1180" height="732" alt="image" src="https://github.com/user-attachments/assets/a448d0ad-e559-4c43-9559-8903a672c618" />
<img width="1920" height="955" alt="image" src="https://github.com/user-attachments/assets/dd04b5c8-2b91-438b-b83f-a1610e3cc1e2" />

## Tìm hiểu về Plesk
### Cài đặt
<img width="1224" height="65" alt="image" src="https://github.com/user-attachments/assets/7ff4af6a-2f01-4f39-9fc6-627d93c7605e" />
<img width="1027" height="520" alt="image" src="https://github.com/user-attachments/assets/c6673cdf-506e-4cea-98a1-548cb915ca7c" />
<img width="1677" height="952" alt="image" src="https://github.com/user-attachments/assets/be97413a-a352-4fbe-8ced-bd5d632890b8" />
<img width="864" height="902" alt="image" src="https://github.com/user-attachments/assets/f08a37f3-9bb0-4335-a18a-a1b1a195d29f" />

<img width="709" height="798" alt="image" src="https://github.com/user-attachments/assets/a89567bc-a0b7-4034-b9a7-ecc9c65562ba" />
<img width="1659" height="925" alt="image" src="https://github.com/user-attachments/assets/bc045a47-fcb6-409f-9bb1-6b0d0d9eea91" />
<img width="1915" height="722" alt="image" src="https://github.com/user-attachments/assets/42812cdf-83c2-4e6d-ad05-73cab8727f5f" />

<img width="1664" height="684" alt="image" src="https://github.com/user-attachments/assets/e3c1b3be-7dbd-4d59-95f5-754f3f673b29" />
<img width="1732" height="803" alt="image" src="https://github.com/user-attachments/assets/50d29dde-2dc5-4972-b548-f04bd68ced5b" />
<img width="1491" height="884" alt="image" src="https://github.com/user-attachments/assets/9f61b3a4-7d77-40c2-ba38-d6d1a303b0f1" />
<img width="907" height="922" alt="image" src="https://github.com/user-attachments/assets/f88b0b9c-ea03-446f-aa56-4496e6c80db1" />
<img width="1507" height="589" alt="image" src="https://github.com/user-attachments/assets/80f6623b-54ea-412e-8bf6-e3549ddca4be" />

<p><b>Restore/Backup</b></p>
<img width="1635" height="492" alt="image" src="https://github.com/user-attachments/assets/8fea8547-1917-45a4-baa8-186c35589ec2" />
<img width="1536" height="904" alt="image" src="https://github.com/user-attachments/assets/f961181b-144b-4a5f-bd6a-33855c7fde3f" />
<img width="1467" height="456" alt="image" src="https://github.com/user-attachments/assets/3f72297e-6d96-4d07-9cd8-62a45839ea47" />
<img width="1707" height="945" alt="image" src="https://github.com/user-attachments/assets/c18e03ee-ff77-4145-8a3f-443af736c3ca" />
<img width="1453" height="364" alt="image" src="https://github.com/user-attachments/assets/131dc7d9-6a22-45cd-879b-5898657a60ea" />

## Tìm hiểu về cPanel
### Cài đặt
<p>Cài tên hostname</p>
<img width="688" height="57" alt="image" src="https://github.com/user-attachments/assets/1d922d13-bc65-4779-9307-ed7d4eea9ffa" />
<img width="941" height="77" alt="image" src="https://github.com/user-attachments/assets/86557c44-856a-4e47-b32d-d7ff39f73bf2" />
<img width="1920" height="496" alt="image" src="https://github.com/user-attachments/assets/afb03153-e617-4706-ba68-a35075dee8ef" />
<img width="1375" height="494" alt="image" src="https://github.com/user-attachments/assets/1fa9b7c7-6702-45aa-ada2-4b98d43d40fd" />
<img width="1535" height="661" alt="image" src="https://github.com/user-attachments/assets/b5c4b4e8-0da5-45ed-9656-f4c657813ef9" />
<img width="728" height="747" alt="image" src="https://github.com/user-attachments/assets/7136960f-3722-4cc7-84f6-82ba2557e26b" />
<img width="1916" height="667" alt="image" src="https://github.com/user-attachments/assets/c1347496-6e4a-455f-b3d3-b7ce8d78d1d7" />
<img width="692" height="555" alt="image" src="https://github.com/user-attachments/assets/9f466c8f-ced4-43be-8448-ef39780a7622" />
<img width="1151" height="930" alt="image" src="https://github.com/user-attachments/assets/c3066303-9482-4c92-ad5a-16fd73581280" />
<img width="1834" height="699" alt="image" src="https://github.com/user-attachments/assets/1572ccc5-afd1-4081-908c-dcdbd2bbfea9" />

<p>Cài đặt web</p>
<p>Tạo domain hoaquangthang.com</p>
<img width="1086" height="695" alt="image" src="https://github.com/user-attachments/assets/d3f3c330-3c86-45a9-a9a1-d2a1328ba869" />
<img width="1014" height="384" alt="image" src="https://github.com/user-attachments/assets/bed14030-080f-4468-aa79-40909b812f26" />
<p>Đăng nhập user người dùng vào ip 103.124.93.233:2083</p>
<img width="1916" height="667" alt="image" src="https://github.com/user-attachments/assets/a998c0da-bff6-44cd-b716-b39ba4bd6511" />
<p>Truy cập file manager quản lý file web</p>
<img width="1920" height="502" alt="image" src="https://github.com/user-attachments/assets/21ac6ed1-6c80-41fb-85d9-8f0ac5186e48" />
<img width="1516" height="582" alt="image" src="https://github.com/user-attachments/assets/f3d5d886-09d4-4a57-918a-028efa95878e" />

<p>Tạo database mới</p>
<img width="1537" height="546" alt="image" src="https://github.com/user-attachments/assets/793ff79b-22cf-47ed-9ba5-f666b2f87f16" />

<img width="1041" height="653" alt="image" src="https://github.com/user-attachments/assets/d712cf2e-fdcc-47f2-8e86-0a83318996c4" />
<img width="1610" height="824" alt="image" src="https://github.com/user-attachments/assets/d1dadbd4-daea-4c24-abde-0d1427bf7b08" />
<img width="1469" height="542" alt="image" src="https://github.com/user-attachments/assets/aab80455-8b9e-4de4-8c90-16f1a1e2a8d2" />
<img width="1920" height="996" alt="image" src="https://github.com/user-attachments/assets/ded18a41-2228-407a-b41f-12bc0a136289" />
<p>Cấu hình SSL</p>
<img width="1172" height="250" alt="image" src="https://github.com/user-attachments/assets/88bf27c7-ffc5-4c47-8dfc-061efd2972f0" />

<img width="758" height="878" alt="image" src="https://github.com/user-attachments/assets/12e10e43-d331-4800-82ae-7af53107f1c2" />
<p>Generate new key</p>
<img width="1465" height="802" alt="image" src="https://github.com/user-attachments/assets/34e45bf0-76e8-4da7-a5b0-be569470f5db" />
<img width="1906" height="988" alt="image" src="https://github.com/user-attachments/assets/7968eaa0-a31e-4b54-91b3-a545c1d3d243" />

## Backup and restore
<img width="1448" height="739" alt="image" src="https://github.com/user-attachments/assets/c0ff5415-4e28-4045-bf0a-fe1103664fff" />
<p>Cài đặt full backup</p>
<img width="884" height="520" alt="image" src="https://github.com/user-attachments/assets/d721fd69-0cb6-4cd1-a0c5-cd76041db816" />
<img width="991" height="730" alt="image" src="https://github.com/user-attachments/assets/c05b4ad0-a874-423b-bf2c-bb99ce3e0b17" />
<img width="1649" height="645" alt="image" src="https://github.com/user-attachments/assets/8acfd658-8fe7-4339-90bf-b5a522a11e1b" />
<img width="1618" height="737" alt="image" src="https://github.com/user-attachments/assets/2a4ef0b4-ce91-442a-8f63-9916a78ee13f" />
<img width="1503" height="310" alt="image" src="https://github.com/user-attachments/assets/1f83bd82-1044-4514-a7a6-80156b641eec" />
<p><b>Giao diện và trải nghiệm sử dụng</b></p>
cPanel từ lâu đã trở thành tiêu chuẩn ngành với giao diện quen thuộc, trực quan và được đại đa số người dùng hosting biết đến. Tuy nhiên, sự quen thuộc đó đổi lại bằng một giao diện khá cũ kỹ, nhiều tính năng hiển thị cùng lúc gây rối mắt. Plesk ngược lại có thiết kế hiện đại, gọn gàng và thân thiện hơn, hỗ trợ tốt cả trên desktop lẫn mobile. DirectAdmin có giao diện đơn giản nhất trong ba, thiếu tính thẩm mỹ nhưng nhẹ và nhanh, phù hợp với người dùng kỹ thuật không cần quá nhiều trực quan hóa.

<p><b>Hỗ trợ hệ điều hành</b></p>
Đây là điểm phân biệt rõ ràng nhất. cPanel chỉ chạy trên Linux (CentOS, AlmaLinux, CloudLinux, Ubuntu). DirectAdmin cũng chỉ hỗ trợ Linux. Trong khi đó, Plesk là lựa chọn duy nhất trong ba nền tảng hỗ trợ cả Linux lẫn Windows Server, điều này khiến Plesk trở thành lựa chọn bắt buộc nếu bạn cần chạy ứng dụng ASP.NET hoặc môi trường Windows.

<p><b>Chi phí bản quyền</b></p>
DirectAdmin có mức giá thấp nhất, thường chỉ từ vài đô mỗi tháng với license không giới hạn tài khoản, phù hợp cho nhà cung cấp hosting nhỏ muốn tiết kiệm chi phí. Plesk có nhiều gói linh hoạt theo số lượng domain, giá ở mức trung bình, phù hợp cả cá nhân lẫn doanh nghiệp. cPanel đắt nhất trong ba và từng gây tranh cãi khi thay đổi chính sách giá vào năm 2019, chuyển sang tính phí theo số lượng tài khoản — điều này khiến nhiều nhà cung cấp hosting quy mô lớn tốn thêm đáng kể chi phí vận hành.

<p><b>Tính năng và hệ sinh thái</b></p>
cPanel có hệ sinh thái lâu đời nhất với rất nhiều plugin, tích hợp bên thứ ba và tài liệu hướng dẫn phong phú. Đây là lý do cPanel vẫn chiếm thị phần lớn dù đắt hơn. Plesk nổi bật với tích hợp sẵn Docker, Git, WordPress Toolkit và hỗ trợ Node.js, Python, Ruby tốt hơn — phù hợp với developer hiện đại. DirectAdmin tuy đơn giản hơn về tính năng nhưng đủ dùng cho các nhu cầu hosting cơ bản đến trung cấp, và ngày càng được cải thiện qua các bản cập nhật gần đây.

<p><b>Hiệu năng và tài nguyên hệ thống</b></p>
DirectAdmin tiêu thụ ít tài nguyên nhất, khởi động nhanh và hoạt động ổn định ngay cả trên máy chủ cấu hình thấp. cPanel và Plesk nặng hơn do có nhiều dịch vụ chạy ngầm hơn, đòi hỏi RAM và CPU cao hơn để vận hành trơn tru.
