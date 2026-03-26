Địa chỉ IPv4 là một chuỗi nhị phân 32-bit được sử dụng để định danh duy nhất cho một thiết bị mạng. Để con người dễ đọc và quản lý, 32 bit được chia thành 4 nhóm, mỗi nhóm 4 bit(gọi là 1 octo), được ngăn cách bởi dấu chấm và biểu diễn dưới dnajg thập phân.

### Cấu trúc 32-bit và Chuyển đổi

Mỗi địa chỉ IP như `192.168.1.1` thực chất là `11000000.10101000.00000001.00000001`
Mỗi `octet` mang giá trị từ 0-255 giá trị (2^8 = 256 giá trị). Cấu trúc này không chỉ định dang thiết bị mà còn chia địa chỉ thành `hai phần`: `Network ID(địa chỉ mạng)` và `Host ID(địa chỉ máy trạm trong mạng đó)` . Ranh giới giưuax hai phần này được đỉnh nghĩa bởi `Subnet mask`
#### Phân lớp địa chỉ IPv4(Classful Addressing)
Trong lịch sử phát triển, IPv4 được chia thành ác lớp (A,B,C,D,E) dựa trên bit đầu tiên  của dịa chỉ. VBieejc phân lớp giúp các `router` đời đầu xác định nhanh chóng phần mạng và phần host mà không cần subnet mask phức tạp![[Pasted image 20260316104443.png]]

|Lớp|Phạm vi Octet đầu tiên|Mục đích|
|---|---|---|
|**A**|1 - 126|Mạng cực lớn (ví dụ: ISP quốc tế)|
|**B**|128 - 191|Mạng trung bình (doanh nghiệp lớn)|
|**C**|192 - 223|Mạng nhỏ (văn phòng, gia đình)|
|**D**|224 - 239|Dành riêng cho Multicast|
|**E**|240 - 255|Dành cho thử nghiệm và nghiên cứu|
_Lưu ý: Địa chỉ bắt đầu bằng 127 được dành riêng cho Loopback (127.0.0.1 dùng để kiểm tra card mạng nội bộ)._
#### Phân biệt địa chỉ Public và Private
Trong thực tế, bạn không dùng tùy tiện mọi địa chỉ trong các dải trên. IPv4 được chia thành hai loại chính:
1. `Public IP`: Được quản lý bỏi `IANA` và các tổ chức khu vực. Các địa chỉ này phải là `duy nhất` trên toàn cầu và được `định tuyến trên Internet` 
2. `Private IP` : Dành cho mạng nội bộ, không thể định tuyến trực tiếp lên Internet. Các dãy này bao gồm:
    - Lớp A: `10.0.0.0` - `10.255.255.255`
    - Lớp B: `172.16.0.0` - `172.31.255.255`
    - Lớp C: `192.168.0.0` - `192.168.255.255`
Sự tách biệt này cực kỳ quan trọng; các thiết bị trong nhà bạn dùng `Private IP`, sau đó thông qua `Router` thực hiện `NAT`(Network Address Translation) để `biến đổi` thành `Public IP` khi đưa ra ngoài Internet
![[Pasted image 20260316104309.png]]
#### Các trường hợp đặc biệt cần lưu ý
- `Network Address`: ĐỊa chỉ đầu tiên trong một dải mạng ví dụ `191.168.1.0` dùng để đại diện cho chính mạng đó, không gán được cho thiết bị
- `Broadcast Address`: Địa chỉ cuối cùng trong dải ví dụ `192,168,1,255`, dùng để gửi tin đến tất cả các thiết bị trong cùng một phân đoạn mạng
- `Default Gateway`: Địa chỉ của `Router` mà thiết bị sẽ gửi dữ liệu đến `nếu đích nằm ngoài mạng nội bộ`
Cấu trúc địa chỉ IPv4 là nền tảng của mọi giao tiếp trên Internet. Bạn cần nắm vững sự khác biệt giữa Network ID và Host ID, cũng như cách phân biệt giữa dải Public và Private. Đây là bước đệm bắt buộc để thực hiện các kỹ thuật phức tạp hơn như Subnetting và NAT trong các phần tiếp theo.
![[Pasted image 20260316105111.png]]
![[Pasted image 20260316105300.png]]
![[Pasted image 20260316105553.png]]
![[Pasted image 20260316105717.png]]
![[Pasted image 20260316105810.png]]
![[Pasted image 20260316105901.png]]
![[Pasted image 20260316112612.png]]
![[Pasted image 20260316134418.png]]
![[Pasted image 20260316140949.png]]
### Phân chia mạng con(Subnetting) IPv4 chi tiết

Phân chia mạng con Subnetting là quá trình mượn các bit từ phần `Host` của địa chỉ `IPv4` để chia một mạng lớn thành các phân đoạn nhỏ hơn, giúp tối ưu hóa viẹc quản lý và giảm thiểu lưu lượng quảng bá(broadcast traffic)
#### Cơ chế mượn bit và Subnet Mask
Mỗi địa chỉ IPv4 32-bit bao gồm hai phần: `Network ID` và `Host ID`. Khi bạn cần chia mạng, bạn thay đổi `Subnet Mask` bằng cách chuyển các bit từ `Host ID` sang `Network ID`. Việc này được biểu diễn thông qua ký hiệu `CIDR(Classless Inter-Domain Routing)`, ví dụ `/24` nghĩa là 24 bit đầu tiên dành cho mạng. 
`Khi ta mượn n bit từ phần Host thì ta sẽ có 2^n mạng con mới` . Mỗi mạng con này sẽ có số lượng `Host khả dụng là 2^h -2` (với h là số bit còn lại của phần Host), phải trừ đi 2 địa chỉ : địa chỉ `Network Address` và địa chỉ `Broadcast Address` 
Ví dụ, với dải mạng: `192.168.1.0/24` 
- `Subnet Mask mặc định`: `255.255.255.0`
- Nếu mượn 2 bit: Subnet Mask trở thành: `255.255.255.192` hay (`/26`)
- Số mạng con tạo ra: `2^2`  = 4 mạng
- Số host mỗi mạng: `2^(32-26) -2 = 2^(6) - 2 = 62 host`
![[Pasted image 20260316143846.png]]
![[Pasted image 20260316143902.png]]
![[Pasted image 20260316143928.png]]
![[Pasted image 20260316144020.png]]
#### Các bước tính toán Subnetting chi tiết
Tuân thủ các bước:
1. `Xác định yêu cầu`: Cần bao nhiêu mạng con và bao nhiêu host trên mỗi mạng?
2. `Tìm số bit cần mượn`: Sử dụng công thức `2^n >= số mạng yêu cầu`
3. `Xác định Subnet Mask mới`: cộng số bit đã mượn vào phần `Network hiện tại`
4. `Tính bước nhảy (Magic Number)`: Xác định giá trị tăng dần của dãy mạng con. Magic Number được tính bằng cách lấy `256` trừ đi giá trị của `octet` chứa bit mượn cuối cùng trong `Subnet mask`
**Ví dụ thực tế:** Cần chia mạng `172.16.0.0/16` thành các mạng con, mỗi mạng cần tối thiểu 1000 host.

- Yêu cầu host: 2h−2≥1000⇒2h≥1002⇒h=102h−2≥1000⇒2h≥1002⇒h=10.
- Vì tổng là 32 bit, số bit cho Network còn lại: 32−10=2232−10=22.
- Subnet Mask mới: `/22` (tương đương `255.255.252.0`).
- Bước nhảy tại octet thứ 3: 256−252=4256−252=4.
- Các mạng con sẽ là: `172.16.0.0/22`, `172.16.4.0/22`, `172.16.8.0/22`, v.v.
Cách nhìn phát biết ngay (mẹo CCNA)
`/22` là nằm ở `octet thứ 3` từ ngoài vào sẽ tổng là 24 bit
24-22 = 2
2^2 = 4 => Magic Number
Mask = 256 − 2^(8 − số bit network) => octet 3
#### Variable Length Subnet Masking(VLSM)
Trong thực tế thì không phải lúc nào các mạng cũng cần số lươnjg host bằng nhau. VLSM cho phép bạn chia mạng con thành các mạng có kích thước khác nhau trong cùng một dải IP gốc, tránh lãng phí địa chỉ.
> ***Quy tắt quan trọng nhất của VLSM là luôn chia mạng cho các phận đoạn lớn nhất trước*** 

| Yêu cầu Host                   | CIDR | Subnet Mask     | Số IP khả dụng |
| ------------------------------ | ---- | --------------- | -------------- |
| 2 host (kết nối router-router) | /30  | 255.255.255.252 | 2              |
| 30 host                        | /27  | 255.255.255.224 | 30             |
| 62 host                        | /26  | 255.255.255.192 | 62             |
| 126 host                       | /25  | 255.255.255.128 | 126            |
![[Pasted image 20260316153937.png]]
![[Pasted image 20260316154115.png]]
1. Chia dải mạng `192.168.10.0/24` thành 4 mạng con đều nhau. Xác định Subnet Mask, dải IP và Broadcast của mạng con thứ 3.
	4 mạng => 2^n >=4 => n = 2
	Mượn thêm 2 bit bên Host
	Suy ra `/26`
	Block size: `256 - 2^(32-26) = 64`
	Subnet nhảy `0, 64, 128, 192`
#### Công thức tính Subnet Mask
B1. Xác định octet chứa Subnet
`/22`
```
octet = floor(22/8) + 1 = 3 => Octet 3
```
B2. Sôt bit network trong octet đó
```
n = 22 mod 8 = 6
```
B3. Subnet mask của octet 
```
Mask_octet = 256 - 2^(8-6) = 252
```

Ví dụ như `/26`
26 mod 8 = 2
Mask _octet = 256 - 2^(8-2) = 192
#### Tổng quát nhất
```
Mask_octen = 256 - 2^(8-(CIDR mod 8))
```
CIDR là /n
Block size (Magic number)
```
2^(8-(CIDR mod 8))
```
Công thức tổng quát của Host
```
Host = 2^(32-CIDR) -2
```
#### Exercise
1. `Chia dải mạng `192.168.10.0/24` thành 4 mạng con đều nhau. Xác định Subnet Mask, dải IP và Broadcast của mạng con thứ 3.`
4 mạng bằng nhau => 2^n >=4 => n =2 
Mượn thêm 2 bit bên Host 
`/26` => octet 4
mask_octet = 256 - 2^(8 - (CIDR mod 8)) = 256 - 2^(8-(26 mod 8)) = 192
=>Subnet mask:  255.255.255.192
Block size: 2^(8-(CIDR mod 8)) = 64 
=> Subnetting 1: 192.168.10.0/26
Subnetting 2: 192.168.10.64/26
Subnetting 3: 192.168.10.128/26
Broadcast: 192.168.10.191/26 
Host range: 129-190
Subnetting 4: 192.168.10.192/26
2.` Với dải mạng `10.0.0.0/8`, hãy thiết kế VLSM cho: 1 mạng 500 host, 1 mạng 200 host và 2 mạng 50 host. Tính Subnet Mask cho từng trường hợp.`
Sắp xếp từ lớn đến bé
B1: Sắp xếp từ lớn đến bé
![[Pasted image 20260317074319.png]]
B2. Tìm số IP cần cấp
```
IP_Cần = Host +2
```
Vì +2 cho Broadcast và Network
![[Pasted image 20260317074525.png]]
B3: Tìm lũy thừa 2 gần nhất
```
2^n >= Host + 2
```
![[Pasted image 20260317074959.png]]
B4: Tìm Prefix
A:
$2^n \ge 500 + 2$  => $n \ge 9$ 
$Host \ge 9 => Network = 23$
$Subnetmask = 255.255.254.0$
$Block size(Magic number) = 256 - 254 = 2$ tại octet thứ 3
Tức là 
$Host range: 10.0.0.1 ---> 10.0.1.254$
$Broadcast = 10.0.1.255$
$Host khả dụng: 2^{Host} -2 = 510$ 
Mà số `IP đã nhảy tương ứng với mỗi block là: 512IP`
B: 
$2^n \ge 200 + 2 => n \ge 8$
$Subnet mask = 255.255.255.0$
$Blocksize = 1 = 256IP$
$Host range: 10.0.2.1 ---> 10.0.2.254$
$Broadcast: 10.0.2.255$
Tương tự cho còn lại,....
### Địa chỉ IPv6: Cấu trúc và các loại địa chỉ

IPv6(Internet Protocol version 6) là giải pháp kiến trúc thay thế cho IPv4 được thiết kế để khắc phục triệt để sự cạn kiệt không gian địa chỉ toàn cầu bằng cách mở rộng chiều dài địa địa chỉ từ 32-bit len 128-bit. Thay vì ký hiệu thâp phân tách bằng dấy chấm như IPv4, IPv6 sử dụng hệ thập lục phần phân cách bằng dấu 2 chấm
#### Cấu trúc địa chỉ IPv6
Một địa chỉ IPv6 gồm 128 bit, được chia thành 8 nhóm, mỗi nhóm 16bit. Mỗi nhóm được biểu diễn bằng 4 chữ số thập lục
Ví dụ: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`
Để làm việc với các địa chỉ dài này hiệu quả, hệ thống sử dụng hai quy tắc nén:
1. Loại bỏ số 0 dẫn đầu: ví dụ `0db8` thành `db8`
2. Nén chuỗi 0 liên tiếp: `0000` thành `::` quy tắc này chỉ được sử dụng 1 lần duy nhất trong 1 địa chỉ để tránh gây nhập nhằng cho bộ định tuyến
Ví dụ nén: `2001:db8:85a3:0:0:8a2e:370:7334` trở thành `2001:db8:85a3::8a2e:370:7334`
#### Các loại IPv6
Khác với IPv4, IPv6 sử dụng Broadcast. Thay vào đó, nó phân laoij địa chỉ dựa trên phạm vi mvaf mục đích giao tiếp
1. Unicast
Định danh duy nhất cho 1 giao diện mạng. Gói tin gửi tới địa chỉ Unicast sẽ được gửi đến đúng giao diện đó
- Global Unicast Address(GUA): Tương tự IP Public trong IPv4, có thể được định tuyến trên toàn cầu bắt đầu bằng `2000::/3`
- Link-Local Address: Địa chỉ bắt buộc phải có trên mọi giao diện IPv6, dùng để giao tiếp trong cùng 1 LAN. Luôn bắt đầu bằng `fe80::/10`
- Loopback Address: `::1` tương đương với `127.0.0.1` trong IPv412
1. Multicast
Địa chỉ Multicast được dử dụng để gửi một gói tin đến một nhóm các giao diện thường là các thiết bị cùng chạy một giao thưcd định tuyến. Địa chỉ Multicast luôn bắt đầu bằng tiền tố `ff00::/8`
2. Anycast
Đây là một địa chỉ được gán cho nhièu giao diện thường trên các thiét bị khác nhau. Khi gửi gói tin đến địa chỉ Anycast mạng sẽ định tuyến gói tin đó đến giao diện "gần nhất" dựa trên số liêu jcuar giao thức định tuyến

![[Pasted image 20260317085739.png]]
![[Pasted image 20260317085914.png]]
![[Pasted image 20260317090011.png]]
![[Pasted image 20260317090048.png]]
![[Pasted image 20260317090208.png]]
![[Pasted image 20260317090311.png]]
![[Pasted image 20260317090356.png]]
![[Pasted image 20260317090451.png]]
![[Pasted image 20260317090533.png]]
![[Pasted image 20260317090701.png]]
![[Pasted image 20260317090743.png]]
![[Pasted image 20260317090820.png]]
### Thực hành Subnetting IPv4 và cấu hình IP trên thiết bị

Subnetting là quá trình chia mộtdiar địa chỉ mạng lớn thành các mạng con nhỏ hơn để tối ưu việc quản lý tài nguyên tăng cường bảo mật. Thay vì sử dụng một dải địa chỉ dư thừa cho một phân đoạn mạng, bạn sử dụng subnet mask để xác định rõ phần nào của địa chỉ `Network ID` và phàn nào của `Host ID`
#### Cơ chế chia mạng con(Subnetting)
Một địa chỉ IPv4 gồm 32 bit, được chia thành phần mạng và phần máy dựa trên `Subnet Mask`. Việc mượn bit từ phần `Host` để tạo ra các mạng con `Subnet` chính là cốt lõi của `Subnetting`
Khi ta mượn `n` bit từ phần `Host`, ta sẽ tạo được $2^n$ mạng con mới. Số lượng host khả dụng trên mỗi mạng con được tính theo công thức $2^{32-m}-2$ trong đó m là tổng số bit của phần Network bao gồm cả các bit đã mượn
>> Lư ý: Ta luôn phải trừ đi 2 địa chỉ địa chỉ Network Address và địa chỉ quảng bá Broadcast Address

#### Ví dụ thực tế: Chia mạng `192.168.1.0/24`
Chia thành 4 mạng con 
1. Bạn cần mượn 2 bit từ phần Host (22=422=4).
2. Subnet mask mới sẽ là /26 (24 + 2). Chuyển sang dạng thập phân: 255.255.255.192.
3. Mỗi mạng con sẽ có 64 địa chỉ (256/4 = 64).
![[Pasted image 20260317093453.png]]
![[Pasted image 20260317093501.png]]
#### Cấu hình IP trên thiết bị Cisco
Trên thiế bị Cisco (Router/Switch Layer 3) việc gán địa chỉ IP được thực hiện trực tiếp trên cổng giao tiếp(interface). Không chỉ gán địa chỉ mà còn đảm bảo cổng ở trạng thái "no shutdown"
![[Pasted image 20260317104827.png]]
![[Pasted image 20260317105044.png]]
Cùng subnet cùng mạng thì ping thấy nhau
![[Pasted image 20260317105130.png]]
Đối với Switch Layer 2 sẽ không có IP nó quản lý thông qua MAC nên ta cần tạo VLAN 1 ảo để quản lý. Những thằng khác cắm vào cấu hình IP thì nó tự động nhận IP thôi nếu nằm trong mạng

## Giới hạn cần biết

Subnet `/24` (255.255.255.0) cho mày **254 địa chỉ** từ `.1.1` đến `.1.254`  
Cắm bao nhiêu switch, bao nhiêu AP thì thiết bị vẫn lấy địa chỉ trong dải đó

```
.1.1    → Router
.1.2    → Switch management
.1.3    → AP
.1.10   → PC
.1.20   → Printer
.1.30   → Phone WiFi
...
.1.254  → thiết bị cuối cùng
```

---

## Khi nào mới tạo ra mạng `.2.x` khác?

Khi mày dùng **VLAN** hoặc **thêm interface router** — lúc đó mới tách thành mạng riêng biệt, ví dụ:

```
VLAN 1 → 192.168.1.x  (văn phòng)
VLAN 2 → 192.168.2.x  (camera)
VLAN 3 → 192.168.3.x  (WiFi khách)
```

1. Chia mạng 172.16.0.0/16 thành các subnet sao cho mỗi subnet chứa tối đa 1000 host. Bạn cần mượn bao nhiêu bit và subnet mask mới là gì?
2. Cấu hình IP 172.16.0.1 với subnet mask tương ứng trên cổng FastEthernet0/1 của Router, sau đó thực hiện lệnh kiểm tra trạng thái cổng.
```shell
configure terminal
interface gigabitethernet 0/0/1
no shutdown
end
write memory


Router# show ip interface brief
```

3. Giải thích tại sao trong ví dụ chia mạng 192.168.1.0/26, địa chỉ đầu tiên (192.168.1.0) và cuối cùng (192.168.1.63) lại không thể gán cho máy tính.
![[Pasted image 20260320100302.png]]

Block size: 2^(8 - (28 mod 8)) = 16 (IP)
0->15
16->31
32->47
48-> ...
Nhanh hơn là lấy 100 / 16 = 6 dư 4 là bắt đầu từ block thứ 6 cộng lên
16 x 6 = 96 + 15 = 111