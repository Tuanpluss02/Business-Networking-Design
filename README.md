
HỌC VIỆN CÔNG NGHỆ BƯU CHÍNH VIỄN THÔNG

**KHOA VIỄN THÔNG 1**













**BÁO CÁO TIỂU LUẬN**

**MÔN HỌC: KĨ THUẬT MẠNG TRUYỀN THÔNG**

**NHÓM MÔN HỌC: 01**


**     

`                     `**Họ và tên : Đỗ Ngọc Tuân** 

`                     `**Mã sinh viên: B20DCVT330**  

`		  `**Số điện thoại: 0969527012**

`                     `**Giảng viên giảng dạy: Phạm Anh Thư**







**HÀ NỘI - 2023**

**MỤC LỤC**
#
[PHẦN 1: GIỚI THIỆU CHUNG	3****](#_toc133397788)**

[1. Đề tài tiểu luận	3](#_toc133397789)

[2. Mục đích và mục tiêu thực hiện đề tài	3](#_toc133397790)

[3. Vấn đề đặt ra của đề bài	3](#_toc133397791)

[**PHẦN 2: NỘI DUNG CHÍNH	4****](#_toc133397792)

[1. Kịch bản xây dựng	4](#_toc133397793)

[2. Thiết kế hệ thống	4](#_toc133397794)

[3. Phương án lựa chọn thiết bị	6](#_toc133397795)

[4. Thực hiện mô phỏng trên Cisco Packet Tracer	7](#_toc133397796)

[4.1. Lắp đặt các thiết bị	7](#_toc133397797)

[4.2. Cài đặt dịch vụ DHCP và định tuyến	8](#_toc133397798)

[4.3. Cài đặt DNS server và Web Server	15](#_toc133397799)

[4.4. Cấu hình server IoT	18](#_toc133397800)

[4.5. Thiết lập dịch vụ email	23](#_toc133397801)

[**PHẦN 3: KẾT LUẬN	25****](#_toc133397802)

[**PHẦN 4: TÀI LIỆU THAM KHẢO	26****](#_toc133397803)





# <a name="_toc133397788"></a>**PHẦN 1: GIỚI THIỆU CHUNG**
## <a name="_toc133397789"></a>**1. Đề tài tiểu luận**
Thiết kế xây dựng mạng LAN cho doanh nghiệp có nhiều tầng. Sử dụng dải địa chỉ 192.168.30.0/24 để chia cho toàn bộ hệ thống khoảng 230 máy tính sử dụng.
## <a name="_toc133397790"></a>**2. Mục đích và mục tiêu thực hiện đề tài**
`	`Trong thời buổi kinh tế thị trường hiện nay việc ứng dụng công nghệ thông tin để phục vụ cho việc quản lý, trao đổi, lưu trữ thông tin, dữ liệu trong một tổ chức, công ty là một điều tất yếu. Vì vậy, việc xây dựng hạ tầng mạng LAN là đều rất quan trọng trong một tổ chức hay doanh nghiệp.

`	`Việc xây dựng một hạ tầng mạng tốt giúp các nhân viên trong tổ chức, doanh nghiệp truy nhập dữ liệu một cách thuận tiện với tốc độ cao, kịp thời cập nhật, trao đổi thông tin dữ liệu nhanh chóng. Bên cạnh đó, hệ thống mạng LAN tốt giúp cho người quản trị mạng có thể tổ chức dữ liệu, phân quyền tài nguyên dữ liệu cho từng đối tượng người sử dụng một cách hiệu quả, giúp cho các hoạt động của tổ chức, doanh nghiệp diễn ra một cách trơn tru, mang lại hiệu quả kinh tế cao.

`	`Ngoài ra, việc xây dựng một mạng LAN hoàn chỉnh còn giúp cho sinh viên như chúng em củng cố các kiến thức đã học, bước đầu làm quen với một mô hình mạng doanh nghiệp.

`	`Mục tiêu: Mục tiêu xuyên suốt của đề tài là vận dụng kiến thức đã có và tìm hiểu thêm những kiến thức về mạng để nghiên cứu và xây dựng hệ thống mạng LAN có thế hoạt đông một cách tốt nhất có thể.
## <a name="_toc133397791"></a>**3. Vấn đề đặt ra của đề bài**
**	Với việc thiết kế hệ thống LAN cho doanh nghiệp có nhiều tầng, nghĩa là nhiều phòng ban khác nhau và số thiết bị khoảng 230 máy tình thì việc lựa chọn phương án thiết kế là hết sức quan trọng. Điều này ảnh hưởng trực tiếp đến sự linh hoạt và hiệu suất của hệ thống. Vì vậy trong bài tiểu luận này, em xin đưa ra bản thiết kế cho đề tài này với nội dung bao gồm:

\- Kịch bản xây dựng

\- Thiết kế kiến trúc mạng

\- Phương án lựa chọn thiết bị

\- Mô phỏng thiết kế trên phần mềm Cisco Packet Tracer 
**







# <a name="_toc133397792"></a>**PHẦN 2: NỘI DUNG CHÍNH**
## <a name="_toc133397793"></a>**1. Kịch bản xây dựng**
`	`Thiết kế hệ thống mạng LAN cho một doanh nghiệp 7 tầng với 240 thiết bị, với các tầng lần lượt như sau (Số thiết bị sử dụng bao gồm cả PC, Laptop, Webcam,….):

\- Tầng 1: Phòng Căn tin với tối đa 60 thiết bị. 

\- Tầng 2: Phòng Nhân sự với tối đa 30 thiết bị

\- Tầng 3: Phòng Kế toán với tối đa 30 thiết bị. 

\- Tầng 4: Phòng Tài chính với tối đa 30 thiết bị. 

\- Tầng 5: Phòng Marketing với tối đa 30 thiết bị. 

\- Tầng 6: Phòng IT với tối đa 30 thiết bị. 

\- Tầng 7: Phòng Server với tối đa 30 thiết bị. 

Số lượng thiết bị các phòng có thể tăng giảm đề phù hợp với các hoạt động của công ty nhưng không vượt quá số lượng tối đa. Mỗi tầng đều có một mạng không dây riêng với mật khẩu chung là *12345678*. Các phòng cũng sẽ có một Camera an ninh riêng được kết nối thông qua mạng không dây và có thể quản lí thông qua trang web. Ngoài ra trong tương lai, công ty có thể lắp đặt thêm các thiết bị thông minh khác cũng cần kết nối với mạng không dây và quản lí trên trang web này, ví dụ: Điều hoà, quạt thông minh, phát hiện cháy,…

Công ty có một trang web để khách hàng có thể truy cập và sử dụng dịch vụ của công ty, website này có tên miền là *ptit.edu.vn*. Ngoài ra cần một trang web quản lí nhân sự cho phòng nhân sự và ban lãnh đạo có tên miền là *manage.ptit.edu.vn.* 

##
## <a name="_toc133397794"></a>**2. Thiết kế hệ thống**

`	`Doanh nghiệp gồm có 7 tầng với mỗi tầng là một phòng ban khác nhau, mỗi phòng ban có số thiết bị khác nhau nên em sử dụng kĩ thuật chia mạng VLSM để chia cho từng phòng. Sau khi chia 192.168.30.0/24 thành các dải IP cho từng phòng, mỗi phòng sẽ sử dụng một VLAN riêng cụ thể như:

\- Tầng 1: Phòng Căn tin với 60 thiết bị. Sử dụng dải địa chỉ 192.168.30.0/26

\- Tầng 2: Phòng Nhân sự với 30 thiết bị. Sử dụng dải địa chỉ 192.168.30.128/27

\- Tầng 3: Phòng Kế toán với 30 thiết bị. Sử dụng dải địa chỉ 192.168.30.64/27

\- Tầng 4: Phòng Tài chính với 30 thiết bị. Sử dụng dải địa chỉ 192.168.30.192/27

\- Tầng 5: Phòng Marketing với 30 thiết bị. Sử dụng dải địa chỉ 192.168.30.160/27

\- Tầng 6: Phòng IT với 30 thiết bị. Sử dụng dải địa chỉ 192.168.30.96/27

\- Tầng 7: Phòng Server với 30 thiết bị. Sử dụng dải địa chỉ 192.168.30.224/27

`	`Sử dụng một Switch Layer 3 làm Core Switch cho cả toà nhà nối đến Switch riêng của mỗi tầng. Có thể nối trực tiếp các thiết bị đến Switch thông qua cổng FastEthernet hoặc thông qua kết nối không dây từ Access Point.

`	`Ngoài việc kết nối trực tiếp vào switch, ở mỗi tầng sẽ sử dụng một Access Point để phát sóng WiFi. Điều này giúp cho các thiết bị như điện thoại, máy tính bảng, Laptop hay Webcam có thể dễ dàng kết nối vào mạng mà không cần sử dụng dây.

`	`Do số lượng thiết bị mỗi phòng có thể tăng giảm nên cần sự linh hoạt trong việc gán địa chỉ IP cho các thiết bị. Vì vậy em sử dụng một DHCP Server với mục đích cấp IP động cho từng tầng. Như vậy sẽ đảm bảo ngay khi thiết bị được kết nối với mạng thông qua Switch hoặc Access Point sẽ được cấp địa chỉ IP tự động. Hơn nữa do các tầng đều sử dụng VLAN nên em sử dụng thêm một dịch vụ có tên VTP.

VTP viết tắt của từ *VLAN Trunking Protocol* là giao thức độc quyền của Cisco hoạt động ở lớp 2 của mô hình OSI. VTP giúp cho việc cấu hình VLAN luôn đồng nhất khi thêm, xóa, sửa thông tin về VLAN trong một hệ thống mạng. Để chuyển yêu cầu lấy IP của các thiết bị đến DHCP server cần sử dụng “IP helper-address” . Và cuối cùng để định tuyến chỉ ần sử dụng câu lệnh “ip routing” trong Switch Layer 3. 

`	`Ở mỗi tầng sẽ có một webcam nên cần một IoT Server để có thể quản lí các thiết bị này dễ dàng hơn. Ngoài ra có thể mở rộng/thêm các thiết bị IoT khác như điều hoà, quạt, phát hiện cháy,… Việc truy cập vào trang quản lí sẽ thông qua trang web *iot.ptit.edu.vn.*

`	`Doanh nghiệp có một trang web nên cần một Web Server để host trang web này. Trang web này sẽ được gán domain là *ptit.edu.vn.*

`	`Giữa các nhân viên/phòng ban cần liên lạc với nhau thông qua email nên cần một Mail Server hỗ trợ việc này. Domain cho email sẽ là *ptit.edu.vn*

`	`Cuối cùng, để gán domain cho các dịch vụ ở trên và để các thiết bị có thể truy cập vào các trang web này sẽ cần một DNS Server. Ngoài ra server này cũng host một trang web quản lí nhân viên với tên miền là *manage.ptit.edu.vn*. Do trang web này chỉ nội bộ nhân viên trong doanh nghiệp sử dụng nên không cần một server riêng.







## <a name="_toc133397795"></a>**3. Phương án lựa chọn thiết bị**

Dưới đây là các thiết bị sử dụng và số lượng ước tính dựa trên thiết kế đã đề ra:


|**Tên thiết bị**|**Số lượng**|**Mục đích**|
| :-: | :-: | :-: |
|PC - PT|~ 200|Máy tính của doanh nghiệp|
|Webcam|7|Camera an ninh|
|Server - PT|6|Sử dụng cho các dịch vụ: DHCP, Mail ,DNS, Web, IoT|
|AccessPoint PT-N|6|Phát tín hiệu mạng không dây|
|Switch 3560 24PS|1|Core Switch cho cả toà nhà|
|Switch 2950 - 24|7|Switch riêng cho từng tầng|
|Laptop, Smartphone, Tablet|~ 20|Các thiết bị cá nhân của nhân viên công ty|

## <a name="_toc133397796"></a>**4. Thực hiện mô phỏng trên Cisco Packet Tracer**
### <a name="_toc133397797"></a>*4.1. Lắp đặt các thiết bị*

























###
###
### <a name="_toc133397798"></a>*4.2. Cài đặt dịch vụ DHCP và định tuyến*

\- Trước hết cần cấu hình Core Switch: Tạo và đặt tên các VLAN




\- Cài đặt VTP cho Core Switch sang mode server và đổi domain thành *ptit.edu.vn*




\- Gán dải địa chỉ IP cho từng VLAN






\- Chuyển các cổng kết nối của Core Switch sang mode trunk vì các cổng này được kết nối với các Switch khác




\- Tương tự với các Main Switch ở các tầng, config cổng kết nối với Core Switch thành mode trunk







\- Sau đó chuyển tất cả các cổng còn lại của các Main Switch sang mode access và thêm VLAN tương ứng vào




` `- Gán địa chỉ IP cho Server DHCP






\- Chuyển sang tab Services, chọn DHCP sau đó bật dịch vụ và thêm các “pool” tương ứng với các VLAN theo bản thiết kế



\- Thiết lập dịch vụ IP helper-address trong từng VLAN theo cú pháp

`	`*ip helper-address <ip của server DHCP>*





\- Thiết lập định tuyến cho mạng




Sau khi xong các bước này, các thiết bị đã có thể request để lấy IP, dưới đây là ảnh ví dụ một PC ở VLAN 60 – MARKETING



Như vậy, các thiết bị đã có thể lấy IP đúng theo thiết kế đã đề ra, như ở ảnh trên PC đã lấy đúng dải IP của phòng Marketing (nằm trong dải 192.168.30.60 – 192.168.30.191).

` 	`Tiếp theo, thử ping giữa các PC ở cùng một tầng và khác tầng

\- Ping 2 PC cùng ở tầng 6





\- Từ một PC tầng 1 ping đến một PC khác ở tầng 4



Cả 2 trường hợp đều có tín hiệu reply từ PC được ping, như vậy định tuyến hoạt động rất tốt.



### <a name="_toc133397799"></a>*4.3. Cài đặt DNS server và Web Server*
\- Trước tiên, gán địa chỉ IP tĩnh cho cả 2 server. Với phần DNS của Server DNS  để mặc định là 0.0.0.0, của web server để là IP của server DNS



\- Tiếp theo, ở server DNS chuyển sang tab Services và chọn DNS, sau đó thêm một bản ghi A với name là domain *ptit.edu.vn* và Address là IP của Web server

\- Sau đó vào Web server và chọn tab Service -> HTTP rồi bật cả HTTP và HTTPS. Có thể chỉnh sửa các file code để phù hợp với yêu cầu của doanh nghiệp.

















` `Sau khi config xong, có thể thử truy cập vào trang web thông qua Web Browser của PC bất kì theo tên miền *ptit.edu.vn* hoặc IP của Web Server

Như vậy, trang web đã có thể truy cập được từ tất cả các thiết bị. Nội dung của trang web có thể được thay đổi thông qua việc sửa đổi các file code trong web server.

\- Tiếp theo, theo yêu cầu của doanh nghiệp cần một trang web để quản lí nhân viên, theo kế hoạch website này sẽ được host luôn trong DNS server. Vì vậy chỉ cần thêm một bản ghi A nữa với address chính là IP của DNS server với tên miền là *manage.ptit.edu.vn*





\- Thử truy cập trang web này từ một PC bất kì



Như vậy, trang web đã hoạt động bình thường, phần code của server này đã được em chỉnh sửa lại để có giao diện như trên.

### <a name="_toc133397800"></a>*4.4. Cấu hình server IoT*
`	`Do doanh nghiêp có sử dụng webcam và một số thiết bị IoT khác nên cần một server để quản lí cá thiết bị này. Dưới đây là các bước thực hiện:

\- Gán địa chỉ IP cho server



\- Chuyển sang tab services chọn IoT và chuyển trạng thái sang on (khi mới bật sẽ không có bất cứ user nào, trong hình là user cũ tạo từ trước):



\- Tạo thêm một bản ghi A trong DNS server trỏ đến IP của IoT server với tên miền là *iot.ptit.edu.vn*






\- Truy cập vào tên miền vừa thêm, trang đăng nhập hiện ra, ấn *Sign up now* để tạo một user mới. Ở đây em để cả username và password là “cisco”.



\- Sau khi đăng nhập, trang web sẽ chuyển đến phần quản lý các thiết bị IoT hiện đã kết nối, vì chưa kết nối bất cứ thiết bị nào nên danh sách sẽ trống. Tiếp tục thiết đặt một Access Point cho từng phòng để kết nối webcam qua tín hiệu không dây. Đầu tiên cần nối Access Point với Switch chính của tầng đó, sau đó thay đổi tên của mạng không dây ở phần “SSID” , chọn kiểu password là WP2A-PSK và điền vào phần PSK Pass Phrase là “12345678”. Đây là mật khẩu mặc định đã ghĩ rõ trong bản thiết kế: 


\- Sau đó truy cập vào webcam, kết nối với mạng không dây thông qua phần Config-> Wireless0. SSID là tên mạng không dây tương ứng của từng tầng, password mặc định là “12345678”:



\- Tiếp tục chuyển sang tab Settings để add remote cho webcam. Ở phần IoT Server chọn Remote Server, với Server Address là địa chỉ IP của IoT Server, Username và password điền chính xác như đã tạo ở bước trước đó:



\- Sau khi thực hiện các bước tương tự trên webcam của từng tầng, truy cập lại trang web *iot.ptit.edu.vn* để bật webcam, ấn vào nút hình chữ nhật màu đỏ để bật Webcam:



` `Sau khi hoàn thành đủ các bước, có thể thấy các webcam đã hoạt động bình thường. Thông qua trang web này có thể bật tắt và xem các web cam, ngoài ra có thể điều khiển cả các thiết bị khác với các bước tương tự webcam.









### <a name="_toc133397801"></a>*4.5. Thiết lập dịch vụ email*

\- Gán IP cho server Email



\- Chuyển sang Services -> Email, Domain Name là “ptit.edu.vn” sau đó thêm user để bằng cách điền vào “User” và “ Password” sau đó ấn “+”


\- Tạo tài khoản và đăng nhập ở 2 PC với thông tin đã đăng kí ở bước trước. Phần Server Information điền IP của Mail Server



\- Thử gửi/ nhận email



`	`Như vậy PC kia đã nhận được email, hoàn thành thiết lập dịch vụ email cho công ty.







# <a name="_toc133397802"></a>**PHẦN 3: KẾT LUẬN**

Qua phần mô phòng trên phần mềm Cisco Packet Tracer, em đã hoàn thành việc mô phỏng một hệ thống mạng LAN đáp ứng đủ các yêu cầu của doanh nghiệp thông qua việc sử dụng các dịch vụ như DHCP, VLAN, DNS server, Mail server,… Việc sử dụng một Switch Layer 3 thay cho router là vì Switch Layer 3 thường có khả năng xử lý định tuyến và chuyển tiếp gói tin giống như một router, nhưng với hiệu suất tốt hơn. Trong một mạng LAN nhỏ hoặc trung bình, nếu cần thực hiện các chức năng định tuyến đơn giản và không có yêu cầu đặc biệt về bảo mật, việc sử dụng một Switch Layer 3 có thể là một lựa chọn tốt hơn so với việc sử dụng một router. Điều này có thể giúp giảm chi phí cho doanh nghiệp.

Tuy nhiên, trong một mạng lớn hơn hoặc có yêu cầu bảo mật cao, router vẫn là một lựa chọn tốt hơn. Router có khả năng xử lý định tuyến phức tạp hơn, bảo mật mạng tốt hơn và có thể kết nối với các mạng khác nhau, trong khi Switch Layer 3 thường chỉ phục vụ cho một mạng LAN duy nhất. 

Về phạm vi của bài tiểu luận này, với yêu cầu chính tập trung vào việc thiết kế mạng phù hợp cho doanh nghiệp nên tạm thời có thể bỏ qua các dịch vụ bảo mật như Firewall hay VPN.

Cuối cùng, có thể kết luận rằng việc thiết kế mạng LAN phù hợp cho doanh nghiệp là một công việc quan trọng và phức tạp, đòi hỏi sự tập trung và chú ý đến nhiều yếu tố khác nhau. Tuy nhiên, việc đầu tư thời gian và nỗ lực để thiết kế một hệ thống mạng LAN tốt sẽ giúp cho doanh nghiệp đạt được hiệu quả và hiệu suất tốt hơn trong hoạt động kinh doanh của mình.


# <a name="_toc133397803"></a>**PHẦN 4: TÀI LIỆU THAM KHẢO**
#
[1] <https://www.youtube.com/watch?v=s5t_iYOEX5M>

[2] <https://www.youtube.com/watch?v=_sr9yTw20FU>

[3] <https://www.youtube.com/watch?v=Pv7Oo6eqNRo>

[4] <https://www.youtube.com/watch?v=_BVvXph43aM>

[5] <https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipaddr_dhcp/configuration/15-sy/dhcp-15-sy-book/dhcp-relay-agent.html>

[6] <https://timigate.com/2018/08/configure-cisco-dhcp-relay-agents-using-packet-tracer-in-two-minutes.html>



