# Nghiên cứu toàn bộ tính năng của WHM kết hợp với cloudlinux
## Cài đặt Direct admin kết hợp với cloudlinux
### Kiểm tra cài đặt LVE Manager để quản lý tài nguyên
<p>Xem lvemanager đã cài vào hệ thống</p>
<img width="524" height="56" alt="image" src="https://github.com/user-attachments/assets/55aaf83a-e8c0-4d6b-9d9d-9088bce88983" />
<p>Kiểm tra trạng thái lvemanager</p>
<img width="962" height="237" alt="image" src="https://github.com/user-attachments/assets/869942e6-bc68-4e83-9ab3-0791f256f061" />
<p>Kiểm tra trên phiên bản giao diện xuất hiện CPU Speed, RAM, IO Share, Entry Processes </p>
<img width="1619" height="448" alt="image" src="https://github.com/user-attachments/assets/3982b338-8cf6-4514-be8b-55e4c1dbc4b6" />

| Tham số | Ý nghĩa |
| :--- | :--- |
| **SPEED** | Giới hạn hiệu năng CPU được phép sử dụng. |
| **VMEM** | Giới hạn bộ nhớ ảo (Virtual Memory). |
| **PMEM** | Giới hạn bộ nhớ vật lý thực tế (RAM). |
| **IO** | Giới hạn tốc độ đọc/ghi dữ liệu của ổ cứng. |
| **IOPS** | Giới hạn số lượng thao tác đọc/ghi trên ổ cứng trong một giây. |
| **EP** | Giới hạn số lượng tiến trình kết nối đồng thời tại một thời điểm (Entry Processes). |
| **NPROC** | Tổng số lượng tiến trình tối đa được phép chạy cùng lúc. |
| **INODES** | Giới hạn tổng số lượng file và thư mục được lưu trữ trên hosting. |

<p>Kiểm tra cấu hình giới hạn bằng lệnh</p>
<img width="702" height="114" alt="image" src="https://github.com/user-attachments/assets/cccceb18-8a7a-4473-9214-4b43294fe0e9" />

<p>Dùng lvetop để xem trực tiếp các tiến trình bị giới hạn tài nguyên</p>
<img width="676" height="94" alt="image" src="https://github.com/user-attachments/assets/043b653b-2c0e-4fdc-b7d0-17c8a8094dd1" />

<p>Kiểm tra cài đặt CageFS là chức năng mỗi người dùng chỉ nhìn thấy thư mục và tệp của mình, không thể truy cập vào dữ liệu của người dùng khác hoặc hệ thống./p>
<p>Kiểm tra gói</p>
<img width="492" height="75" alt="image" src="https://github.com/user-attachments/assets/7fb82664-909f-4c84-939e-647b4b9f26de" />
<p>Xem trạng thái hoạt động của CageFS đang bật hay khởi tạo cấu hình xong hay chưa</p>
<img width="602" height="90" alt="image" src="https://github.com/user-attachments/assets/22265791-d2ba-454d-90aa-176b8aa23a98" />
<p>Xem danh sách user được enable</p>
<img width="595" height="123" alt="image" src="https://github.com/user-attachments/assets/f2672220-1436-4bba-84dd-0ad3cc312d83" />
<p>Kiểm tra trạng thái hoạt động của MySQL trên giao diện, đang ở trạng thái abusers</p>
<img width="1439" height="592" alt="image" src="https://github.com/user-attachments/assets/80b818d9-03e4-4104-a844-6c537eed4add" />
<p>Xem trạng thái hoạt động của db</p>
<img width="882" height="235" alt="image" src="https://github.com/user-attachments/assets/56fd5898-5adb-4c29-89e9-261849d43932" />

### Thử tạo account và gán giới hạn tài nguyên cho account
<img width="467" height="570" alt="image" src="https://github.com/user-attachments/assets/5b8ec77e-13fe-46b9-9e0e-934410036bb8" />
<p>Vào trang giao diện và chọn add new user</p>
<img width="1469" height="915" alt="image" src="https://github.com/user-attachments/assets/d19f923d-ff2f-4e5d-a99b-09790c5e2811" />
<p>Hiển thị tạo thêm gói giới hạn</p>
<img width="1524" height="903" alt="image" src="https://github.com/user-attachments/assets/d2665a31-fada-4606-bf5b-5b396d76478b" />
<img width="1502" height="854" alt="image" src="https://github.com/user-attachments/assets/88e44ed1-e3e0-4c2f-b8d0-3fab3ac2cf02" />
<p>Tiếp theo nhập form vào tạo user</p>
<img width="1617" height="713" alt="image" src="https://github.com/user-attachments/assets/62b4632d-a0bc-40e1-b32d-e58b396e9145" />
<img width="1503" height="666" alt="image" src="https://github.com/user-attachments/assets/54de6e17-8cb6-4b8b-980a-8fe790dba342" />
<img width="869" height="441" alt="image" src="https://github.com/user-attachments/assets/113d206f-9020-4949-b8b4-88ce33956265" />
<p>Kết quả</p>
<img width="1656" height="487" alt="image" src="https://github.com/user-attachments/assets/a81e0d08-b454-456c-8550-acc3a8c26fd4" />
<img width="640" height="115" alt="image" src="https://github.com/user-attachments/assets/82d9cdb4-5e1b-4c75-9de2-1e63350a077c" />

<p>Chạy thử dưới user quangthang để test tài nguyên và xem thông số trên hệ thống</p>
<img width="661" height="87" alt="image" src="https://github.com/user-attachments/assets/2b20ef41-da24-41bf-91a5-db9cef5ff721" />
<img width="903" height="251" alt="image" src="https://github.com/user-attachments/assets/28056bdf-a0ca-4f98-a6c1-ab90476f1c82" />

### Backup và Restore
<p>Chọn vào mục Schedule để tiến hành Backup</p>
<img width="1834" height="860" alt="image" src="https://github.com/user-attachments/assets/05c5a9f8-d1a9-455b-af14-8ada99bb3be9" />
<p>Chọn all user để backup toàn bộ user</p>
<img width="1602" height="703" alt="image" src="https://github.com/user-attachments/assets/653adac6-daf4-40c2-83e6-32bf4f17bee7" />
<img width="1555" height="597" alt="image" src="https://github.com/user-attachments/assets/81fd6f06-6a7d-4057-b8d1-be96f4d558e4" />
<img width="1502" height="600" alt="image" src="https://github.com/user-attachments/assets/48c7d4b0-bd70-4a90-b079-2a090318c358" />
<img width="1573" height="648" alt="image" src="https://github.com/user-attachments/assets/4751d934-1573-4742-a0c1-52d3f993abfb" />
<p>Kiểm tra trong file hệ thống của cloudlinux</p>
<img width="558" height="67" alt="image" src="https://github.com/user-attachments/assets/b03922e8-4ee2-4609-9313-8381cc5c939a" />


<p>Restore</p>
<img width="1744" height="703" alt="image" src="https://github.com/user-attachments/assets/a36e9d72-13c8-4f18-9278-67f2a2d314da" />
<img width="1754" height="735" alt="image" src="https://github.com/user-attachments/assets/4dcd3969-bbeb-48c7-8885-7f843f86efec" />
<img width="1749" height="858" alt="image" src="https://github.com/user-attachments/assets/c539f32f-780a-4d7a-8417-8ebd70d93fba" />

<p>Kiểm tra ssl của giao diện</p>
<img width="950" height="494" alt="image" src="https://github.com/user-attachments/assets/1a62348c-a04a-4ed4-a0e9-b3b8984aac65" />

<p>Kiểm tra ssl của https tới tên miền</p>
<img width="953" height="909" alt="image" src="https://github.com/user-attachments/assets/25c9bb38-6a81-49b6-b753-b8975abc55a0" />
<img width="964" height="759" alt="image" src="https://github.com/user-attachments/assets/91b5ac52-43d5-4f3b-8add-15fc5b146eea" />

<p>Kiểm tra tls bằng nmap</p>
<img width="958" height="733" alt="image" src="https://github.com/user-attachments/assets/a5578c42-a30e-45f1-badb-350c8721cd85" />

# Zabbix Server
## Cài đặt 
<p>Tải gói tài nguyên</p>
<img width="988" height="278" alt="image" src="https://github.com/user-attachments/assets/fa894ace-fbe9-4273-bbec-ee24d0097949" />
<img width="948" height="304" alt="image" src="https://github.com/user-attachments/assets/10570a40-5375-462d-9de4-033359999e23" />

<p>Cài đặt Zabbix server và web apache</p>
<img width="980" height="522" alt="image" src="https://github.com/user-attachments/assets/207039e4-9c30-4507-93b5-a35b16d970dc" />

<p>Cài đặt cơ sở dữ liệu</p>
<img width="843" height="164" alt="image" src="https://github.com/user-attachments/assets/785029ef-4266-4f58-9f85-949c86508051" />

<p>Tiến hành tạo cơ sở dữ liệu</p>
<img width="903" height="256" alt="image" src="https://github.com/user-attachments/assets/42d8af32-5fac-4a6f-a219-f500165fddd5" />
<img width="687" height="258" alt="image" src="https://github.com/user-attachments/assets/a2a934d9-012d-415f-86cf-aa7baca66fdf" />

<p>Nhập dữ liệu mẫu vào cơ sở dữ liệu</p>
<img width="976" height="68" alt="image" src="https://github.com/user-attachments/assets/59e5bb88-250d-4f70-a8c7-662d65f8d691" />

<p>Nhập mật khẩu vào file config csdl</p>
<img width="682" height="532" alt="image" src="https://github.com/user-attachments/assets/e9ff3d5e-e16a-49d3-8d16-2455b9e0768d" />

<p>Khởi động zabbix</p>
<img width="980" height="206" alt="image" src="https://github.com/user-attachments/assets/ce626a58-9b97-4a73-a817-d3d742c2b0dd" />
<p>Cài giao diện</p>
<img width="1296" height="798" alt="image" src="https://github.com/user-attachments/assets/8aad8853-a8ab-4b11-8a68-7d086e518d49" />
<img width="1487" height="747" alt="image" src="https://github.com/user-attachments/assets/9a33f8c0-7be9-4574-b44c-d0cc0fc903d7" />
<img width="1142" height="753" alt="image" src="https://github.com/user-attachments/assets/2ae75d6c-05fb-4acf-b319-c3bcb58e9860" />
<img width="1258" height="711" alt="image" src="https://github.com/user-attachments/assets/bb597f53-f30b-4211-bed7-9b7d2d6aa770" />
<img width="1125" height="639" alt="image" src="https://github.com/user-attachments/assets/5f642451-fea7-4cca-9a58-1c330a67dc65" />

<p>Đăng nhập vào zabbix</p>
<img width="1920" height="959" alt="image" src="https://github.com/user-attachments/assets/b0e5a331-4c2d-4818-8f93-3e9f5f2d8846" />

<p>Kết nối máy chạy direct admin vào hệ thống và lấy dữ liệu</p>
<img width="819" height="501" alt="image" src="https://github.com/user-attachments/assets/81614686-6ee1-4bf9-aa25-b30baf3fe39d" />
<img width="1229" height="687" alt="image" src="https://github.com/user-attachments/assets/2562d6b6-434f-44f3-a7aa-f168c91fea84" />
<img width="1736" height="113" alt="image" src="https://github.com/user-attachments/assets/d1e38d0b-b7f8-4691-86a2-7940745c78e7" />
<img width="1920" height="893" alt="image" src="https://github.com/user-attachments/assets/aa3ed975-cb6e-4550-ba30-b9166642ea30" />

# Check MK
<p>Cài đặt</p>
<p>Tải và cài gói</p>
<img width="993" height="203" alt="image" src="https://github.com/user-attachments/assets/49118419-9709-43a0-b2df-64e3dc8f8db2" />
<img width="916" height="301" alt="image" src="https://github.com/user-attachments/assets/2b8c91c6-b3f5-47ad-b1ff-f44e083667ad" />

<p>Tạo site để giám sát</p>
<img width="631" height="104" alt="image" src="https://github.com/user-attachments/assets/da6ba0b5-f362-4ba7-ad1b-b84569ea11ea" />
<img width="1071" height="348" alt="image" src="https://github.com/user-attachments/assets/a229181a-7d55-4a44-a033-a1eab6fe7acb" />

<p>Chạy site hiển thị giao diện đăng nhập</p>
<img width="1918" height="980" alt="image" src="https://github.com/user-attachments/assets/63f705fc-a1a0-492a-a0c9-e91b4b60bc7d" />
<img width="1911" height="873" alt="image" src="https://github.com/user-attachments/assets/c58d8107-7736-475b-a8ee-a4d6259709bf" />

<p>Add máy chạy DA vào host checkmk</p>
<img width="1917" height="594" alt="image" src="https://github.com/user-attachments/assets/a85e5f83-1caa-4893-b4c4-8f9825b02d56" />
<img width="1920" height="573" alt="image" src="https://github.com/user-attachments/assets/8ae3d3aa-05f7-49db-961a-78b983a973fc" />
<img width="1914" height="921" alt="image" src="https://github.com/user-attachments/assets/f0ee2c4d-5b98-47d4-8e5a-a22941d4b8ee" />
<img width="1856" height="564" alt="image" src="https://github.com/user-attachments/assets/c1f7ebe0-b482-4d7e-87ee-1c389df8b69d" />

<p>Kiểm tra các dịch vụ của máy host</p>
<img width="1920" height="898" alt="image" src="https://github.com/user-attachments/assets/f286f739-5d31-4260-9fb1-65b8ba68c467" />
