Thiết kế một mạng văn phòng nhỏ đòi hỏi sự kết hợp giữa hiểu biết lý thuyết về mô hình phân lớp và tư duy thực tiễn về luồng dữ liệu. Một văn phòng điển hình với 10-20 thiết bị không cần các cấu trúc phức tạp như các trung tâm dữ liệu, nhưng yêu cầu sự ổn định, khả năng mở rộng tối thiểu và tính phân đoạn hợp lý để đảm bảo hiệu suất.

### Phân tích yêu cầu và hạ tang vật lý

Trước khi kết nối bất kỳ thiết bị nào, bạn cần xác định ranh giới vật lý và logic. Một văn phòng nhỏ thường bao gồm:
- **Thiết bị đầu cuối (End Devices):** Máy tính nhân viên, máy in mạng, điện thoại IP.
- **Thiết bị truy cập (Access Layer):** Switch (cung cấp cổng kết nối vật lý), Access Point (AP - cung cấp kết nối không dây).
- **Thiết bị biên (Edge/Gateway):** Router (kết nối văn phòng với Internet).
![[unnamed (1).png]]
Trong mô hình mạng hiện đại, sự phân chia giữa Layer 1 (Vật lý) và Layer 2 (Liên kết dữ liệu) được thể hiện rõ nhất ở Switch. Switch nhận tín hiệu điện từ cáp xoắn đôi (vật lý), sau đó đọc địa chỉ MAC trong Frame Ethernet (liên kết dữ liệu) để chuyển tiếp gói tin đến đúng cổng đích.
![[Pasted image 20260311095004.png]]

![[Pasted image 20260311095042.png]]
## Tư duy thiết lập mạng phân đoạn
Thay vif cắm tất cả mọi thứ vào một thiết bị duy nhát, hãy phan tách hệ thống theo vai trò. Sai lầm phổ biến của người mới bắt đầu là `Phẳng hóa` mạng(Flat network), nơi mọi thiết bị đều nhìn thấy nhau, dẫn đến hiện tượng Broadcast Storm khi số lươnjg thiết bị tăng lên.
### Nguyên tắc 1: Cấu trúc hình sao (Star Topology)
**Mọi thiết bị phải kết nối về Switch trung tâm**. Điều này đảm bảo nếu một sợi cáp hoặc một thiết bị dầu cuối bị lõi, toàn bộ mạng văn phòng vẫn hoạt động được.
### Nguyễn tắc 2: Tách biệt lưu lượng VLAN căn bản
Ngay cả mạng nhỏ đi nữa thì việc phân tách lưu lượnng giữa `Thiết bị văn phòng` và `Thiết bị khách(Guest Wifi)` là cần thiết để bảo mật. Chúng ta séuwr dụng VLAN(Virtual LAN) để chia nhỏ Switch vật lý thành các miền quảng bá(broadcast domains) logic riêng biệt.
### Nguyên tắc 3: Xác định đường đi dữ liệu(Data path)
Mỗi thiết bị mạng cần một địa chỉ IP(Layer 3 Network). Để các thiết bị này có thể giao tiếp được với nhau cùng một dải, chúng gửi Frame với địa chỉ MAC đích. Nếu đích nằm ngoài dải mạng(web). Frame sẽ được gửi tới `Default Gateway` thường là `router`
### Các bước triển khai thực tế

1. Lập sơ đồ đấu nối: Vẽ sơ đồ vị trí các ổ cắm mạng trên tường và vị trí đặt Switch
2. Cáp mạng (Layer 1):  luôn sử dụng chuẩn cáp `T568B` cho cả hai đầu đối với mạng LAN văn phòng. Đảm bảo độ dài cáp không quá 100m để tránh suy hao tín hiệu
3. Đặt tên và gán cổng(Layer 2): trên Switch, gán nhãn cho từng cổng. Ví dụ, cổng 1-10 cho máy tính, cổng 11-15 cho máy in, 20-24 cho AP. Điều này giúp xử lý sự cố nhanh chóng sau này
4. Kiểm tra đèn tín hiệu: Đèn LED trên Switch là công cụ chẩn đoán nhanh nhất. Đèn màu xanh lá ổn định nghĩa là liên kết vật lý (Link) đã sẵn sàng. Đèn nhấp nháy báo hiệu đang có luồng dữ liệu(Traffic) đi qua
>Lưu ý: ***Trong văn phòng hãy luôn ưu tiên kết nối có dây cho máy tính để bàn và máy in để đảm bảo băng thông ổn định. Chỉ sử dụng Wifi cho thiết bị di động hoặc các vị trí không có dây tới***

![[Pasted image 20260311104831.png]]
![[Pasted image 20260311104925.png]]
![[Pasted image 20260311105005.png]]
![[Pasted image 20260311105528.png]]
![[Pasted image 20260311105716.png]]
![[Pasted image 20260311105739.png]]
![[Pasted image 20260311105803.png]]
![[Pasted image 20260311105955.png]]
![[Pasted image 20260311133040.png]]
![[Pasted image 20260311133447.png]]
![[Pasted image 20260311133519.png]]
![[Pasted image 20260311133657.png]]
![[Pasted image 20260311133744.png]]
![[Pasted image 20260311133937.png]]
# Giới thiệu về Router, Switch, Hub và Access Point
Thiết bị mạng là xương sống của mọi hạ tầng viễn thông. Để hiểu cách dữ liệu di chuyển từ điểm A đến điểm B, bạn cần nắm rõ chức năng vật lý và logic ủa bốn thiết bị nền tảng: Hub, Switch, Roter và Access Point
#### Hub: Thiết bị lớp vật lý(Layer 1)
Hub là thiết bị kết nói trung tâm cho ác máy tính trong cùng một phân đoạn mạng LAN. Về mặt kỹ thuật, Hub hoạt động hoàn toàn ở Lớp 1 của mô hình OSI

Khi một tín hiệu điện(dữ liêu) đi vào một cổng của Hub, Hub sẽ sao chép tín hiệu đó ra tất cả các cổng còn lại ngoài trừ cổng nhận. Quá trình này được gọi là `flooding`. Hub không hiểu địa chỉ MAC hay địa chỉ IP; nó chỉ là một thiết bị lặp tín hiệu(repeater) đa cổng.
- *`Vấn đề cốt lõi`*: Vì Hub gửi dữ liệu đến mọi thiết bị, nó tạo ra một `Collision Domain`(miền xung đột) duy nhât. Nếu hai thiết bị gửi  dữ liệu cùng lúc, xung đột sẽ xảy ra và các gói tin bị hỏng
- *`Tình trạng hiện tại`*: Hub gần như đã bị loại bỏ trong mạng hiện đại vì tính kém hiệu quả và bảo mật thấp(bất kỳ ai cắm vào Hub cũng có thể "nghe lén" lưu lượng của người khác)
![[Pasted image 20260313103145.png]]

#### Switch: Thiết bị lớp liên kết dữ liệu - Data-Link (Layer 2)
Switch thông mình hơn Hub nhờ khả năng đọc địa chỉ `MAC` của Frame. Switch xây dựng một bảng gọi là `Bảng MAC` hay `CAM` Table để ghi nhớ địa chỉ MAC nào nằm ở cổng nào
Khi một frame đến, Switch sẽ tra cứu địa chỉ MAC đích trong bảng CAM:
- Nếu tìm thấy cổng tương ứng, nó chỉ gửi dữ liệu đến cổng đó Unicast
- Nếu không tìm thấy, nó sẽ gửi dẽ liệu ra tất cả cổng(Broascast) để tìm thiết bị đó
***`Ưu điểm vượt trội của Switch`*** : 
 - `Giảm xung đột`: Mỗi cổng trên Switch là một `Collision Domain` riêng biệt. Điều này cho phép truyền dữ liệu song công(full-duplex) mà không sợ bị xung đột
 - `Tối ưu hóa băng thông`: Dữ liệu chỉ dược gửi đến đích, không làm phiền các thiết bị khác tỏng mạng
 ![[Pasted image 20260313104544.png]]
 
![[Pasted image 20260313104447.png]]
#### Router: Thiết bị lớp mạng - Network(Layer 3)
Router là thiết bị kết nối các mạng khác nhau(ví dụ: Kết nối các mạng LAN của ta với Internet). Router hoạt động ở Lớp 3(Network Layer) và `Quyết định đường đi dựa trên địa chỉ IP`
Khác với Switch, Router không chuyển tiếp gói tin broadcast(trừ khi được cấu hình đặc biệt). Router chia mạng thành các `Broadcast domain` riêng biệt. Mỗi khi nhận một gói tin, Router xem địa chỉ `IP đích` , tham  chiếu đến `Bảng định tuyến Router Table` để quyết định cổng ra `interface` tối ưu nhất.
"Tóm tắt sự khác biệt": Switch kết nối các thiết bị trong cùng một `LAN`, trong khi Router kết nối các mạng khác nhau(WAN/Internet)
#### Access Point
Access Point đóng vai trò là "trạm phát sóng", cho phép các thiết bị không dây wifi kết nối vòa mạng có dây. AP không phải là thiết bị vô tuyến; nó thực chất là một `Switch không dây`
- Khi một thiết bị Wifi gửi dữ liệu, AP nhận sóng vô tuyến, chuyển thành tính hiệu điện và truyền vào mạng có dây qua cổng `Ethernet` kết nối với Switch
- AP hiện đại thường đi kèm với các tính năng bảo mật `WPA3` và quản lý lưu lượng để đảm bảo nhiều thiết bị không dây có thể giao tiếp đồng thời mà không bị troe mạng.
![[Pasted image 20260313104915.png]]
![[Pasted image 20260313105210.png]]

![[Pasted image 20260313105227.png]]


![[Pasted image 20260313105256.png]]
### Bảng só sánh thiết bị mạng
| Thiết bị     | Lớp OSI | Xử lý dữ liệu dựa trên | Phạm vi hoạt động         |
| ------------ | ------- | ---------------------- | ------------------------- |
| Hub          | Layer 1 | Tín hiệu điện, Bit     | Một Collision domain      |
| Switch       | Layer 2 | Địa chỉ MAC, Frames    | Một mạng LAN              |
| Router       | Layer 3 | Địa chỉ IP, Packet     | Giữa các mạng khác nhau   |
| Access Point | Layer 2 | Địa chỉ MAC, frames    | Kết nối không dây vào LAN |
![[Pasted image 20260313105325.png]]
### Cấu hình cơ bản Switch Cisco

Cisco IOS(Internetwork Operating System) sử dụng một cấu trúc phân cấp các chế độ(model) để quản lý thiết bị. Khi bạn kết nối vào switch qua cổng console, bạn bắt đầu ở chế độ `User Exec`, nơi quyền hạn bị hạn chế. Để thực hiện bất kỳ thay đổi cấu hình nào, bạn phả di chuyển qua các cấp độ quyền cao hơn.
#### Phân cấp chế độ hoạt động trong IOS
Mỗi chế độ trong Cisco IOS có một dấu nhắc(prompt) đặc trưng, cho biết bạn đang ở đâu và có thể thực hiện những gì:
1. `User EXEC Mode:`  `Switch>`  - Cho phép xem trạng thái cơ bản, nhưng không thể cấu hình
2. `Privileged EXEC Mode` : `Switch#` - Cho phép xem toàn bộ trạng thái và quản trị thiết bị. Truy cập bằng lệnh `enable` 
3. `Global Configuration Mode:`  `Switch(config)#` - Nơi thực hiện các thay đổi cấu hình ảnh hưởng tới toàn bộ switch. Truy cập bằng lệnh `configure terminal`
4. `Interface/Line Mode:` `Switch(config-if)#` hoặc `Switch(config-line)#` - Dành riêng cho cấu hình trên một cổng vật lý hoặc cổng quản trị cụ thể.
### Bảng tóm tắt lệnh chuyển mode

| Từ mode                   | Sang mode                        | Lệnh                                                  |
| ------------------------- | -------------------------------- | ----------------------------------------------------- |
| User EXEC `>`             | Privileged EXEC `#`              | `enable`                                              |
| Privileged EXEC `#`       | User EXEC `>`                    | `disable`                                             |
| Privileged EXEC `#`       | Global Config `(config)#`        | `configure terminal` (hoặc `conf t`)                  |
| Global Config `(config)#` | Privileged EXEC `#`              | `exit` hoặc `end` hoặc `Ctrl+Z`                       |
| Global Config `(config)#` | Sub-config `(config-if)#` ...    | `interface Fa0/1`, `line vty 0 4`, `router ospf 1`... |
| Sub-config `(config-if)#` | Global Config `(config)#`        | `exit`                                                |
| Sub-config `(config-if)#` | Privileged EXEC `#` (nhảy thẳng) | `end` hoặc `Ctrl+Z`                                   |
| Bất kỳ                    | Thoát khỏi thiết bị              | `logout` hoặc `exit`                                  |

**Lưu ý quan trọng:**

- `exit` — lùi **1 cấp** (sub → global → privileged)
- `end` / `Ctrl+Z` — nhảy **thẳng về Privileged EXEC** từ bất kỳ config mode nào
- Mật khẩu `enable secret` có thể được hỏi khi gõ `enable` nếu đã cấu hình

### Các bước cấu hình cơ bản
![[cisco_ios_mode_switching.svg|697]]


Một switch Cisco mới xuất xưởng cần được thiết lập cơ bản để đẩm bảo tính bảo mật và khả năng quản lý.
![[Pasted image 20260315190904.png]]

1. Đặt tên thiết bị
- Phải gõ `enable` trước để vào chế độ `Privileged`
```bash
Switch# configure terminal
```
Chuyển sang chế độ `Global Configuration Mode` 
`Switch(config)#` hostname SW-Floor1
![[Pasted image 20260315184021.png]]
2. Bảo mật truy cập
Ta cần chặn người lạ truy cập vào `console` và quan mạng `SSH/Telnet`. Cần đặt mật khẩu cho chế độ `Privileged EXEC` và cổng console
```bash
SW-Floor1(config)# enable secret Cisco123  ! Mật khẩu cho chế độ quyền cao nhất
SW-Floor1(config)# line console 0
SW-Floor1(config-line)# password ConsolePass
SW-Floor1(config-line)# login             ! Bắt buộc kiểm tra mật khẩu
SW-Floor1(config-line)# exit
```
3. Cấu hình IP quản lý (Switch Virtual Interface - SVI)
Mặc định switch Layer 2 không có IP trên các cổng vật lý. Để quản lý switch từ xa, bạn cần phải đặt IP cho một interface ảo gọi là `VLAN 1` 
```bash
SW-Floor1(config)# interface vlan 1
SW-Floor1(config-if)# ip address 192.168.1.10 255.255.255.0
SW-Floor1(config-if)# no shutdown
SW-Floor1(config-if)# exit
```
4. Lưu trữ cấu hình
Cisco lưu cấu hình hiện tại trên `RAM(running-config)`, sẽ mất khi tắt. Để lưu vĩnh viễn, bạn phải ghi vào `NVRAM (Startup-config)` 
```
SW-Floor1# copy running-config startup-config
```
#### Kiểm tra trạng thái thiết bị
Sử dụng các lệnh `show` trong chế độ `Priviledged EXEC` xác thực cấu hhình:
- `show running-config`: Xem cấu hình đang chạy hiện tại
- `show ip interface brief`: Kiểm tra trạng thái IP và tình trạng `Up/Down` của các cổng
- `show version`: Xem thông tin phàn cứng và hệ điều hành
### Exercises

1. Truy cập vào thiết bị (giả lập trên Packet Tracer hoặc GNS3), thực hiện đổi hostname thành "Core-Switch" và đặt mật khẩu privileged là "Secret123".
![[Pasted image 20260315200217.png]]
2. Cấu hình một IP quản lý là 10.0.0.5/24 cho VLAN 1, đảm bảo interface đã được bật (no shutdown).
![[Pasted image 20260315200539.png]]
- `10.0.0.5` → IP quản lý của switch
    
- `255.255.255.0` → Subnet mask tương ứng với `/24`
```
no shutdown
```
Nếu không bật, interface sẽ ở trạng thái **administratively down**.
Lưu và thoát cấu hình
```
end
write memory
```
hoặc 
```
copy running-config startup-config
```
![[Pasted image 20260315202640.png]]
![[Pasted image 20260315202704.png]]
Thực hiện gắn 1 con PC vào và cấu hình IP tĩnh cho PC đó cùng lớp với Switch sau đó thực hiện lấy PC đó ping thì sẽ thấy được Switch
Cấu hình Switch Cisco dựa trên tư duy phân cấp: từ việc truy cập cơ bản đến quyền quản trị cao nhất, và cuối cùng là đi sâu vào các cấu hình cụ thể cho từng cổng. Việc tuân thủ quy trình `copy running-config startup-config` là bước sống còn để đảm bảo cấu hình tồn tại sau khi khởi động lại. Đây là nền tảng để bạn tiếp tục sang các cấu hình phức tạp hơn về VLAN và giao thức kết nối mạng trong các phần sau.
![[Pasted image 20260316090728.png]]
![[Pasted image 20260316091119.png]]
![[Pasted image 20260316091432.png]]
![[Pasted image 20260316092127.png]]
![[Pasted image 20260316093236.png]]
![[Pasted image 20260316093534.png]]
![[Pasted image 20260316094623.png]]
![[Pasted image 20260316094819.png]]
![[Pasted image 20260316095410.png]]
![[Pasted image 20260316100016.png]]
