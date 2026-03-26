## Lớp 7: Ứng dụng (Application)

Đây là lớp tương tác tực tiếp với phàn mềm người dùng. Nó không phải là ứng dung bạn đang dùng (như Chrome hay Outlook) mà là `Các giao thức` cho phép ứng dụng đó giao tiếp với mạng

Ví dụ: HTTP/HTTPS(duyệt web), FTP(truyền file), SMTP(gửi email)
`Vai trò`: Chuyển đổi dữ liệu từ ứng dụng thành định dạng mà mạng có thể hiểu được
## Lớp 6: Trình bày (Presentation)

Lớp này đóng vai trò là "bộ thông dịch". Nó đảm bảo rằng dữ liệu gửi đi ở  một định dạng mà hệ thống nhận có thể đọc được. Các công việc chính bao gồm:
- Mã hóa/Giải mã: Chuyển đổi dữ liệu(ví dụ: ASCII sang EBCDIC)
- Nén dữ liệu: Giảm kích thước tệp để truyền tải nhanh hơn
- Bỏa mật: Mã hóa dữ liệu(SSL/TLS)
## Lớp 5: Phiên (Session)
Lớp phiên chịu trách nhiệm thiết lập, quản lý và kết thúc các "cuộc hội thoại" session giưuax các ứng dụng trên hai thiết bị khác nhau. Nếu kết nối bị ngắt giữa chừng, lớp này giúp khôi phục phiên làm việc mà không cần bắt đầu lại từ đầu.
## Lớp 4: Truyền tải (Transport)
Đây là lớp quyết định cách thức truyền dữ liệu: đảm bảo độ tin cậy hoặc ưu tiên tốc độ
- `TCP(Transmission Control Protocol)`: hướng kết nối, đảm bảo dữ liệu đến nơi an toàn, đúng thứ tự(sử dụng cho web, email)
- `UDP(User Datagram Protocol)`: Không hướng kết nối, tập trung vào tốc độ, chấp nhan mất mát dữ liệu (sử dụng cho stream vidoe, game online)
- `Đơn vị dữ liệu(PDU)`: Segment(Phân đoạn)
## Lớp 3: Mạng (Network)
Lớp này quyết định dường đi của dữ liệu từ nguồn đến đích thônng qua các `Router`. Tại đây, dữ liệu được đóng gói với địa chỉ IP nguồn và đích.
- `Chức năng`: Định tuyến(Routing) và gán địa chỉ logic(IP Addressing)
- `Thiết bị`: `Router`, `Layer 3 Switch`
- `Đơn vị dữ liệu (PDU)`: `Packet(gói tin)`
## Lớp 2: Liên kết dữ liệu (Data Link)
Lớp này đảm nhận việc truyền dữ liệu giữa hai thiết bị nằm cùng trong một mạng vật lý. Nó sử dụng địa chỉ vật lý `MAC Address` để định dang thiết bị

- `Chức năng`: kiểm soát truy cập môi trường truyền dẫn, phát hiện lỗi ở lớp vật lý
- `Thiết bị` : Switch, Bridge
- `Đơn vị tình PDU`: `Frame(Khung)`
## Lớp 1: Vật lý (Physical)
Là tầng dưới cùng, bao gồm các phương tiện truyền dãn vật lý như cáp đồng, cáp quang, hoặc sóng vô tuyến. Lớp này truyền các bit (0 và 1) dưới dạng tín hiệu điện, ánh  sáng hoặc sóng từ
```js
Lớp 7: Ứng dụng
Lớp 6: Trình bày
Lớp 5: Phiên
Lớp 4: Truyền tải - Segment
Lớp 3: Mạng - Packet
Lớp 2: Liên kết dữ liệu - Frame
Lớp 1: Vật lý - Bit
```
## Quá trình đóng gói dữ liệu (Encapsulation)
Khi bạn gửi dữ liệu, thông tin sẽ được đóng gói từ Lớp 7 xuống Lớp 1. Tại mỗi lớp, một phần thông tin điều khiển  `Header` được thêm vào dữ liệu gốc `Payload`

| **Lớp**   | **Đơn vị dữ liệu** | **Chức năng chính**               |
| :-------- | ------------------ | --------------------------------- |
| ==7,6,5== | Data               | Định dạng và quản lý dữ liệu      |
| ==4==     | Segment            | Đmar bảo truyền tải TCP/UDP       |
| ==3==     | Packet             | Định tuyến(IP Addrressing)        |
| ==2==     | Frame              | Địa chỉ MAC và kiểm soát truy cập |
| ==1==     | Bit                | Truyền tín hiệu vật lý            |
Mô hình OSI giúp chúng ta "phân lớp" sự cố. Khi mạng gặp lỗi, kỹ sư mạng sẽ kiểm tra từ Lớp 1 trở lên: Kiểm tra cáp (Lớp 1), kiểm tra kết nối Switch (Lớp 2), kiểm tra cấu hình IP (Lớp 3), cho đến các dịch vụ phần mềm (Lớp 7). Việc nắm vững 7 lớp này là chìa khóa để xử lý sự cố chuyên nghiệp trong các module tiếp theo về định tuyến và chuyển mạch.

## Mô hình TCP IP: Lớp truy cập mạng , Internet, truyền tải, ứng dụng

### Cấu trúc 4 lớp của TPC/IP

### 1. Lớp Ứng dụng (Application Layer)

Đây là lớp tương tác trực tiếp với người dùng và các phần mềm ứng dụng như trình duyệt web, phần mềm email. Lớp này cung cấp các giao thức để dữ liệu có thể được xử lý bởi ứng dụng.

- **Giao thức tiêu biểu**: HTTP/HTTPS (Web), SMTP/IMAP (Email), FTP (Truyền file), DNS (Phân giải tên miền).
- **Chức năng**: Chuyển đổi dữ liệu từ ứng dụng thành các định dạng giao thức mạng.
### 2. Lớp Truyền tải (Transport Layer)

Lớp này chịu trách nhiệm thiết lập kênh truyền thông giữa hai máy chủ. Nó quyết định dữ liệu được gửi đi như thế nào: có kiểm soát lỗi hay không, có đảm bảo thứ tự hay không.

- **TCP (Transmission Control Protocol)**: Cung cấp kết nối tin cậy, có xác nhận (acknowledgment), kiểm tra lỗi và sắp xếp lại gói tin. Dùng cho web, email, truyền file.
- **UDP (User Datagram Protocol)**: Truyền nhanh nhưng không đảm bảo, không có xác nhận. Dùng cho video streaming, VoIP hoặc chơi game trực tuyến nơi tốc độ quan trọng hơn độ chính xác tuyệt đối.
### 3. Lớp Internet (Internet Layer)

Nhiệm vụ cốt lõi là định tuyến (routing). Lớp này xử lý việc đóng gói dữ liệu vào các gói tin (packet) và quyết định đường đi tốt nhất để các gói tin này đến đích dựa trên địa chỉ IP.

- **Giao thức tiêu biểu**: IP (IPv4, IPv6), ICMP (dùng cho lệnh `ping`), ARP (ánh xạ IP sang MAC).
- **Chức năng**: Định vị thiết bị trên mạng toàn cầu thông qua địa chỉ logic.
### 4. Lớp Truy cập mạng (Network Access Layer)

Đây là lớp thấp nhất, định nghĩa cách dữ liệu được truyền qua các phương tiện vật lý như cáp đồng, cáp quang hoặc sóng không dây. Nó xử lý việc chuyển đổi gói tin thành các frame và truyền qua địa chỉ vật lý (MAC address).

- **Công nghệ**: Ethernet, Wi-Fi (802.11).
- **Chức năng**: Giao tiếp trực tiếp với phần cứng, điều khiển truy cập vào đường truyền vật lý.
