Hệ thống file Linux được tổ chức theo cấu trúc cây(`hierarchical tree`), bắt đầu từ thư mục gốc `/`. Mọi tài nguyên, từ đĩa cứng, thiết bị ngoại vi cho đén các tiến trình chạy trong bộ nhớ, đều được biểu diễn dứo dnajg file hoặc thư mục, hiểu các hddieuf hướng thao tác với cấu trúc này là kỹ thuật sống còn
#### Cấu trúc cây thư mục (Filesystem Hierarchy Standard - FHS)
Linux tuân thủ nghiêm ngặt tiêu chuẩn FHS để đảm bảo tính đồng nhất giữa các bản phân phối, Dưới đây là các vị trí quan trọng cần nắm vứng:
- `/`: Thư mục gốc, điểm bắt đầu của toàn bộ hệ thống
- `/bin` và `/usr/bin`: chứa các lệnh nhị phân thực thi cơ bản cho mọi người dùng như `ls`, `cp`, `mv`)
- `/etc`: chưacs các file cấu hình hệ thống. Đây là nơi bạn sẽ chỉnh sửa khi muốn thay đổi hành vi của các dịch vụ
- `/home`: nơi lưu trữ dữ liệu các nhân của người dùng (ví dụ: `/home/user`)
- `/var`: chứa các dữ liệu thay dổi thường xuyên, điển hình là log hệ thống `/'var/log` hoặc dữ liệu web `var/www`
- `/root`: thư mục các nhân  của người dùng quản trị `root`
![[Pasted image 20260322102534.png]]
## Điều hướng trong hệ thống file

Việc điều hướng yêu cầu bạn hiểu rõ khái niệm đường dẫn tuyệt đối (absolute path) và đường dẫn tương đối (relative path). Đường dẫn tuyệt đối luôn bắt đầu từ `/` (ví dụ: `/etc/ssh/sshd_config`), trong khi đường dẫn tương đối bắt đầu từ vị trí làm việc hiện tại (current working directory).

- `pwd` (Print Working Directory): Hiển thị đường dẫn đầy đủ của vị trí hiện tại.
- `cd` (Change Directory): Di chuyển giữa các thư mục.
    - `cd ~`: Quay về thư mục home của người dùng hiện tại.
    - `cd ..`: Di chuyển lên thư mục cha.
    - `cd -`: Quay lại thư mục bạn vừa ở trước đó.
- `ls` (List): Liệt kê nội dung thư mục.
    - `ls -l`: Hiển thị chi tiết quyền hạn, chủ sở hữu và kích thước.
    - `ls -a`: Hiển thị cả các file ẩn (tên bắt đầu bằng dấu chấm `.`).
#### Thao tác với File và Thư mục
Để quản lý dữ liệu, bạn thực hiện cac thao tác `CRUD` thông qua các lệnh sau:
##### Create and Delete
- `touch <filename>`: tạo một file rỗng hoặc cập nhật thời gian treuy cập sửa đổi file hiện có
- `mkdir <dirname>`: tạo thư mục mới, dùng tùy chọn `-p` để tạo cấu trúc thư mục lồng nhau ví dụ `mkdir -p project/src/main`
- `rm <filename>`: xóa file
- `rmdir <dirname>`: xóa thư mục rỗng
- `rm -rf <dirname>: xóa đệ quy một thư mục và toàn bộ nọi dung bên trong nó. Cảnh báo: Đây là lệnh cựckyf nguyển nếu gõ nhầm`
##### Copy and Move
- `cp <src> <des>`: Sao chép file hoặc thư mục. Để sao chép thư mục hãy sử dụng `cp -r`
- `mv <src> <des>`: di chuyển file hoặc thu mục, lệnh này cũng dược dùng để đổi tên file ví dụ `mv old_name.txt new_name.txt`
##### Read file
Thay vì mở toàn bộ file bằng sạon thảo, hãy sử dụng công cụ đọc nhanh:
- `cat`: In toàn bọ nội dung file ra màn hình (chỉ dùng cho file nhỏ)
- `less`: cho phép cuộn trang để đọc file lớn, tìm kiếm nọi dùng bằng phím `/`
- `head` / `tail`: xem 10 dòng đầu hoặc 10 dòng cuối. `tail -f` là công cụ cực kỳ hữu ích để theo dõi log hệ thóng theo thời gian thực
![[Pasted image 20260322104327.png]]
1. Tạo cấu trúc thư mục sau bằng một lệnh duy nhất: `/tmp/lpi/module1/practice`.
2. Chuyển vào thư mục `practice`, tạo 5 file trống có tên từ `file1.txt` đến `file5.txt`.
3. Sao chép tất cả các file có đuôi `.txt` vào thư mục `lpi`.
```
mv * .txt ./src/...
```
1. Đổi tên `file1.txt` thành `config.conf` và xóa toàn bộ thư mục `module1`.
![[Pasted image 20260322105619.png]]
![[Pasted image 20260322105816.png]]
### Quản lý các tiến trình đang chạy (ps, top, htop, kill)
Một tiến trình process trong linux đơn giản lalf một thực thể đang hcayj của một chương trình .,Khi bạn khởi đọng hệ thống, hạt nhân kernel khởi tạo các tiến trình ,và mỗi tiến trình được đinh danh bằn một số nguyên duy nhất gọi là PID. Hiểu cách kiểm saots ác tiến trình này là kỹ năng ốn còn để duy trì sự ổn định của hệ thống
#### Kiẻm tra trnjag thái tiến trình với ps
Lênh `ps` (process status) cung cấp cái nhìn `tĩnh` vè các tiến trình tại thời điểm thực thi. Thay vì dùng `ps` đơn thuần, hãy tập thoi quen sử dụng các tùy chọn `aux` để có cái nhìn toàn diện:
- `a`: hiển thị tất cả người dùng (bao gồm cả các tiến trình gắn với terminal)
- `u`: Hiển thị thông tin định hướng người dùng(user-oriented), cho biết ai đang chạy tiến trình đó, mức độ sử dụng CPU/RAM
- `x`: Hiển thị các tiến trnhf không gắn với terminal
```bash
ps aux | grep nginx
```
Các cột cần quan tâm
`STAT`: trạng thái(R, S, Z)
#### Giám sát thười gian thực với top và htop
Nếu `ps` là một bức ảnh hucpj nhanh thì `top` và `htop` là những thước phim
`top` được cài sẵn trên mọi bản phân phối. Khi chạy `top`, bạn thấy một bảng đièu khiẻn cập nhạt liên tục các tìa nguyên hệ thống ở phía trên và danh sách các tiến trình tiêu thụ tài nguyên hiều nhất phía tưởc. Cácp hím tắt hữu ích trong `top`:
- `P`: sắp xếp theo %CPU
- `M`: Sắp xếp theo %RAM
- `k`: gửi tính hiệu kết thúc tiến trình, ta sẽ phải biết PID
- `q`: thoát chương trình
`htop` là phiên bản nâng cấp của `top` hỗ trợ giao diện màu sắc, nếu hệ thống vẫn chưa có thì tải `sudo apt install htop`
#### Kiểm soát tiến trình với kill
Khi một tiến trình bị treo hoặc hiến dụng tìa nguyên quá mức, bạn cần gửi một itnsh hiệu `signal`tới nó. Lệnh `kill` không chỉ đơn thuần là giết, nó là công cụ gửi tín hiệu
Các tín hiệu quan tọng nhất:
- `SIGTERM (15)`: Mặc định. Tín hiệu lịch sự, hêu cầu tiến trình tự dọn dẹp và đóng lại
### Giám sát tài nguyên hệ thống CPU, RAM, Disk, I/O

![[Pasted image 20260323102932.png]]
Để đảm bảo hệ thống hoạt động ổn định dưới tải trọng thì cần giám sát theo dõi tìa nguyên hệ thống. Khi máy chủ chậm lại, `vấn đề không bao giờ là ngẫu nhiên`, nó nằm ở sự tranh chấp tài nguyên giữa `CPU, RAM, hoặc đọc I/O`
