# DNS
## Tìm hiểu về hệ thống DNS
<p>DNS là viết tắt của Domain Name System hệ thống phân giải tên miền, phân giản tên miền thành địa chỉ IP tương ứng</p>
<p>Có 4 loại DNS <b>DNS Recursor, Root Name Server, TLD Name Server, Authoritative Name Server</b></p>
<p><b>DNS Recursor </b>đảm nhận việc đi tìm địa chỉ IP và trả về kết quả cho client, dùng các DNS Server, còn có cơ chế cache để tăng tốc độ phản hồi thay vì lúc nào cũng đi tìm IP, sau khi tìm được địa chỉ ip thì sẽ lưu vào cache trong một khoảng thời gian nhất định dựa vào TTL, ở lần truy cập sau thì sẽ lập tức trả về IP từ cache mà không cần thông qua DNS Server</p>
<p><b>Root Name Server </b>chứa một tệp dữ liệu Root Zone File lưu trữ thông tin đến các TLD Name Server như .com .net .vn .org </p>
<p><b>TLD Name Server (Top-Level Doamin Name Server) </b>duy trì danh sách thông tin về tất cả các tên miền thuộc quyền quản lý của nó, gồm 2 nhóm lớn <b>gTLD, ccTLD</b></p>
<p>gTLD Tên miền dùng chung quản lý các đuổi phổ biến mang tính quốc tế như .com .org .net .edu</p>
<p>ccTLD Tên miền quốc gia quản lý các đuôi dành riêng cho từng quốc gia hoặc vùng lãnh thổ như .vn .uk .jp</p>
<p><b>Authoritative Name Server </b>máy chủ tên miền có thẩm quốc, được cấu hình trực tiếp bởi chủ sở hữu tên miền để lưu trữ các bản ghi DNS thực tế</p>
<p>DNS gồm Public DNS và Local DNS. Public DNS là các máy chủ phân giải tên miền được vận hành bởi các nhà cung cấp dịch vụ Internet (ISP) hoặc các tổ chức bên thứ ba, mở cửa cho tất cả mọi người trên Internet sử dụng.</p>
<p>Local DNS là máy chủ DNS được triển khai và quản lý bên trong một mạng cục bộ (LAN), không cho phép truy cập từ Internet bên ngoài.</p>

## Các loại bản ghi trong DNS 
<p>Gồm có các bản ghi <b>SOA (Start of Authority), NS (Name Server), Record A, Record AAAA, Record PTR, Record SRV, Record CNAME (Canonical Name), Record MX, Record TXT, Record DKIM, Record SPF</b></p>
<p><b>DNS SOA </b>là bản ghi khởi đầu và bắt buộc trong mỗi tập tin cơ sở dữ liệu DNS. Bản ghi này chứa các thông tin quản trị quan trọng giúp hệ thống DNS vận hành chính xác và đồng bộ. Mỗi zone DNS chỉ được phép có duy nhất một bản ghi SOA, SOA cung cấp: </p>
<p>Master DNS: Địa chỉ máy chủ tên miền chính (Primary DNS Server) – nơi khởi nguồn và quản lý toàn bộ dữ liệu DNS của domain.</p>
<p>Email quản trị: Địa chỉ email của quản trị viên hệ thống, được ghi ở định dạng đặc biệt (ví dụ: admin.nhanhoa.com thay cho admin@nhanhoa.com).</p>
<p>Serial: Mã số phiên bản của zone – thường theo định dạng YYYYMMDDNN – để máy chủ Secondary biết khi nào cần cập nhật dữ liệu mới.</p>
<p>Refresh: Khoảng thời gian máy chủ Secondary cần kiểm tra dữ liệu từ máy chủ Primary để đồng bộ thông tin.</p>
<p>Retry: Nếu không thể kết nối với Primary, sau thời gian này máy chủ Secondary sẽ thử lại.</p>
<p>Expire: Nếu sau một thời gian dài không thể đồng bộ được, dữ liệu trên máy chủ Secondary sẽ bị xem là không hợp lệ.</p>
<p>TTL (Time to Live): Thời gian mà các máy chủ khác được phép lưu cache thông tin này trước khi phải truy vấn lại.</p>
<p><b>NS Record (Name Server)</b>là bản ghi DNS dùng để xác định máy chủ tên miền nào đang chịu trách nhiệm quản lý và phân giải thông tin của một domain cụ thể. Mỗi zone DNS sẽ có ít nhất một NS Record, chỉ rõ địa chỉ của các máy chủ DNS được ủy quyền. Nhờ đó, quá trình truy vấn tên miền được định tuyến chính xác đến hệ thống DNS phù hợp, đảm bảo website hoạt động ổn định.</p>
<p><b>Record A (Address Record) </b>là một trong những bản ghi quan trọng trong hệ thống DNS, dùng để ánh xạ tên miền thành địa chỉ IP dạng IPv4. Nhờ bản ghi này, người dùng có thể truy cập website bằng cách nhập tên miền thay vì phải ghi nhớ dãy số IP phức tạp</p>
<p><b>Record AAAA </b>là bản ghi DNS dùng để ánh xạ tên miền đến địa chỉ IP phiên bản IPv6, tương tự như Record A nhưng dành cho môi trường mạng hiện đại hơn. Với khả năng cung cấp hàng tỷ tỷ địa chỉ, IPv6 được phát triển nhằm thay thế IPv4</p>
<p><b>PTR Record (Pointer Record) </b>Trong hệ thống DNS thông thường, bản ghi A/AAAA thực hiện ánh xạ từ tên miền (hostname) → địa chỉ IP. Ngược lại, bản ghi PTR (Pointer Record) được sử dụng để thiết lập ánh xạ địa chỉ IP → tên miền, hay còn gọi là Reverse DNS Lookup.</p>
<p><b>SRV Record (Service Record) </b>SRV Record (Service Record) là bản ghi DNS được dùng để xác định vị trí chính xác của các dịch vụ cụ thể trong một tên miền, chẳng hạn như dịch vụ thoại, nhắn tin hoặc email. Bản ghi này cung cấp thông tin chi tiết về tên máy chủ, số cổng, giao thức sử dụng và các thông số ưu tiên giúp hệ thống định tuyến lưu lượng truy cập đến đúng máy chủ dịch vụ</p>
<p>Các trường quan trọng trong bản ghi SRV:</p>
<p>Tên dịch vụ: Xác định loại dịch vụ đang được sử dụng.</p>
<p>Giao thức: Chỉ rõ giao thức truyền dữ liệu như TCP hoặc UDP</p>
<p>Tên miền: Gắn liền với dịch vụ cần định vị.</p>
<p>TTL: Thời gian lưu bản ghi trong bộ nhớ cache.</p>
<p>Class: Luôn là IN (Internet)</p>
<p>Ưu tiên: Quyết định mức độ ưu tiên giữa các máy chủ, số nhỏ hơn được ưu tiên hơn</p>
<p>Trọng lượng: Dùng để cân bằng tải giữa các máy chủ có cùng mức ưu tiên.</p>
<p>Port: Số cổng mà dịch vụ hoạt động</p>
<p>Target: Tên miền đầy đủ (FQDN) của máy chủ cung cấp dịch vụ</p>

# Web Server
## Linux 
<p><b>Triển khai site wordpress trên LAMP stack</b></p>
<p>Cài đặt apache2 </p><img width="875" height="468" alt="image" src="https://github.com/user-attachments/assets/790de66b-9998-4322-b65c-4ffa35209128" />
<p>Cài đặt mysql</p><img width="786" height="186" alt="image" src="https://github.com/user-attachments/assets/e101a757-1664-4e93-8a07-051627ca87e3" />
<img width="756" height="518" alt="image" src="https://github.com/user-attachments/assets/94bdd7b8-2359-4860-9b11-efaa992aed63" />
<p>Tải mã nguồn WordPress</p><img width="782" height="120" alt="image" src="https://github.com/user-attachments/assets/d3c0e30c-4e75-4e67-ac18-ea2f8c48ea41" />
<img width="812" height="190" alt="image" src="https://github.com/user-attachments/assets/e4e7fff8-57a2-467d-9ac9-79276b390d66" />
<img width="783" height="339" alt="image" src="https://github.com/user-attachments/assets/1083ec2d-2ffa-4e05-8e4c-8b8c3f58db25" />
<p>Truy cập vào IP 10.130.10.132</p><img width="833" height="872" alt="image" src="https://github.com/user-attachments/assets/2ac7eaa9-a0ce-419e-bfa5-030aee269bd8" />
<img width="826" height="863" alt="image" src="https://github.com/user-attachments/assets/b12a6367-e803-4058-ab63-953269ea0b9e" />
<img width="1719" height="934" alt="image" src="https://github.com/user-attachments/assets/b520146a-4e14-41cd-9d30-b4ad97d02028" />
<p><b>Triển khai site wordpress LEMP stack</b></p>
<p>Cài đặt Nginx</p><img width="846" height="180" alt="image" src="https://github.com/user-attachments/assets/28f7eb98-74ac-45f2-9e0d-62a744689064" />
<img width="896" height="366" alt="image" src="https://github.com/user-attachments/assets/eac22303-356f-4489-a71e-23d178abbe24" />
<img width="774" height="417" alt="image" src="https://github.com/user-attachments/assets/3d2eed85-b219-4369-8cb6-178724d10d3c" />
<img width="772" height="193" alt="image" src="https://github.com/user-attachments/assets/0c479546-e1fa-4ee8-8063-47ac934f203b" />
<img width="1704" height="918" alt="image" src="https://github.com/user-attachments/assets/49842c8d-e1d5-4536-b6a9-b0c931a849dc" />
<p>Triển khai site wordpress tách web server, DB server (1 node web server, 1 node DB server)</p>
<p>Chinh bind-addresss = 0.0.0.0 trên máy db để lắng nghe mọi ip</p> <img width="1518" height="746" alt="image" src="https://github.com/user-attachments/assets/5aa0927a-0ef1-4f92-939f-4654bf8a1482" />
<img width="1190" height="364" alt="image" src="https://github.com/user-attachments/assets/f1922e05-6aab-4440-91eb-fd5926edc41a" />
<p>Trên máy server:</p>
<img width="766" height="107" alt="image" src="https://github.com/user-attachments/assets/d64a8533-3880-404f-9466-a402e97d538b" />
<img width="762" height="553" alt="image" src="https://github.com/user-attachments/assets/a1175b22-c5ac-408f-b427-817fe911ae3c" />
<p>Cấu hình nginx</p>
<img width="776" height="554" alt="image" src="https://github.com/user-attachments/assets/b21283a5-8d8c-4438-8853-16f548b6c0c6" />
<img width="1643" height="893" alt="image" src="https://github.com/user-attachments/assets/dcb78ed7-2018-497b-8d92-cfefb355833e" />
<img width="1655" height="916" alt="image" src="https://github.com/user-attachments/assets/4b9d6c9b-114f-4dc3-a4ab-016daeb218e0" />
<p><b>viết bash script LAMP, LEMP</b></p>
<img width="1920" height="966" alt="image" src="https://github.com/user-attachments/assets/8bb39a6f-c6ff-4bdf-8f24-e0d5fc9f4fc3" />
<img width="1920" height="979" alt="image" src="https://github.com/user-attachments/assets/96db28d2-e732-4aef-9e14-bcd048c32062" />
<img width="1920" height="987" alt="image" src="https://github.com/user-attachments/assets/f21d2c48-b33d-40fc-9557-ec309e168be7" />



