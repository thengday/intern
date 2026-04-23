# Triển khai ứng dụng mail server Zimbra
## Triển khai ứng dụng mail server Zimbra	Cài đặt email server zimbra trên Ubuntu 22.04
<p>Cấu hình /etc/hosts</p>
<img width="721" height="100" alt="image" src="https://github.com/user-attachments/assets/34dc3645-9647-4631-a989-342ca2e329a3" />
<img width="788" height="213" alt="image" src="https://github.com/user-attachments/assets/a8726842-5508-4506-b3ba-9b03254bec2e" />
<p>Tạo domain ảo</p>
<img width="694" height="86" alt="image" src="https://github.com/user-attachments/assets/06cb1b0f-304b-4018-9d73-c6fc00ee7ec6" />
<img width="810" height="568" alt="image" src="https://github.com/user-attachments/assets/ada5877e-4d97-4729-a2ca-25a77a81627b" />
<p>Tạo file để caifl zimbra</p>
<img width="776" height="86" alt="image" src="https://github.com/user-attachments/assets/a4b74fd2-84a9-4a44-82de-1b3b68dfd7b4" />
<p>Tải và giải nén file zimbra</p>
<img width="1013" height="627" alt="image" src="https://github.com/user-attachments/assets/67fefbd8-57cf-48f6-a6fe-23a7001de015" />
<img width="821" height="207" alt="image" src="https://github.com/user-attachments/assets/66bf5df4-61ae-4646-88c0-d74df3c52d7f" />
<p>Cài admin store password</p><img width="795" height="626" alt="image" src="https://github.com/user-attachments/assets/eb111481-7f50-49be-b089-bac14793b192" />
<img width="813" height="636" alt="image" src="https://github.com/user-attachments/assets/dda4eaba-fa9f-4966-a35d-9d6ad9972f51" />

## Khởi tạo user zimbra
<p>Sử dụng lệnh zmprove</p>
<img width="856" height="154" alt="image" src="https://github.com/user-attachments/assets/24e9ba4d-8959-4941-a2ed-7102a217d490" />
<img width="1399" height="188" alt="image" src="https://github.com/user-attachments/assets/11d96c99-1fbc-4295-bd75-ee8ee69f4b3c" />
<p>Đăng nhập thành công</p>
<img width="1646" height="676" alt="image" src="https://github.com/user-attachments/assets/0e53c8b1-ef75-475e-9dfd-fd6da313ba3c" />
## Thiết lập chính sách mật khẩu
<img width="1642" height="822" alt="image" src="https://github.com/user-attachments/assets/62f56d2a-5495-4e28-885b-aebd7392ff2f" />

## Thiết lập chữ ký email zimbra
<p>Thiết lập chữ ký cá nhân</p>
<p>Truy cập vào Preferences -> Signatures </p><img width="1658" height="758" alt="image" src="https://github.com/user-attachments/assets/8a221b4c-1839-4e1f-a9ea-6c7b6c218128" />

## Thiết lập forward email zimbra
<img width="1653" height="653" alt="image" src="https://github.com/user-attachments/assets/3802124d-2b8c-46cf-a503-76892687ceae" />

## Tìm ID mailbox account trong email zimbra
<p>Đăng nhập vào zimbra mail sử dụng lệnh zmprov gmi tên user</p>
<img width="967" height="135" alt="image" src="https://github.com/user-attachments/assets/ddfb0543-8288-4762-bde0-f19349bbbe0f" />

## Đổi mật khẩu account admin zimbra
<p>Sử dụng lênh zmprove sp admin@nhanhoa.local</p>
<img width="648" height="128" alt="image" src="https://github.com/user-attachments/assets/1271c12b-c739-450c-900b-3f7bb738bb0c" />

## Kiểm tra log gửi/nhận email zimbra (đặc biệt chú ý)
<p>Gửi mail</p>
<img width="1639" height="549" alt="image" src="https://github.com/user-attachments/assets/0a9af159-29d3-4ddc-a8fd-668e449053c6" />

<img width="835" height="583" alt="image" src="https://github.com/user-attachments/assets/ecba044e-1be4-4410-82ef-e608d600d466" />
## Thay đổi logo trong email zimbra
<p>Tao file logo mới </p>
<img width="867" height="458" alt="image" src="https://github.com/user-attachments/assets/3cf5d009-0e8c-49a9-8f0b-f3154323e981" />
<img width="848" height="108" alt="image" src="https://github.com/user-attachments/assets/ad78cc74-184d-458b-937a-02bddc54438a" />
<img width="1639" height="848" alt="image" src="https://github.com/user-attachments/assets/373d5d63-4a99-46be-b2a8-ed203a8b516f" />

## Thay đổi title web zimbra
<p>Sửa file /opt/zimbra/jetty/webapps/zimbra/WEB-INF/classes/messages/ZmMsg.properties</p>
<img width="839" height="65" alt="image" src="https://github.com/user-attachments/assets/9f05ecd1-486a-4276-9e7e-f77d2fe79946" />

<img width="890" height="30" alt="image" src="https://github.com/user-attachments/assets/993ba860-08aa-4979-b335-0bfc3fbb64c1" />
<img width="1646" height="97" alt="image" src="https://github.com/user-attachments/assets/577c68f1-2208-4d3d-9bd8-78ed1c64904a" />

<img width="1652" height="84" alt="image" src="https://github.com/user-attachments/assets/240b8abe-9c40-467f-b3eb-78b8d8d09e5e" />

## Chỉnh sửa quota account email zimbra
<img width="1638" height="650" alt="image" src="https://github.com/user-attachments/assets/190ec3cb-e9c4-4a94-8a99-4921f1de928f" />

## Backup/Restore
<p>Tạo script Backup</p>
<img width="834" height="704" alt="image" src="https://github.com/user-attachments/assets/028953c4-0b90-4b44-be57-b7fe648997d2" />
<img width="793" height="162" alt="image" src="https://github.com/user-attachments/assets/0c566211-4d16-4139-abaa-1fc52d6c2856" />
<p>Restore tạo script </p>
<img width="836" height="319" alt="image" src="https://github.com/user-attachments/assets/d5f714f3-62b7-4903-be47-09b6af166452" />
<img width="845" height="221" alt="image" src="https://github.com/user-attachments/assets/f026d968-4386-44dc-9deb-768426bd6fa5" />



