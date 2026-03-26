Terminal là giao diện dòng lệnh (Command Line Interface - CLI), nơi bạn giao tiếp trực tiếp với hệ điều hành thông qua các lệnh văn bản thay vì sử dụng chuột và giao diện đồ họa (GUI). Trong Linux, Terminal không chỉ là công cụ điều khiển; nó là trung tâm quyền năng nhất của hệ thống, cho phép bạn thực hiện mọi tác vụ quản trị với độ chính xác và tốc độ cao.
#### Cấu trúc một câu lệnh cơ bản
Mọi câu lệnh trong Linux thường tuân theo cú pháp: `command [options] [arguments]`
`Command`: tên chương trình muốn thực thi `ls, cd, pwd`
`OPtions`: Các tham số điều chỉnh hành vi của lệnh, thường bắt đầu bằng dấu gạch ngang `-` cho dạng viết tắt hoặc hai dấu gạch ngang `--` cho tên đầy đủ
- Arguments: đối tượng mà lệnh sẽ tác động lên ví dụ như `tên file` `tên thư mục` `hoặc địa chỉ IP`
Ví dụ: `ls -l /home`
`ls`: list liệt kê nội dung thư mục
`-l`: là option hiển thị chi tiết (long listing)
`/home`: là arguments chỉ định vị trí cần liệt kê

#### Các lệnh điều hướng và xác định vị trí
Trước khi thao tác với dữ liệu, ban phải biết mình đang đứng ở đâu và di chuyển đến đâu
- `pwd`(Print Working Directory): Hiển thị đường dẫn đầy đủ của thư mục hiện tại. Đây là lệnh đầu tiên bạn nên gõ nếu cảm thấy lạc trong hệ thống file
- `cd (change directory)`:  Lệnh thay đổi thư mục làm việc
	- `cd /etc`: di chuyển vào thư mục `etc`
	- `cd ..`: di chuyển ngược lại thư mục cha
	- `cd ~`:  di chuyển nhanh về thư mục home
	- `cd -`: quay lại thư mục vừa đứng trước đó
`ls(list)`: hiển thị danh sách file và thư mục:
	- `ls -a`: hiển thi jcacs file ẩn file có dấu `.` ở đầu tên
	- `ls -lh`: hiển thị định dạng dài `-l` và kích thước ở dạng dễ đọc `-h` human readable ví dụ như KB, MB thay vì byte
#### Lệnh hỗ trợ và quản lý thông tin lệnh
Khi bạn không nhớ chính xác cứ pháp hoặc muốn tìm hiểu sâu về một công cụ, hệk thống cung cấp các tìa liẹu sẵn:
- `man(manual pages)`: đây là cuốn từ điển cua Linux . Gõ `man [tên lệnh]` để xem hướng dẫn chi tiết cách dùng, các options và ví dụ
- `history`: xem lại danh sách các lệnh ban đã từng gõ trong phiên làm việc hiện tại, Ban có thẻ sử dunhg lại lệnh cũ bằng cách gõ `!n` với `n` là số thức tự lênh hiển thị trong `history`
- clear: làm sạch màn hình Terminal, giúp abnj có không gian làm viẹc mà không làm mất lịch sử các lênhj chạy
![[Pasted image 20260322101440.png]]
![[Pasted image 20260322101504.png]]
![[Pasted image 20260322101518.png]]
![[Pasted image 20260322101532.png]]
#### Các lệnh xem thông tin hệ thống
Đôi khi ta cần biết nhanh trạng thái thông mà khong cần các công cụ quản lý chuyên sâu
`date`: hiển thi jthowif gian hệ thống
`whoami`: cho biết bạn đang đăng nhập dới ngườidugnf nào
`hostname`: hiển thi jteen máy chủ trong mạng
`uptime`: xem hệ thóng đã chạy được bao lâu kể từ lần cuối đăng nhập