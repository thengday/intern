# Triển khai multi server trên zimbra
## Cài đặt, cấu hình
<img width="769" height="219" alt="image" src="https://github.com/user-attachments/assets/0b644b7f-2422-4e52-81d7-f7de673aee62" />

<img width="634" height="162" alt="image" src="https://github.com/user-attachments/assets/b1834b6a-e8ae-4567-bcbb-09bda47c9957" />
<p>set hostname trên máy ldap</p>
<img width="420" height="58" alt="image" src="https://github.com/user-attachments/assets/b392acfb-8d56-4932-8816-913f34d248db" />
<p>Cài rsyslog</p>
<img width="979" height="309" alt="image" src="https://github.com/user-attachments/assets/a95e1ce6-9e14-45ba-8488-7d8f271fd2cd" />


<p>Tải và cài đặt zimbra</p>
<img width="965" height="484" alt="image" src="https://github.com/user-attachments/assets/629b6876-4209-4da4-9db5-b7d43500ee95" />
<img width="670" height="29" alt="image" src="https://github.com/user-attachments/assets/21bef35d-0277-4ded-bf81-62a6e06fbd4f" />


<img width="915" height="470" alt="image" src="https://github.com/user-attachments/assets/1f7e2db2-1392-477b-ae3f-bdbff897bf05" />
<img width="666" height="249" alt="image" src="https://github.com/user-attachments/assets/e3ab2ff7-0bdb-4b9f-8113-2234f6525070" />
<img width="683" height="242" alt="image" src="https://github.com/user-attachments/assets/6671f324-5807-4019-b351-8fca65c18171" />
<img width="774" height="238" alt="image" src="https://github.com/user-attachments/assets/d0fd7b77-1327-4af6-a028-26720da9f060" />

<p>Cấu hình hostname & hosts cho máy mail2</p>
<img width="692" height="56" alt="image" src="https://github.com/user-attachments/assets/e7fac7e2-5680-4a16-a639-b1f8228c6fa9" />
<img width="639" height="159" alt="image" src="https://github.com/user-attachments/assets/c5d40375-d6bf-455b-baa5-ee592c27b54e" />

<p>Tải và cài đặt zimbra cho mail2</p>
<img width="953" height="501" alt="image" src="https://github.com/user-attachments/assets/b82fb70d-b5a3-4bb2-bbcb-5974e50d4a3a" />
<img width="819" height="76" alt="image" src="https://github.com/user-attachments/assets/a9efdb71-090e-4bdb-b4d9-7917fa2b749e" />
<img width="653" height="491" alt="image" src="https://github.com/user-attachments/assets/9997b10a-e7e0-495f-a27c-17ab7f88b0aa" />
<p>Cấu hình </p>
<img width="807" height="267" alt="image" src="https://github.com/user-attachments/assets/e827e2c5-c7cd-4958-9af1-d3beab2349c3" />

<img width="866" height="589" alt="image" src="https://github.com/user-attachments/assets/dc7ea851-544f-4d9a-8c45-d51e7170bab5" />
<img width="971" height="629" alt="image" src="https://github.com/user-attachments/assets/70ec63d3-1df1-4def-92d5-203a269a617b" />

<p><b>Mail1</b></p>
<p>Cấu hình hostname & hosts</p>
<img width="774" height="418" alt="image" src="https://github.com/user-attachments/assets/634cf4b8-b25d-4d7c-9624-9242e42a11fc" />
<p>Tải và cài đặt zimbra</p>
<img width="958" height="483" alt="image" src="https://github.com/user-attachments/assets/3cba5292-c617-4401-b025-9fd3200c05a9" />
<img width="649" height="337" alt="image" src="https://github.com/user-attachments/assets/f723d198-a253-4a5e-8ade-90f4e4773071" />
<img width="883" height="397" alt="image" src="https://github.com/user-attachments/assets/eb86072d-11b2-4fe2-abe0-ac3b63f45ba6" />
<p>Cấu hình </p>
<img width="699" height="271" alt="image" src="https://github.com/user-attachments/assets/a622d5df-cdda-4f60-af50-2e559ecf79bb" />
<img width="882" height="697" alt="image" src="https://github.com/user-attachments/assets/c3de28e0-98b6-4f6e-83dc-bb30dede6c77" />
<img width="692" height="225" alt="image" src="https://github.com/user-attachments/assets/c78bfa73-ae41-43b5-8505-e689dfa4492a" />


<p>Kiểm tra cài LDAP Master/Replica và đồng bộ.</p>
<p>Gồm 2 LDAP Master và Replica</p>
<p>LDAP Master có ip: 192.168.229.135</p>
<p>LDAP Replica có ip: 192.168.229.140</p>
<p>Kiểm tra cả 2 LDAP đang chạy</p>
<p>Trên LDAP Master</p>
<img width="513" height="125" alt="image" src="https://github.com/user-attachments/assets/0d5989cf-62e8-4902-9864-5a88532297dd" />
<p>Trên LDAP Replica</p>
<img width="526" height="159" alt="image" src="https://github.com/user-attachments/assets/177e9c54-eed1-4f37-879d-4286363b5441" />
<p> Kiểm tra MMR đã enable trên cả 2 node</p>
<p>Trên LDAP Master</p>
<img width="711" height="451" alt="image" src="https://github.com/user-attachments/assets/2da6477f-427f-439c-9fec-2e9ee1965237" />
<p>LDAP master đã trỏ về LDAP replica</p>
<p>Kiểm tra MMR đã enable trên cả 2 node</p>
<p>Trên LDAP Master</p>
<img width="706" height="461" alt="image" src="https://github.com/user-attachments/assets/0b472ef5-8e39-4509-9598-236122020a03" />
<p>Trên LDAP Replica</p>
<img width="723" height="441" alt="image" src="https://github.com/user-attachments/assets/97016891-c362-4164-8607-d5f30367fcfd" />
<p>Kiểm tra syncprov overlay trên LDAP Master</p>
<img width="541" height="379" alt="image" src="https://github.com/user-attachments/assets/ac09a460-f6ec-4bf0-804d-c1747ad2a504" />
<p>Module syncprov đã trỏ vào cơ sở dữ liệu của LDAP Replica</p>
<p>Đếm số entry trên 2 node LDAP</p>
<img width="440" height="151" alt="image" src="https://github.com/user-attachments/assets/0db72541-0f3e-4ce2-88ef-8bd987bb1fac" />
<img width="424" height="141" alt="image" src="https://github.com/user-attachments/assets/5858eb95-f0e8-4eb1-8306-1a6c7391e793" />
<p>Cả 2 node đều có 32 entry bằng nhau</p>
<p>Test Sync từ LDAP Master sang LDAP Replica</p>
<img width="527" height="74" alt="image" src="https://github.com/user-attachments/assets/c463bd41-c04b-4071-8021-345fbf603f5c" />
<img width="677" height="166" alt="image" src="https://github.com/user-attachments/assets/57d20f74-cc3c-4b2f-beef-59416b737c82" />

<p>Test Sync từ LDAP Replica sang Master</p>
<img width="520" height="53" alt="image" src="https://github.com/user-attachments/assets/55483af1-3f87-4579-aa7e-eb4c50b9b5d8" />
<img width="660" height="176" alt="image" src="https://github.com/user-attachments/assets/fb58011c-e487-4c57-9f6c-0f6aa7f1c44b" />

<p><b>Kiểm tra MTA hoạt động, relay đúng.</b></p>
<p>Gửi mail test bằng máy mail1 </p>
<img width="1019" height="44" alt="image" src="https://github.com/user-attachments/assets/9111d782-0c9b-43fe-917f-290aee267e72" />
<p>Sau khi gửi xong, check log zimbra.log để kiểm tra mta đã delivery chưa</p>
<img width="1091" height="81" alt="image" src="https://github.com/user-attachments/assets/51fda577-b30e-4127-abe5-aa5b57d48743" />
<p>Máy mta nhận 2 LDAP master và replica</p>
<img width="659" height="97" alt="image" src="https://github.com/user-attachments/assets/d5e5dce8-4ea6-4330-b222-414af4e270d6" />

<p><b>Kiểm tra Mailbox server tạo user và hoạt động.</b></p>
<p>Kiểm tra các dịch vụ trên máy Mailbox</p>
<img width="465" height="217" alt="image" src="https://github.com/user-attachments/assets/ed565156-7eba-4a6f-abec-c841bf5d1bb0" />
<p>Tạo 1 user ở mailbox</p>
<img width="726" height="66" alt="image" src="https://github.com/user-attachments/assets/0ded3f75-6e0d-4acd-99e2-14ed73a98e15" />
<p>Kiểm tra mailbox của user vừa tạo</p>
<img width="614" height="278" alt="image" src="https://github.com/user-attachments/assets/6b403f2c-20fc-4eea-b73f-529f244c70a4" />
<img width="477" height="81" alt="image" src="https://github.com/user-attachments/assets/2387c180-884b-40fe-ac1b-a5e635ff2cc3" />
<img width="614" height="278" alt="image" src="https://github.com/user-attachments/assets/7f6d43f5-44f4-45b2-a35d-4cd72ba0f838" />
<p><b>Kiểm tra Proxy điều hướng đúng đến mailbox.</b></p>
<p>Kiểm tra các cổng từ Mail1:MTA+Proxy đến mail2:Mailbox</p>
<img width="694" height="167" alt="image" src="https://github.com/user-attachments/assets/b766c40a-25be-485e-ab8c-f003c0ce4fc5" />
<img width="659" height="79" alt="image" src="https://github.com/user-attachments/assets/cc2bf050-7cde-41ad-ba27-88b5b119953a" />
<img width="736" height="68" alt="image" src="https://github.com/user-attachments/assets/f4f30ad3-e9d7-4c1e-9314-f96eb2786587" />

## Chức năng vận hành
<p><b>Gửi/nhận mail nội bộ và ra ngoài.</b></p>
<img width="1537" height="487" alt="image" src="https://github.com/user-attachments/assets/772819b0-b0d3-4de0-8f04-a5e23deb2249" />
<img width="1460" height="470" alt="image" src="https://github.com/user-attachments/assets/fde93171-0a09-4983-afd7-982eae05d744" />

<img width="1201" height="85" alt="image" src="https://github.com/user-attachments/assets/dec99531-54e3-4366-ae6f-c52faa6b1577" />
