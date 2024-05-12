# GIỚI THIỆU CHUNG

Thiết kế xây dựng mạng LAN cho doanh nghiệp có nhiều tầng. Sử dụng dải địa chỉ 192.168.30.0/24 để chia cho toàn bộ hệ thống khoảng 230 máy tính sử dụng.


# NỘI DUNG CHÍNH

## 1. Kịch bản xây dựng

Thiết kế hệ thống mạng LAN cho một doanh nghiệp 7 tầng với 240 thiết bị, với các tầng lần lượt như sau (Số thiết bị sử dụng bao gồm cả PC, Laptop, Webcam,….):

- Tầng 1: Phòng Căn tin với tối đa 60 thiết bị.

- Tầng 2: Phòng Nhân sự với tối đa 30 thiết bị

- Tầng 3: Phòng Kế toán với tối đa 30 thiết bị.

- Tầng 4: Phòng Tài chính với tối đa 30 thiết bị.

- Tầng 5: Phòng Marketing với tối đa 30 thiết bị.

- Tầng 6: Phòng IT với tối đa 30 thiết bị.

- Tầng 7: Phòng Server với tối đa 30 thiết bị.

Số lượng thiết bị các phòng có thể tăng giảm đề phù hợp với các hoạt động của công ty nhưng không vượt quá số lượng tối đa. Mỗi tầng đều có một mạng không dây riêng với mật khẩu chung là _12345678_. Các phòng cũng sẽ có một Camera an ninh riêng được kết nối thông qua mạng không dây và có thể quản lí thông qua trang web. Ngoài ra trong tương lai, công ty có thể lắp đặt thêm các thiết bị thông minh khác cũng cần kết nối với mạng không dây và quản lí trên trang web này, ví dụ: Điều hoà, quạt thông minh, phát hiện cháy,…

Công ty có một trang web để khách hàng có thể truy cập và sử dụng dịch vụ của công ty, website này có tên miền là _ptit.edu.vn_. Ngoài ra cần một trang web quản lí nhân sự cho phòng nhân sự và ban lãnh đạo có tên miền là _manage.ptit.edu.vn._

##

## 2. Thiết kế hệ thống

Doanh nghiệp gồm có 7 tầng với mỗi tầng là một phòng ban khác nhau, mỗi phòng ban có số thiết bị khác nhau nên em sử dụng kĩ thuật chia mạng VLSM để chia cho từng phòng. Sau khi chia 192.168.30.0/24 thành các dải IP cho từng phòng, mỗi phòng sẽ sử dụng một VLAN riêng cụ thể như:

- Tầng 1: Phòng Căn tin với 60 thiết bị. Sử dụng dải địa chỉ 192.168.30.0/26

- Tầng 2: Phòng Nhân sự với 30 thiết bị. Sử dụng dải địa chỉ 192.168.30.128/27

- Tầng 3: Phòng Kế toán với 30 thiết bị. Sử dụng dải địa chỉ 192.168.30.64/27

- Tầng 4: Phòng Tài chính với 30 thiết bị. Sử dụng dải địa chỉ 192.168.30.192/27

- Tầng 5: Phòng Marketing với 30 thiết bị. Sử dụng dải địa chỉ 192.168.30.160/27

- Tầng 6: Phòng IT với 30 thiết bị. Sử dụng dải địa chỉ 192.168.30.96/27

- Tầng 7: Phòng Server với 30 thiết bị. Sử dụng dải địa chỉ 192.168.30.224/27

Sử dụng một Switch Layer 3 làm Core Switch cho cả toà nhà nối đến Switch riêng của mỗi tầng. Có thể nối trực tiếp các thiết bị đến Switch thông qua cổng FastEthernet hoặc thông qua kết nối không dây từ Access Point.

Ngoài việc kết nối trực tiếp vào switch, ở mỗi tầng sẽ sử dụng một Access Point để phát sóng WiFi. Điều này giúp cho các thiết bị như điện thoại, máy tính bảng, Laptop hay Webcam có thể dễ dàng kết nối vào mạng mà không cần sử dụng dây.

Do số lượng thiết bị mỗi phòng có thể tăng giảm nên cần sự linh hoạt trong việc gán địa chỉ IP cho các thiết bị. Vì vậy sử dụng một DHCP Server với mục đích cấp IP động cho từng tầng. Như vậy sẽ đảm bảo ngay khi thiết bị được kết nối với mạng thông qua Switch hoặc Access Point sẽ được cấp địa chỉ IP tự động. Hơn nữa do các tầng đều sử dụng VLAN nên sử dụng thêm một dịch vụ có tên VTP.

VTP viết tắt của từ _VLAN Trunking Protocol_ là giao thức độc quyền của Cisco hoạt động ở lớp 2 của mô hình OSI. VTP giúp cho việc cấu hình VLAN luôn đồng nhất khi thêm, xóa, sửa thông tin về VLAN trong một hệ thống mạng. Để chuyển yêu cầu lấy IP của các thiết bị đến DHCP server cần sử dụng "IP helper-address" . Và cuối cùng để định tuyến chỉ ần sử dụng câu lệnh "ip routing" trong Switch Layer 3.

Ở mỗi tầng sẽ có một webcam nên cần một IoT Server để có thể quản lí các thiết bị này dễ dàng hơn. Ngoài ra có thể mở rộng/thêm các thiết bị IoT khác như điều hoà, quạt, phát hiện cháy,… Việc truy cập vào trang quản lí sẽ thông qua trang web _iot.ptit.edu.vn._

Doanh nghiệp có một trang web nên cần một Web Server để host trang web này. Trang web này sẽ được gán domain là _ptit.edu.vn._

Giữa các nhân viên/phòng ban cần liên lạc với nhau thông qua email nên cần một Mail Server hỗ trợ việc này. Domain cho email sẽ là _ptit.edu.vn_

Cuối cùng, để gán domain cho các dịch vụ ở trên và để các thiết bị có thể truy cập vào các trang web này sẽ cần một DNS Server. Ngoài ra server này cũng host một trang web quản lí nhân viên với tên miền là _manage.ptit.edu.vn_. Do trang web này chỉ nội bộ nhân viên trong doanh nghiệp sử dụng nên không cần một server riêng.

## 3. Phương án lựa chọn thiết bị

Dưới đây là các thiết bị sử dụng và số lượng ước tính dựa trên thiết kế đã đề ra:

| **Tên thiết bị** | **Số lượng** | **Mục đích** |
| --- | --- | --- |
| PC - PT | ~ 200 | Máy tính của doanh nghiệp |
| Webcam | 7 | Camera an ninh |
| Server - PT | 6 | Sử dụng cho các dịch vụ: DHCP, Mail ,DNS, Web, IoT |
| AccessPoint PT-N | 6 | Phát tín hiệu mạng không dây |
| Switch 3560 24PS | 1 | Core Switch cho cả toà nhà |
| Switch 2950 - 24 | 7 | Switch riêng cho từng tầng |
| Laptop, Smartphone, Tablet | ~ 20 | Các thiết bị cá nhân của nhân viên công ty |

## 4. Thực hiện mô phỏng trên Cisco Packet Tracer

### 4.1. Lắp đặt các thiết bị

![image](https://user-images.githubusercontent.com/82562559/235387689-09fe7ddd-7436-43d8-9edd-4c40dfb3ea6b.png)

_Hình 1: Topo mạng tầng 6, 7_

![image](https://user-images.githubusercontent.com/82562559/235387708-46dff721-abd3-424b-9f59-b20d5b30a6ba.png)

_Hình 2: Topo mạng tầng 4, 5_

![image](https://user-images.githubusercontent.com/82562559/235387786-826f9824-69ac-4f38-abd5-0830214e3967.png)

_Hình 3: Topo mạng tầng 2, 3_

![image](https://user-images.githubusercontent.com/82562559/235387795-741b2445-36bb-43ee-8687-d1dfe7652fd0.png)

_Hình 4: Topo mạng tầng 1_

![image](https://user-images.githubusercontent.com/82562559/235387811-76bc229b-633d-43a0-b68a-80a2ba790fd2.png)

_Hình 5: Core Switch được nối với Main Switch của tất cả các tầng_

### 4.2. Cài đặt dịch vụ DHCP và định tuyến

- Trước hết cần cấu hình Core Switch: Tạo và đặt tên các VLAN

![image](https://user-images.githubusercontent.com/82562559/235387836-0d8a70e8-b564-4b6f-8ba5-b2e2b359d3c1.png)


- Cài đặt VTP cho Core Switch sang mode server và đổi domain thành _ptit.edu.vn_

![image](https://user-images.githubusercontent.com/82562559/235387852-0366d7c6-b0e9-45bd-a4dc-906077f3706f.png)


- Gán dải địa chỉ IP cho từng VLAN

![image](https://user-images.githubusercontent.com/82562559/235387862-1af8845b-ad32-4f13-ab68-ee80e18837c5.png)


- Chuyển các cổng kết nối của Core Switch sang mode trunk vì các cổng này được kết nối với các Switch khác

![image](https://user-images.githubusercontent.com/82562559/235387873-02c5317d-82ac-407c-a35b-d947bd15dd24.png)


- Tương tự với các Main Switch ở các tầng, config cổng kết nối với Core Switch thành mode trunk

![image](https://user-images.githubusercontent.com/82562559/235387887-85b5f72f-8594-4b29-8108-88da98a3e0eb.png)

- Sau đó chuyển tất cả các cổng còn lại của các Main Switch sang mode access và thêm VLAN tương ứng vào

![image](https://user-images.githubusercontent.com/82562559/235387901-d93ea1f4-01aa-4466-b6ba-06bca5e74e6d.png)

- Gán địa chỉ IP cho Server DHCP

![image](https://user-images.githubusercontent.com/82562559/235387917-89b5574d-7eaf-464a-8775-720634caf7e2.png)

- Chuyển sang tab Services, chọn DHCP sau đó bật dịch vụ và thêm các "pool" tương ứng với các VLAN theo bản thiết kế

![image](https://user-images.githubusercontent.com/82562559/235387926-d41756e0-0c5c-466e-8a31-62d2be3cd0b8.png)


- Thiết lập dịch vụ IP helper-address trong từng VLAN theo cú pháp

_ip helper-address \<ip của server DHCP\>_

![image](https://user-images.githubusercontent.com/82562559/235387938-32f883bb-d510-4419-a197-f8e9db5c949c.png)


- Thiết lập định tuyến cho mạng

![image](https://user-images.githubusercontent.com/82562559/235387949-a1dcc37c-06d0-44cb-90ad-a5f1955cab77.png)


Sau khi xong các bước này, các thiết bị đã có thể request để lấy IP, dưới đây là ảnh ví dụ một PC ở VLAN 60 – MARKETING

![image](https://user-images.githubusercontent.com/82562559/235387956-e17307f8-79a9-40fb-be9a-0580aca92dde.png)


Như vậy, các thiết bị đã có thể lấy IP đúng theo thiết kế đã đề ra, như ở ảnh trên PC đã lấy đúng dải IP của phòng Marketing (nằm trong dải 192.168.30.60 – 192.168.30.191).

Tiếp theo, thử ping giữa các PC ở cùng một tầng và khác tầng

- Ping 2 PC cùng ở tầng 6

![image](https://user-images.githubusercontent.com/82562559/235387970-69b0a8b8-6b00-47ce-9aff-c1ac348af75e.png)

- Từ một PC tầng 1 ping đến một PC khác ở tầng 4

![image](https://user-images.githubusercontent.com/82562559/235387982-ab00b22c-571c-4c2d-8efc-a9704a3f90ab.png)


Cả 2 trường hợp đều có tín hiệu reply từ PC được ping, như vậy định tuyến hoạt động rất tốt.

### 4.3. Cài đặt DNS server và Web Server

- Trước tiên, gán địa chỉ IP tĩnh cho cả 2 server. Với phần DNS của Server DNS để mặc định là 0.0.0.0, của web server để là IP của server DNS

![image](https://user-images.githubusercontent.com/82562559/235387993-12c2072e-386e-4a52-a925-17b307dbf1c2.png)


- Tiếp theo, ở server DNS chuyển sang tab Services và chọn DNS, sau đó thêm một bản ghi A với name là domain _ptit.edu.vn_ và Address là IP của Web server

![image](https://user-images.githubusercontent.com/82562559/235387999-1956c6a9-69c7-4d70-bc9f-5ca817cf8d90.png)


- Sau đó vào Web server và chọn tab Service -\> HTTP rồi bật cả HTTP và HTTPS. Có thể chỉnh sửa các file code để phù hợp với yêu cầu của doanh nghiệp.

![image](https://user-images.githubusercontent.com/82562559/235388012-656272e7-2fda-40a8-b3a2-6820d21171a3.png)


Sau khi config xong, có thể thử truy cập vào trang web thông qua Web Browser của PC bất kì theo tên miền _ptit.edu.vn_ hoặc IP của Web Server

![image](https://user-images.githubusercontent.com/82562559/235388036-b7fc6555-89dd-434b-b976-368864cc8c3e.png)


Như vậy, trang web đã có thể truy cập được từ tất cả các thiết bị. Nội dung của trang web có thể được thay đổi thông qua việc sửa đổi các file code trong web server.

- Tiếp theo, theo yêu cầu của doanh nghiệp cần một trang web để quản lí nhân viên, theo kế hoạch website này sẽ được host luôn trong DNS server. Vì vậy chỉ cần thêm một bản ghi A nữa với address chính là IP của DNS server với tên miền là _manage.ptit.edu.vn_

![image](https://user-images.githubusercontent.com/82562559/235388045-a21daaef-6745-419d-8f28-41515074b2de.png)


- Thử truy cập trang web này từ một PC bất kì

![image](https://user-images.githubusercontent.com/82562559/235388058-735da690-1a54-4d15-90e7-8fb9e7bebad1.png)


Như vậy, trang web đã hoạt động bình thường, phần code của server này đã được chỉnh sửa lại để có giao diện như trên.

### 4.4. Cấu hình server IoT

Do doanh nghiêp có sử dụng webcam và một số thiết bị IoT khác nên cần một server để quản lí cá thiết bị này. Dưới đây là các bước thực hiện:

- Gán địa chỉ IP cho server

![image](https://user-images.githubusercontent.com/82562559/235388081-b179ccb6-b3ae-4d99-9217-5b8f2c99a4de.png)


- Chuyển sang tab services chọn IoT và chuyển trạng thái sang on (khi mới bật sẽ không có bất cứ user nào, trong hình là user cũ tạo từ trước):

![image](https://user-images.githubusercontent.com/82562559/235388089-b35b9756-90cf-4486-b84c-eccb90e7148e.png)


- Tạo thêm một bản ghi A trong DNS server trỏ đến IP của IoT server với tên miền là _iot.ptit.edu.vn_

![image](https://user-images.githubusercontent.com/82562559/235388091-9f7cf15a-48fe-4cb8-9807-83ce94b4497a.png)


- Truy cập vào tên miền vừa thêm, trang đăng nhập hiện ra, ấn _Sign up now_ để tạo một user mới. Ở đây để cả username và password là "cisco".

![image](https://user-images.githubusercontent.com/82562559/235388102-fa0f8e23-fca1-4196-855c-1a6774010082.png)


- Sau khi đăng nhập, trang web sẽ chuyển đến phần quản lý các thiết bị IoT hiện đã kết nối, vì chưa kết nối bất cứ thiết bị nào nên danh sách sẽ trống. Tiếp tục thiết đặt một Access Point cho từng phòng để kết nối webcam qua tín hiệu không dây. Đầu tiên cần nối Access Point với Switch chính của tầng đó, sau đó thay đổi tên của mạng không dây ở phần "SSID" , chọn kiểu password là WP2A-PSK và điền vào phần PSK Pass Phrase là "12345678". Đây là mật khẩu mặc định đã ghĩ rõ trong bản thiết kế:

![image](https://user-images.githubusercontent.com/82562559/235388111-c99f25fb-917a-4690-8734-066d3883887e.png)


- Sau đó truy cập vào webcam, kết nối với mạng không dây thông qua phần Config-\> Wireless0. SSID là tên mạng không dây tương ứng của từng tầng, password mặc định là "12345678":

![image](https://user-images.githubusercontent.com/82562559/235388117-038316a2-f3ec-4cca-b609-8ebe8a5dc253.png)

- Tiếp tục chuyển sang tab Settings để add remote cho webcam. Ở phần IoT Server chọn Remote Server, với Server Address là địa chỉ IP của IoT Server, Username và password điền chính xác như đã tạo ở bước trước đó:

![image](https://user-images.githubusercontent.com/82562559/235388127-2dd5b992-3465-4c13-96da-c17f36428196.png)

- Sau khi thực hiện các bước tương tự trên webcam của từng tầng, truy cập lại trang web _iot.ptit.edu.vn_ để bật webcam, ấn vào nút hình chữ nhật màu đỏ để bật Webcam:

![image](https://user-images.githubusercontent.com/82562559/235388135-0092c5d0-5ca8-42ae-a64d-06f308c9773a.png)

Sau khi hoàn thành đủ các bước, có thể thấy các webcam đã hoạt động bình thường. Thông qua trang web này có thể bật tắt và xem các web cam, ngoài ra có thể điều khiển cả các thiết bị khác với các bước tương tự webcam.

### 4.5. Thiết lập dịch vụ email

- Gán IP cho server Email

![image](https://user-images.githubusercontent.com/82562559/235388144-6e25fdc4-a7b0-4509-b05b-fcd0d2c5cb58.png)

- Chuyển sang Services -\> Email, Domain Name là "ptit.edu.vn" sau đó thêm user để bằng cách điền vào "User" và " Password" sau đó ấn "+"

![image](https://user-images.githubusercontent.com/82562559/235388150-bec47fb9-156a-4d59-99d0-66b7748bf038.png)

- Tạo tài khoản và đăng nhập ở 2 PC với thông tin đã đăng kí ở bước trước. Phần Server Information điền IP của Mail Server

![image](https://user-images.githubusercontent.com/82562559/235388155-f49a273c-099b-4187-9654-f5bb2d0f6017.png)

- Thử gửi/ nhận email

![image](https://user-images.githubusercontent.com/82562559/235388163-ed32100d-aae0-4ba7-be94-28cc1d98ba64.png)

Như vậy PC kia đã nhận được email, hoàn thành thiết lập dịch vụ email cho công ty.
