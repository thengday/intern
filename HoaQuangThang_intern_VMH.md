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

