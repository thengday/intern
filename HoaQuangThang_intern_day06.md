# Monitor Promethues + Grafana
## Cài đặt Promethues, Grafana trên Ubuntu 22.04
### Prometheus
<p>Tạo User và các thư mục cần thiết</p>
<img width="760" height="94" alt="image" src="https://github.com/user-attachments/assets/fa491169-6fcd-4fab-82f4-7e217274f569" />
<p>Tải và giải nén Prometheus</p>
<img width="801" height="606" alt="image" src="https://github.com/user-attachments/assets/1802e40c-d89d-4a13-b71a-bcf806f5a353" />
<p>Sao chép các file thực thi và phân quyền</p>
<img width="846" height="140" alt="image" src="https://github.com/user-attachments/assets/46d40767-5286-46e1-98c9-7bbd4e66ecde" />
<p>Sao chép file cấu hình và phân quyền</p>
<img width="847" height="106" alt="image" src="https://github.com/user-attachments/assets/f894edd2-4133-4d06-b841-112d4db5e211" />
<p>Tạo file Systemd Service cho Prometheus</p>
<p>Mở file sudo nano /etc/systemd/system/prometheus.service</p>
<img width="852" height="404" alt="image" src="https://github.com/user-attachments/assets/229c16a3-07f8-40af-8206-45d35ba6db9f" />
<p>Khởi động Prometheus
</p>
<img width="910" height="83" alt="image" src="https://github.com/user-attachments/assets/dfecc756-156e-45ab-8952-bd51cdc3df1a" />

<p>Máy chủ Promethues chạy trên cổng 9090 có URL là http://10.130.10.132:9090</p>
<img width="1919" height="568" alt="image" src="https://github.com/user-attachments/assets/cd43553b-b3a6-4fe1-8ae6-e1ea29c311cb" />

<p>Xác thực login Prometheus Server:</p>
<p>Cài đặt công cụ gen pass và tạo 1 tệp python.</p>
<img width="940" height="128" alt="image" src="https://github.com/user-attachments/assets/6462aa75-c057-49ef-ab70-057bb4ef12fc" />
<p>Thêm vào </p>
<img width="953" height="207" alt="image" src="https://github.com/user-attachments/assets/3abfd3c2-727b-494e-9f4d-4cc970d7c2bb" />
<img width="566" height="69" alt="image" src="https://github.com/user-attachments/assets/0bf7e6aa-e271-4e5e-ac98-3701f474a149" />
<p>Thêm pass đã hash vào file nano /etc/prometheus/web.yml</p>
<img width="894" height="128" alt="image" src="https://github.com/user-attachments/assets/fa651881-884e-4d36-bc9d-f60fc1b592f6" />

<p>Thêm --web.config.file=/etc/prometheus/web.yml \ vào file service /etc/systemd/system/prometheus.service</p>
<img width="865" height="292" alt="image" src="https://github.com/user-attachments/assets/f6b681ba-9204-4d21-a91e-bc5f0b1ec568" />

<img width="1841" height="303" alt="image" src="https://github.com/user-attachments/assets/41a38c25-ab94-4175-8d28-e64d3419bc0f" />

### Grafana
<p>Cài đặt các gói</p>
<img width="919" height="156" alt="image" src="https://github.com/user-attachments/assets/9057f593-b518-47b1-a8c6-4b1837e70f93" />

<p>Thêm GPG key của Grafana</p>
<img width="935" height="67" alt="image" src="https://github.com/user-attachments/assets/20bf97f1-6396-448f-b886-228278ca0b31" />

<p>Thêm kho lưu trữ Grafana</p>
<img width="929" height="63" alt="image" src="https://github.com/user-attachments/assets/0f0430a7-6ea4-49a4-a733-2a7a3debd961" />

<p>Cài đặt và khởi động Grafana</p>
<img width="912" height="103" alt="image" src="https://github.com/user-attachments/assets/674e700c-c405-4967-95d7-012514df262c" />
<img width="954" height="407" alt="image" src="https://github.com/user-attachments/assets/9e47bc66-ad6f-4e99-88a5-0ff2212e32ba" />
<p>Grafana server chạy trên URL http://10.130.10.132:3000</p>
<img width="1918" height="788" alt="image" src="https://github.com/user-attachments/assets/928ad653-ffe2-494e-af92-ed3e1dac630e" />

## Cấu trúc query promethues
<p>Lựa chọn các metrics theo nhãn và thời gian</p>
<p><b>Cú pháp: </b>metric_name{label_name="label_value"}</p>
<p>Bộ lọc nhãn và bộ lọc thời gian</p>
<p>Bộ lọc nhãn được đặt trong dấu ngoặc nhọn. Ví dụ http_requests_total{job="api-server", status="200"}</p>
<p>Bộ lọc thời gian được đặt trong dấu [] ở cuối. Ví dụ metric_name{...}[thời_gian]. http_requests_total{job="api-server"}[5m]</p>
<p>Các hàm</p>
<p>rate(): Đo tốc độ thay đổi của một metric trong một khoảng thời gian.
sum(): Tính tổng của các giá trị metrics.
avg(): Tính giá trị trung bình.</p>

## Monitor server linux
<p>Cài node exporter, tạo user, tải file và phân quyền</p>
<img width="934" height="492" alt="image" src="https://github.com/user-attachments/assets/e5963ba4-0755-40d9-8d40-7384b0b1f4a3" />
<p>Chỉnh sửa file trong service để chạy ngầm theo dõi thông số của server linux</p>
<img width="919" height="230" alt="image" src="https://github.com/user-attachments/assets/f393ea39-e2ce-4d1a-9a2f-16e3d1bbfe45" />

<p>Khởi động node Exporter</p>
<img width="919" height="93" alt="image" src="https://github.com/user-attachments/assets/c7981ba3-851c-44c9-a14c-cd0592cb577e" />
<p>Cấu hình file cấu hình prometheus sudo nano /etc/prometheus/prometheus.yml </p>
<img width="917" height="536" alt="image" src="https://github.com/user-attachments/assets/c8bd8aea-eec1-45ef-a898-4120d5854dfb" />
<p>sudo systemctl restart prometheus Khởi động lại prometheus</p>
<img width="1637" height="692" alt="image" src="https://github.com/user-attachments/assets/15881931-58ac-42f3-8ac6-a9709331b886" />
<p>Thêm prometheus vào data source của grafana</p>
<img width="1612" height="924" alt="image" src="https://github.com/user-attachments/assets/656cb4f6-c66a-440f-974c-c07ec27486c7" />
<p>import dashboard</p>
<img width="429" height="224" alt="image" src="https://github.com/user-attachments/assets/309b2db9-3b22-48dc-8e95-88bf95f05d92" />
<img width="733" height="714" alt="image" src="https://github.com/user-attachments/assets/48c258eb-2121-4e6e-b713-4aa40df18ea6" />
<img width="933" height="713" alt="image" src="https://github.com/user-attachments/assets/cddf4ded-7bb4-41bd-9d62-50babebc8ba1" />
<img width="1574" height="912" alt="image" src="https://github.com/user-attachments/assets/a07879cc-e72f-4e87-866b-0781075cb950" />

## Monitor mysql
<p>Đăng nhập vào mysql</p>
<img width="931" height="405" alt="image" src="https://github.com/user-attachments/assets/47755adf-f0ce-4a7d-a9d5-938415410b9b" />
<p>Tải và cài đặt mysqld_exporter</p>
<img width="941" height="524" alt="image" src="https://github.com/user-attachments/assets/c57a5382-6c77-4044-9053-04ba32cfcfad" />
<img width="929" height="131" alt="image" src="https://github.com/user-attachments/assets/fbf9c35f-19b8-49c5-8ceb-c445ac73ba02" />

<p>Cấu hình thông tin kết nối và tạo Service
</p>
<img width="942" height="161" alt="image" src="https://github.com/user-attachments/assets/caafb71b-adb6-4969-9d5c-b6a9a9f29f12" />

<p>Phân quyền</p>
<img width="822" height="46" alt="image" src="https://github.com/user-attachments/assets/7f2a4ba9-c703-4c38-a913-a9693209614f" />
<p>Tạo file chạy ngầm Systemd</p>
<p>sudo nano /etc/systemd/system/mysqld_exporter.service</p>
<img width="929" height="311" alt="image" src="https://github.com/user-attachments/assets/2616be96-c53d-45d9-a094-3a8160353a8d" />

<p>Khởi động dịch vụ</p>
<img width="939" height="369" alt="image" src="https://github.com/user-attachments/assets/04e10a2f-b081-42ce-9659-937f988a1fd8" />

<p>Cập nhật Prometheus và hiển thị lên Grafana</p>
<p>sudo nano /etc/prometheus/prometheus.yml</p>
<img width="910" height="674" alt="image" src="https://github.com/user-attachments/assets/c2e40af1-d1ac-4134-9992-d31692441380" />

<p>Nhập Dashboard vào Grafana</p>
<img width="887" height="689" alt="image" src="https://github.com/user-attachments/assets/984d482c-43df-4e24-ba87-af2416f3d952" />
<img width="1606" height="802" alt="image" src="https://github.com/user-attachments/assets/9c0e08c5-d1fa-44ce-ab68-6fdee2b1816a" />
<img width="1919" height="643" alt="image" src="https://github.com/user-attachments/assets/4f877770-1c05-4c12-bf35-b254322f22c4" />
<img width="1902" height="915" alt="image" src="https://github.com/user-attachments/assets/c8ad6933-0a19-46bd-99c2-debc7646948b" />

## Đưa biểu đồ lên kết hợp grafana (biểu đồ hiển thị RAM, CPU, Uptime, CPU Load, Mysql)
<p>Tạo dashboard </p>
<img width="1638" height="911" alt="image" src="https://github.com/user-attachments/assets/53c00143-bbc8-4f22-a069-e2322d80abd6" />
<p>Biểu đồ Uptime Server</p>
<img width="1622" height="887" alt="image" src="https://github.com/user-attachments/assets/d86385b8-f4bb-4b68-a9a5-f3934bea71f2" />
<p>Biểu đồ % CPU Usage</p>
<img width="1649" height="880" alt="image" src="https://github.com/user-attachments/assets/34742e66-f064-4f85-b138-36d3b66a2ac0" />
<p>CPU Load
</p>
<img width="1630" height="931" alt="image" src="https://github.com/user-attachments/assets/ec9a95d3-eb8b-4a38-9488-77128e8018d9" />
<p>% RAM Usage</p>
<img width="1618" height="914" alt="image" src="https://github.com/user-attachments/assets/5b6bfbf8-ba98-48b9-a958-49db0d213a0f" />
<p>MySQL Uptime</p>
<img width="1918" height="923" alt="image" src="https://github.com/user-attachments/assets/32d6b995-1d87-47eb-900d-62a52a962fff" />
<img width="1911" height="915" alt="image" src="https://github.com/user-attachments/assets/6b31db3b-ceda-4414-ba74-4db20410a094" />
