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

