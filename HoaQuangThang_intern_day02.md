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
<p><b>NS Record (Name Server)</b>NS Record (Name Server) là bản ghi DNS dùng để xác định máy chủ tên miền nào đang chịu trách nhiệm quản lý và phân giải thông tin của một domain cụ thể. Mỗi zone DNS sẽ có ít nhất một NS Record, chỉ rõ địa chỉ của các máy chủ DNS được ủy quyền. Nhờ đó, quá trình truy vấn tên miền được định tuyến chính xác đến hệ thống DNS phù hợp, đảm bảo website hoạt động ổn định.</p>
<p><b>Record A (Address Record) </b>là một trong những bản ghi quan trọng trong hệ thống DNS, dùng để ánh xạ tên miền thành địa chỉ IP dạng IPv4. Nhờ bản ghi này, người dùng có thể truy cập website bằng cách nhập tên miền thay vì phải ghi nhớ dãy số IP phức tạp</p>
<p><b>Record AAAA </b>là bản ghi DNS dùng để ánh xạ tên miền đến địa chỉ IP phiên bản IPv6, tương tự như Record A nhưng dành cho môi trường mạng hiện đại hơn. Với khả năng cung cấp hàng tỷ tỷ địa chỉ, IPv6 được phát triển nhằm thay thế IPv4</p>
<p><b>PTR Record (Pointer Record) </b>Trong hệ thống DNS thông thường, bản ghi A/AAAA thực hiện ánh xạ từ tên miền (hostname) → địa chỉ IP. Ngược lại, bản ghi PTR (Pointer Record) được sử dụng để thiết lập ánh xạ địa chỉ IP → tên miền, hay còn gọi là Reverse DNS Lookup.</p>
<p><b>SRV Record (Service Record) </b>SRV Record (Service Record) là bản ghi DNS được dùng để xác định vị trí chính xác của các dịch vụ cụ thể trong một tên miền, chẳng hạn như dịch vụ thoại, nhắn tin hoặc email. Bản ghi này cung cấp thông tin chi tiết về tên máy chủ, số cổng, giao thức sử dụng và các thông số ưu tiên giúp hệ thống định tuyến lưu lượng truy cập đến đúng máy chủ dịch vụ</p>
<p>Các trường quan trọng trong bản ghi SRV:</p>
<p>Tên dịch vụ: Xác định loại dịch vụ đang được sử dụng.</p>
<p>Giao thức: Chỉ rõ giao thức truyền dữ liệu như TCP hoặc UDP</p>
<p>Tên miền: Gắn liền với dịch vụ cần định vị.</p>
<p>TTL: Thời gian lưu bản ghi trong bộ nhớ cache.</p>
<p> Class: Luôn là IN (Internet)</p>
<p>Ưu tiên: Quyết định mức độ ưu tiên giữa các máy chủ, số nhỏ hơn được ưu tiên hơn</p>
<p>Trọng lượng: Dùng để cân bằng tải giữa các máy chủ có cùng mức ưu tiên.</p>
<p>Port: Số cổng mà dịch vụ hoạt động</p>
<p>Target: Tên miền đầy đủ (FQDN) của máy chủ cung cấp dịch vụ</p>

# Web Server
