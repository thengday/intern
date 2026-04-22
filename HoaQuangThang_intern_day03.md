# NFS
## Tìm hiểu và cài đặt dịch vụ NFS Server
<p>NFS là một giao thức hệ thống tệp phân tán cho phép một máy tính (Client) truy cập các tệp tin qua mạng chia sẻ từ một máy tính khác (Server) giống hệt như cách nó truy cập vào ổ cứng cục bộ của chính nó.</p>
<p>NFS hoạt động theo theo mô hình Client - Server. NFS Server: Lưu trữ dữ liệu thực tế. Nó sẽ "xuất" (export) một hoặc nhiều thư mục để các máy khác có thể truy cập vào. NFS Client: Sẽ mount thư mục đã được chia sẻ từ Server vào một thư mục trống trên máy của mình và sử dụng</p>
<p><b>Cài đặt NFS Server</b></p>
<p>Cài đặt gói</p><img width="721" height="157" alt="image" src="https://github.com/user-attachments/assets/b8c23e6a-0f64-4f2f-b07f-c3e57a5a7aac" />

## Kết nối nfs client với nfs server
<p>Tạo thư mục chia sẻ trên server và phân quyền</p><img width="578" height="71" alt="image" src="https://github.com/user-attachments/assets/a7aec2ca-9f9f-4041-90fc-941acdac07f7" />
<p>Cấu hình chia sẻ file trong /etc/exports</p><img width="756" height="246" alt="image" src="https://github.com/user-attachments/assets/0d138017-16ef-489e-9095-90e5f138067c" />
<img width="787" height="224" alt="image" src="https://github.com/user-attachments/assets/c5ca8986-da96-4b27-a6fe-c2a0e2e2fb7b" />
<p>Trên máy client cài đặt gói</p><img width="701" height="198" alt="image" src="https://github.com/user-attachments/assets/6d5c2c8c-dc63-4148-bb9a-6c9a5b91363d" />
<p>Tạo file trên client và mount tới địa chỉ server file</p>
<img width="701" height="198" alt="image" src="https://github.com/user-attachments/assets/00fd3dbf-0ed9-4875-96f7-009efac05c5c" />
<p>Kiểm tra tạo file từ máy client vào thư mục chung</p>
<img width="702" height="136" alt="image" src="https://github.com/user-attachments/assets/1a7a64a8-8a42-4dda-88cc-789ffcbd9c22" />
<p>Trên máy server cũng nhận được file TEST.txt</p>
<img width="790" height="98" alt="image" src="https://github.com/user-attachments/assets/fdb1fd5c-299a-4ac8-8e07-67098e505b07" />

# LVM
## Tạo physical volume.
<p>Tạo ổ cứng mới</p>
<img width="710" height="685" alt="image" src="https://github.com/user-attachments/assets/7124f998-9968-4158-8463-66c9d7a4c32d" />
<img width="345" height="338" alt="image" src="https://github.com/user-attachments/assets/8d6a4adb-3d22-4f73-9679-b5cd55d024c0" />
<img width="756" height="227" alt="image" src="https://github.com/user-attachments/assets/0e479652-1b1e-4cce-862d-776ed4752676" />
<img width="763" height="352" alt="image" src="https://github.com/user-attachments/assets/64d762a2-3c3b-4ac1-84c3-743386acb390" />

## Tạo Volume Group
<p>Gộp chung ổ mới tạo vào hệ điều hành</p>
<img width="754" height="433" alt="image" src="https://github.com/user-attachments/assets/27f3d37c-da1d-4454-b427-c084ce49595f" />

## Tạo logical volume.
<p>Sử dụng lênh lvcreate -n logicalvo_dât -L 5G ubuntu-vg</p>
<img width="758" height="424" alt="image" src="https://github.com/user-attachments/assets/13ca13dd-3e5f-485a-8504-25496dd0a5fd" />

## Tạo filesystem trên logical volume.
<p>Tạo filesystem dưới định dạng ext4</p>
<img width="758" height="236" alt="image" src="https://github.com/user-attachments/assets/1bb36181-0b0a-4f38-96f8-eedceff06203" />
<p>Gắn logicalvolume vào file mới tạo trên ubuntu</p>
<img width="760" height="212" alt="image" src="https://github.com/user-attachments/assets/c35afc06-c156-4849-a6bd-041cc120a45e" />

## Chỉnh sửa fstab để tự động mount phân vùng.
<p>Thêm phân vùng đã tạo vào trong file /etc/fstab dùng để các phân vùng mới tự mount khi khởi động máy</p>
<img width="770" height="254" alt="image" src="https://github.com/user-attachments/assets/1932bc8c-462f-4712-bb0b-611f271b7f5e" />
<img width="802" height="263" alt="image" src="https://github.com/user-attachments/assets/ad7c37a3-9940-4a36-8bc8-ec17d52ebaa5" />

## Mở rộng logical volume
<p>Sử dụng lệnh lvextend để mở rộng logical volume sau đó dùng lệnh resize2fs để định dạng lại ext4 trên logical volume để cập nhật lại bộ nhớ</p><img width="786" height="569" alt="image" src="https://github.com/user-attachments/assets/f86c48c4-af92-444f-b90f-47aedbc503dd" />

## Thêm ổ cứng mở rộng logical volume 
<p>Tạo ổ cứng mới </p>
<img width="325" height="425" alt="image" src="https://github.com/user-attachments/assets/6a57b9b5-41f7-4030-9528-82d670734f3c" />
<p>Mở rộng volume group</p>
<img width="779" height="175" alt="image" src="https://github.com/user-attachments/assets/5f14eae4-4491-46de-bd1f-5c280b6f3cfa" />
<img width="755" height="345" alt="image" src="https://github.com/user-attachments/assets/09d02a4f-1b3b-4b51-8ee8-54279bec1f21" />

## Out/ thay thế 1 ổ cứng ra khỏi hệ thống LVM
<img width="762" height="313" alt="image" src="https://github.com/user-attachments/assets/7c4810fd-a120-4e64-9d96-c3c8715964c6" />


##Xóa logical volume, xóa volume group, xóa physical volume.
<p>Xóa logical volume umount /home/thang/mydata, xóa trong phần /etc/fstab</p>
<img width="755" height="550" alt="image" src="https://github.com/user-attachments/assets/91e1297b-0530-4e61-b108-50e04e92650f" />
<p>Xóa volume group</p>
<img width="766" height="237" alt="image" src="https://github.com/user-attachments/assets/ee545f92-c61c-4119-baf6-87c50711eb87" />
<p>Xóa physical volume</p>
<img width="787" height="111" alt="image" src="https://github.com/user-attachments/assets/e5c4e20f-d49d-4687-a353-5c60e4610433" />




