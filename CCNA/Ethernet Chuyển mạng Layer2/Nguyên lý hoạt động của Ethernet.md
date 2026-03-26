Ethernet là tiêu chuẩn giao thức chiếm ưu thế trong các mạng cục bộ LAN, hoạt động dựa trên cơ chế chia sẻ băng thông và kiểm soát truy cập môi trường truyền dẫn. Để các thiết bị trong mạng có thể giao tiếp được với nhau mà không bị xung đột dữ liệu, Ethernet sử dụng một phương thức gọi là `CSDM/CD(Carrier Sense Multiple Access with Collision Dêtction)` 
#### Cơ chế CSMA/CD: Kiểm soát xung đột
Trong môi trường Ethernet truyền thống đặc biệt là hub cũ hoặc cấu trúc mạng bus, nhièu thiết bị cugnf chia sẻ một môi trường truyền dẫn. Nếu hai thiết bị cugnf truyèn dữ liệu một lúc, tín hiệu sẽ bị va chạm(collision), dẫn đến dữ liệu bị hỏng

`CSMA/CD hoạt động theo 3 bước`:
- Carrier Sense(kiẻm tra môi trường): trước khi truyền, thiết bị "lắng nghe" đường truyền. Nếu dường truyền trống, nó mới bắt đầu gửi dữ liệu.
- Multiple Access(Truy cập đa điểm): Nhiều thiết bị có quyền truy cập vào đường truyền bất cứ khi nào nó rảnh
- Collision Detection(phát hiện xung đột): Khi đó, chúng sẽ ngay lập tức dừng gửi và gửi một tín hiệu "jam" để thông báo cho toàn bộ  mạng về xung đột này
![[Pasted image 20260317160442.png]]
_Lưu ý:_ Với các switch hiện đại, hiện tượng xung đột gần như không còn tồn tại vì mỗi cổng của switch tạo ra một "collision domain" riêng biệt (công nghệ full-duplex), cho phép gửi và nhận dữ liệu đồng thời mà không cần CSMA/CD.
## Chế độ truyền dẫn: Half-Duplex và Full-Duplex
Ethernet vận hành theo hai chế độ chính quyết định hiệu suất của mạng:
### Half-Duplex (Bán song công)
Thiết bị có thể gửi hoặc nhận dữ liệu, nhưng không thể làm cả hai cùng một lúc. Hãy hình dung giống như bộ đàm (walkie-talkie): khi người này nói, người kia phải nghe. Chế độ này thường đi kèm với cơ chế CSMA/CD và được sử dụng trên các hub hoặc trong môi trường truyền dẫn cũ.
### Full-Duplex (Song công toàn phần)
Thiết bị có thể gửi và nhận dữ liệu đồng thời thông qua các cặp dây riêng biệt (ví dụ: một cặp dây truyền, một cặp dây nhận trên cáp xoắn đôi). Vì không có xung đột, switch không cần sử dụng CSMA/CD. Đây là tiêu chuẩn trong các mạng hiện đại ngày nay, cho phép băng thông lý thuyết tăng gấp đôi so với chế độ half-duplex.
![[Pasted image 20260317165258.png]]
![[Pasted image 20260318092946.png]]
![[Pasted image 20260319074936.png]]
![[Pasted image 20260319081839.png]]
![[Pasted image 20260319082157.png]]
![[Pasted image 20260319082406.png]]
![[Pasted image 20260319082545.png]]
![[Pasted image 20260319082724.png]]
![[Pasted image 20260319082820.png]]
### Frame Ethernet và địa chỉ MAC

Ethernet là tiêu chuẩn công nghệ thống trị trong mạng LAN, ở tần DataLink, dữ liệu không được truyền đi dưới dạng dòng bit thô mà dược đóng gói vào các đơn vị gọi là Ethernet Frame. Chính cấu trúc của Frame này cho phép thiét bị mạng xác định được nơi gửi, nơi nhận và kiểm tra tính toàn vẹn của dữ liệu.
#### Cấu trúc của một Ethernet Frame 
Một Ethernet Frame chuẩn IEEE 802.3 bao gồm nhiều thành phần được thiết kế đẻ đảm bảo dữ liệu đến đúng đích và không bị lỗi tỏng quá trình truyền dãn.
![[Pasted image 20260319083007.png]]
![[Pasted image 20260319083241.png]]
![[Pasted image 20260319083751.png]]
#### Đại chỉ MAC: Định danh vật lý
Đại chỉ MAC(Media Access Control) là định danh duy nhất được gán cứng vào card mạng (NIC) bưởi nhà sản xuát. Khác với địa chỉ IP có thể thay đổi tùy vào cấu trúc mạng. địa chỉ MAC gắn liền với phần cứng

Địa chỉ MAC có độ dài 48 bit(6 bytes), thường được biểu diễn dưới dạng số thập luc jphaanf, ví dụ: `00:0A:9D:68:16` 
Địa chỉ này được thành 2 phần như 
- OUI(Organizationlly Unique Identifier - 3 bytes đầu): Mã  định danh nahf sản xuất (ví dụ như Cisco, Intel, Dell, ...)
- Vendor - assigned (3 bytes sau): Mã định danh duy nhất cho từng thiết bị cụ thể do nhà sản xuất quy định
#### Các loại địa chỉ MAC đích
Khi một frame được gửi đi, ddiaj chỉ MAC đích trong frame xác định một cách switch xử lý frame đó: 
Unicast: Gửi cho một thiêt bị cụ thể (bit đầu tiên của bytes đầu tiên là 0)
Broadcast: Gửui cho tất cả thiếtb ị trong mạng địa chỉ là `FF:FF:FF:FF:FF:FF`
Multicast: Gửi cho một nhóm các thiết bị được chỉ định(bit đầu tiên của bytes đầu tiên là 1)
![[Pasted image 20260319093442.png]]
Một Ethernet Frame chuẩn (theo chuẩn IEEE 802.3) bao gồm nhiều thành phần được thiết kế để đảm bảo dữ liệu đến đúng đích và không bị lỗi trong quá trình truyền dẫn.

|Thành phần|Độ dài (bytes)|Mô tả|
|---|---|---|
|**Preamble**|7|Dãy bit xen kẽ 0 và 1 dùng để đồng bộ xung nhịp giữa các thiết bị.|
|**Start Frame Delimiter (SFD)**|1|Đánh dấu sự bắt đầu thực sự của khung dữ liệu.|
|**Destination MAC**|6|Địa chỉ vật lý của thiết bị nhận.|
|**Source MAC**|6|Địa chỉ vật lý của thiết bị gửi.|
|**Type/Length**|2|Chỉ định giao thức lớp trên (ví dụ: IPv4 hoặc IPv6).|
|**Payload (Data)**|46 - 1500|Dữ liệu thực tế truyền đi.|
|**Frame Check Sequence (FCS)**|4|Sử dụng thuật toán CRC để kiểm tra xem frame có bị lỗi không.|
![[Pasted image 20260319094310.png]]
![[Pasted image 20260319094407.png]]
![[Pasted image 20260319094923.png]]
## Quá trình xử lý lỗi với FCS
Frame Check Sequence (FCS) là cơ chế "bảo hiểm" của tầng Layer 2. Khi thiết bị nhận một frame, nó sẽ thực hiện tính toán lại giá trị CRC dựa trên nội dung của khung đó và so sánh với giá trị được lưu trong phần FCS.
- **Nếu khớp:** Frame được chấp nhận và xử lý tiếp.
- **Nếu không khớp:** Thiết bị hiểu rằng khung đã bị lỗi trong quá trình truyền (do nhiễu điện từ hoặc va chạm tín hiệu), nó sẽ **hủy bỏ khung ngay lập tức** mà không gửi thông báo cho thiết bị gửi. Việc khôi phục dữ liệu bị mất này sẽ do các giao thức ở tầng trên (như TCP ở Layer 4) đảm nhận.
![[Pasted image 20260319095621.png]]
![[Pasted image 20260319100513.png]]
![[Pasted image 20260319100602.png]]
![[Pasted image 20260319102243.png]]
### Chuyển mạch Layer 2 và bảng CAM

Chuyển mạch Layer 2 là quá trình một thiết bị chuyẻn mạch (Switch) quyết định chuyển tiếp khung dữ liệu Frame dựa trên địa chỉ MAC đích. Không giống như Hub phân tán dữ liệu ra tất cả các cổng, Switch tạo ra các phan đoạn mạng riêng biệt bằng cách học vị trí của các thiết bị và thiết lập kênh truyèn trực tiếp giữa nguồn và đích

#### Bảng CAM và cơ chế Forwarding
Trái tim của một Switch là bảng CAM (Content Addressable Memory), hay conf goij laf bangr ddijja chir MAC. Đây là bảng tra cứu cho phép Switch biết cổng vật lý nào tương ứng v ợi địa chỉ MAC nào
Khi một khung dữ lliệu đến một cổng của Switch, quá trinh xử lý diễn ra theo trình tự sau:
1. `Học địa chỉ MAC (Learning)`: Switch kiểm tra địa chỉ MAC nguồn (Source MAC) của khung dữ liệu. Nếu địa chỉ này chưa có trong bảng `CAM`, Swith sẽ hgi lại địa chỉ MAC đó cùng với cổng mà nó vừa nhận được dữ liệu.
2. `Quyết định chuyển tiếp (Forwarding)` : Switch kiểm tra địac hỉ MAC đích (Destination MAC)
- Nếu địac hri MAC đích tồn tại trong bảng CAM, Switch chỉ gửi khung dữ liệu ra cổng tương ứng (Unicast)
- Nếu địac hỉ MAC đích không có trong bảng (hoặc là địac hri Broadcast `FF:FF:FF:FF:FF:FF`) Switch sẽ đẩy khung duewx liệu ra tất cả các cổng trừ cổng vừa nhận (FLooding)
![[Pasted image 20260319104636.png]]
![[Pasted image 20260319104756.png]]
![[Pasted image 20260319105911.png]]
![[Pasted image 20260319115517.png]]
![[Pasted image 20260319115612.png]]
![[Pasted image 20260319133442.png]]
![[Pasted image 20260319133524.png]]
![[Pasted image 20260319141140.png]]
![[Pasted image 20260319142533.png]]
![[Pasted image 20260319142719.png]]
![[Pasted image 20260319143345.png]]
### Các công nghệ VLAN và Trunking
VLAN (Virtual Local Area Network) là giải pháp chia nhỏ một mạng vật lý thành nhiều mạng logic độc lập ngay trên thiết bị chuyển mạch (Switch). Trong môi trường mạng truyền thống, tất cả thiết bị kết nối vào một Switch sẽ nằm chung một miền quảng bá (Broadcast Domain), dẫn đến việc lưu lượng broadcast (như ARP, DHCP) lan truyền khắp nơi, làm giảm băng thông và tiềm ẩn rủi ro bảo mật. VLAN cô lập các nhóm người dùng này, buộc lưu lượng giữa các VLAN phải đi qua Router hoặc Layer 3 Switch để kiểm soát.
## Phân đoạn mạng với VLAN

Khi bạn cấu hình VLAN, mỗi cổng trên Switch sẽ được gán vào một ID cụ thể (VLAN ID). Các máy tính trong cùng một VLAN ID có thể giao tiếp với nhau trực tiếp ở Layer 2, trong khi máy tính ở các VLAN khác nhau thì không thể, ngay cả khi chúng cắm chung trên một Switch vật lý.

Cơ chế này mang lại hai lợi ích cốt lõi:

- **Tối ưu hóa băng thông:** Giới hạn phạm vi của traffic broadcast chỉ trong nội bộ VLAN đó.
- **Tăng cường bảo mật:** Chỉ những người dùng được phép mới có thể truy cập vào các tài nguyên mạng nhất định (ví dụ: tách biệt VLAN Kế toán và VLAN Khách).
## Giao thức Trunking (802.1Q)

Trunking là kỹ thuật cho phép truyền tải dữ liệu của nhiều VLAN khác nhau trên một đường truyền vật lý duy nhất giữa các thiết bị mạng (thường là giữa các Switch hoặc giữa Switch và Router). Nếu không có Trunking, bạn sẽ cần mỗi VLAN một sợi cáp vật lý riêng biệt nối giữa hai Switch, điều này hoàn toàn bất khả thi khi số lượng VLAN tăng lên.

Để phân biệt Frame của VLAN nào đang đi qua đường truyền Trunk, Switch sử dụng chuẩn **IEEE 802.1Q**. Giao thức này chèn thêm một "Tag" (thẻ) vào tiêu đề (header) của Frame Ethernet.****
![[Pasted image 20260319151736.png]]
- **Tagging:** Thêm VLAN ID (12-bit) vào trong Frame Ethernet gốc.
- **Native VLAN:** Đây là một khái niệm quan trọng trong 802.1Q. Frame thuộc VLAN này khi đi qua đường Trunk sẽ không bị gắn tag. Thông thường, mặc định tất cả các port thuộc về VLAN 1 và VLAN 1 cũng được coi là Native VLAN. Vì lý do bảo mật, người ta thường đổi Native VLAN sang một ID khác để tránh tấn công "VLAN Hopping".
![[Pasted image 20260319152456.png]]
![[Pasted image 20260319152844.png]]
![[Pasted image 20260319154955.png]]
![[Pasted image 20260319160241.png]]
![[Pasted image 20260319161030.png]]
![[Pasted image 20260319161428.png]]
![[Pasted image 20260319161844.png]]
VLAN và Trunking cho phép chúng ta chia nhỏ miền quảng bá và tối ưu hóa tài nguyên phần cứng bằng cách truyền tải nhiều mạng logic trên cùng một đường vật lý. Đây là nền tảng để xây dựng các cấu trúc mạng phân lớp, bảo mật và dễ quản lý. Tiếp theo, chúng ta sẽ tìm hiểu cách ngăn chặn các vòng lặp (loop) phát sinh khi mở rộng mạng bằng giao thức Spanning Tree Protocol (STP).
![[Pasted image 20260319162547.png]]
![[Pasted image 20260319163112.png]]
![[Pasted image 20260319163238.png]]
![[Pasted image 20260319163447.png]]
![[Pasted image 20260319163601.png]]
![[Pasted image 20260319163901.png]]
![[Pasted image 20260319163951.png]]
![[Pasted image 20260319164148.png]]
![[Pasted image 20260319164634.png]]
![[Pasted image 20260319165345.png]]
# Giao thức Spanning Tree Protocol (STP)

Spanning Tree Protocol (STP) là giao thức lớp liên kết dữ liệu được thiết kế để ngăn chặn các vòng lặp (loops) trong mạng Ethernet khi có các liên kết dự phòng (redundant links). Nếu không có STP, các gói tin broadcast trong môi trường chuyển mạch sẽ luân chuyển vô tận giữa các switch, dẫn đến tình trạng bão hòa broadcast (broadcast storm), chiếm dụng toàn bộ băng thông và làm treo bảng địa chỉ MAC của thiết bị.
#### Cách thức hoạt động cảu STP
STP hoạt động bằng cách đặt các cổng dư thừa vào trạng thái `Blocking` thay vì `Forwarding` . Để thực hiện điều này, các Switch chạy thuật toán STP để chọn ra một cấu trúc liên kết hình cây không có vòng lặp, trong mọi đường truyền đều có thể tới đích thông qua một lộ trình duy nhát
Quy trình bầu chọn diễ ra theo ác bước nghiêm ngặt:
1. `Bầu chọn Root Bridge`: Switch có giá trị Bridge ID thấp nhát sẽ trở thành trung tâm cua mạng. Bridge ID bao gồm hai phàn: Bridge Priority mặc định là 32768 và đĩa chỉ MAC . Switch có Priority thấp nhất thắng; nếu bằng nhau, switch có địa chỉ MAC nhỏ nhất sẽ thắng
2. `Chọn Root Port`: trên mỗi switch, cổng có chi phí thấp nhất để đi tới Root Bridge sẽ được chọn làm Root Port
3. `Chọn Designated Port`: trên mỗi phân đoạn mạng segment, switch có chi phí thấp nhất để tới Root Bridge ssex có cổng đóng vai trò Designated Port. Các cổng này có nhiệm vụ chuyển tiếp dữ liệu
4. `Trạng yhais Blocking`: Mọi cổng không phải Root Port hoặc Designated Port sẽ bị dưa vêf trạng thái Blocking để ngăn chặn vòng lặp
![[Pasted image 20260320081729.png]]
![[Pasted image 20260320081955.png]]
![[Pasted image 20260320082451.png]]
An ARP request is ==a broadcast message sent by a device on a local area network (LAN) asking for the physical MAC address associated with a specific IP address==. It is part of the Address Resolution Protocol (ARP), used to map Network Layer (IP) addresses to Data Link Layer (MAC) addresses, enabling data delivery
#### Why do we need Spanning Tree?
![[Pasted image 20260320085405.png]]
In the picture above, we have two switches. These switches are connected with a single cable, so there is a **single point of failure**. To get rid of this single point of failure, we will add another cable:
![[Pasted image 20260320085458.png]]
Thêm 1 sợi dây, chúng ta có `redundancy`(sự dư thừa). Thật không may cho chúng ta là sự dự thừa đó cũng tạo thành vòng lặp. Tại sao lại có vòng lặp đó?
- H1 sends an ARP request because it's looking for the MAC address of H2. An ARP request is a broadcast frame
- SW1 sẽ chuyển tiếp cái broadcast frame này tới tất cả các interface, ngoại trừ interface gửi cái đó
- SW2 sẽ nhận cả 2 cái broadcast frame đó luôn
So, what does SW2 do wwith those broadcast frame?
1. Nó lại chuyển tiếp đi ra tất cả các interface mà nó đang có