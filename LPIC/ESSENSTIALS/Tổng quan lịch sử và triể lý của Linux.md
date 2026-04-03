Linux là một hạt nhân kernel hệ điều hành dược pháttrieern dựa trên nguyên lý của Unix, với triết lý cốt lõi là sự tự do, minh bạch và khả năng tùy biến mạnh mẽ. Thay vì là một sản phẩm thuơgn mại khép kín, Linux tồn tại như một hệ sinh thái cộng tác toàn cầu, nơi mã nguồn mửo cho phpeps bất kỳ ai cũng cótheer kiểm tra, sữa dổi và phân phối lại

Linux không phải là một phần mềm đơn lẻ; đó là một hệ sinh thái được vận hành bởi một "trái tim" trung tâm duy nhất: **Linux Kernel**. Để hiểu cách Linux hoạt động, bạn cần nhìn nhận nó như một cấu trúc phân lớp, nơi nhân (kernel) đóng vai trò là "người phiên dịch" quyền lực nhất giữa phần cứng máy tính và mọi thứ bạn làm trên hệ thống.
#### Sự hình thành của GNU và Linux Kernel
Vào năm 1983, Richard Stallman khởi xướng dự án GNU với mục tiêu xây dựng một hệ điều hành hoàn toàn tự do (free software). Dự án này đã tạo ra hầu hết các thành phần cơ bản như trình biên dịch (GCC), thư viện hệ thống và các công cụ dòng lệnh (GNU coreutils). Tuy nhiên, GNU còn thiếu mảnh ghép cuối cùng: **Kernel** — thành phần trung tâm điều phối phần cứng và phần mềm.

Năm 1991, Linus Torvalds, một sinh viên tại Đại học Helsinki, đã công bố phiên bản đầu tiên của Linux Kernel như một dự án sở thích. Khi kết hợp các công cụ của GNU với Kernel của Linux, một hệ điều hành hoàn chỉnh đã ra đời. Sự kết hợp này chính là lý do nhiều chuyên gia gọi hệ điều hành này là GNU/Linux.
![[Pasted image 20260330080733.png]]
#### Triết lý ủa Unix và Linux
Linux kế thừa triết lý thiết kế từ Unix, tập trung vào tính đơn giản và modular. Các nguyên tắc này vẫn là "kim chỉ nam" cho mọi quản trị viên hệ thống chuyên nghiệp:
- `Mọi thứ là một File`: Trong Linux, file không chỉ là dữ liệu văn bản. Các thiế bị phần cứng(ổ cứng, bàn phím), tiến trình (process) và giao tiếp mạng đều được biểu diễn dưới dạng file. Điều này cho phép bạn sử dụng các công cụ quản lý file quen thuộc để điều khiển toàn bọ hệ thống
- `Chương trình nhỏ, làm tốt một việc`: Thay vì các ứng dụng "tất cả trong một" phức tạp, Linux khuyến khích sử dụng nhiều công cụ nhỏ, mỗi công cụ thực hiện xuất sắc một tác vụ đơn lẻ. Bạn có thể ghép các công cụ  này lại với nhau thông qua `pipes` `|` để thực hiện các xử lý phức tạp.
- `Tính cộng đồng và mã nguồn mở GPL`: Giấy phép GNU GPL đảm bảo rằng bất kỳ cải tiến nào trên Linux cũng phải được chia sẻ ngược lại cho cộng đồng. Điều này ngăn chặn việc độc quyền công nghệ và đảm bảo hệ thống luôn được cải tiến bởi hàng triệu lập trình viên trên toàn thế giới
#### Cấu trúc phân tầng của hệ thống Linux
Để hiểu cách Linux vận hành, hãy hình dung về các lớp ngăn cách giữa người dùng và phần cứng:
1. `Phần cứng`: CPU, RAM, ổ cứng
2. `Hạt nhân (Kernel)`: Lớp trung gian quan trọng nhất. Nó giao tiếp trực tiếp với phần cứng, quản lý bộ nhớ, tiến trình và driver
3. `Shell`: giao diện giữa người dùng và Kernel. Nó nhận lệnh từ người dùng (`bash`, `zsh`) và dịch chúng sang ngôn ngữ mà Kernel có thể hiểu được
4. `Ứng dụng(User sapce)`: Các trình duyệt, trình biên dịch, cơ sở dữ liệu và công  cụ quản trị hệ thống chạy ở đây
***`Key Takeawy`: Quản trị Linux thực chất là việc điều phối sự tương tác giữa các ứng dụng trong User Space thông qua Shell để yêu cầu Kernel thực hiện các thay đổi trên phàn cứng hoặc hệ thống file***

![[Pasted image 20260330090922.png]]

#### Các bản phân phối (Linux Distributions)
Vì mã nguồn của Linux là mở, bất kỳ ai cũng có thể đóng gói Kernel, các cong cụ GNU và phần mềm ứng dụng thành một `bản phân phối`(distro). Các distro khác nhau phục vụ các mục đích khá nhau
`Nhánh Debian/Ubuntu`: Phổ biến trong môi trường máy chủ và phát triển cá nhân, sử dụng hệ thống quản lý gói `apt` 
`Nhánh RHEL/CentOS/Fedora`: Tiêu chuẩn công nghêipj trong các doanh nghiệp lớn, ưu tiên tính ổn định và bảo mật, sừ dụng hệ thônngs `rpm` và `dnf/yum`
Nhánh hiêu lịch sử và triết lý không chỉ là kiến thức lý thuyết; nó giúp bạn hiểu tại sao các lệnh trong Lnyx lại được thiết kế theo các hiện tại và tại sao hệ thống này lại có khả năng chịu tải và ổn định cao hơn hẳn các hệ điều hành đóng khác
![[Pasted image 20260330091440.png]]
![[Pasted image 20260330091538.png]]
![[Pasted image 20260330091612.png]]
![[Pasted image 20260330091748.png]]
![[Pasted image 20260330092005.png]]
![[Pasted image 20260330092112.png]]
![[Pasted image 20260330092308.png]]
![[Pasted image 20260330092409.png]]
![[Pasted image 20260330092500.png]]
### Cài đặt máy ảo Ubuntu Server và thiết lập môi trường thực hành

Ảo hóa là kỹ thuật cho phép bạn chạy nhiều hệ điều hành trên cùng một phần cứng vật lý thông qua một lớp phần mềm trung gian gọi là Hypervisor. Trong môi trường Linux, chúng ta sử dụng máy ảo (Virtual Machine - VM) để tạo ra một không gian làm việc an toàn, cô lập hoàn toàn với máy tính cá nhân của bạn. Điều này đảm bảo rằng mọi thực hành, cấu hình sai lầm hay thử nghiệm phần mềm trong khóa học này đều không làm ảnh hưởng đến hệ điều hành chính (Host OS) của bạn.
#### Cấu trúc máy ảo và vai trò của Hypervisor
Hypervisor đóng vai trò là "người điều phối", phân bổ tài nguyên phần cứng (CPU, RAM, ổ cứng) từ máy chủ vật lý cho các máy ảo. Đối với việc học Linux, chúng ta sẽ sử dụng Oracle VM VirtualBox – một Type-2 Hypervisor chạy trực tiếp trên hệ điều hành của bạn.
![[Pasted image 20260330101824.png]]
![[Pasted image 20260330102012.png]]
![[Pasted image 20260330102354.png]]
![[Pasted image 20260330102829.png]]
![[Pasted image 20260330102928.png]]
![[Pasted image 20260330104542.png]]
![[Pasted image 20260330104945.png]]
### Làm quen với giao diện dòng lệnh (CLI) và cấu trúc cây thư mục (FHS)

Giao diện CLI `command line interface` là môi trường nơi bạn giao tiếp trực tiếp vớih ệ điều hành htoong qua văn bản thay vì biểu tượng đồ họa. Trong Linux, CLI không chỉ là một công cụ bổ trợ; đó là trung tâm điều khiển nơi mọi thoa tác quản trị, tự động hóa và xử lý hệ thống diễn ra.

#### Cấu trúc cây thư mục (FHS -Filesystem Hierarchy Standard)
Trong Linux, mọi thứ đều là tệp tin. Cấu trúc tệp tin được tổ chức theo mô hình cây `tree`, bắt đầu từ thư mục gốc `/` `root directory` . Tiêu chuẩn FHS quy định vị trí của các tệp tin để đảm bảo tính nhất quán giữa các bản phân phối Linux.
![[Pasted image 20260330134155.png]]
![[Pasted image 20260330142139.png]]
![[Pasted image 20260330142422.png]]

[IT@linuxserver ~]$ 
- IT: username
- linuxserver: system name
- ~: is special
- $ : user normal
pwd: `print working directory`
```bash
/linuxserver/home/IT
```
ls: `List directory`
cd: `Change directory`
ls -l: `Long listing`
cd with no arguments takes you back home
`cd ..` 
`".." means the directory above this one`
`cd .`
`"." means this directory`
ls -la: `Long list all`
`"a" display hidden file. "l" displays permision and size of files
ls -h: `show size of file human readable`
`cd ~`
`"~" means home directory`
`cd /tmp`
Absolute: starts with "/"
![[Pasted image 20260330143939.png]]
![[Pasted image 20260330144126.png]]
### Cách tìm kiếm sự trợ giúp trong Linux với Man pages và Info

`man` là manual và info là hai hệ thống tài liệu tích hợp sẵn trên mọi hệ thống Linux, cho phép bạn truy cập vào hướng dẫn kỹ thuật chi tiết của gần như mọi lệnh hoặc cấu hình mà không cần kết nối internet. Việc nắm vững cách sử dụng các công cụ này là kỹ năng quan trọng nhất để trở thành một người dùng Linux tự chủ
#### Hệ thống Man pages (manual pages)
`man` là tài liệu tham khảo tiêu chuẩn cho các lệnh Linux. Mỗi khi bạn không biết một lệnh thực hiện chức năng gì hoặc cần xem danh sách các tùy chọn `flags`, `man` là điểm dừng chân đầu tiên.
![[Pasted image 20260330145650.png]]
`Syntax` 
`man [ten_lenh]`
`man ls`
##### Cấu trúc của một Man page
Một trang `man` được chia thành các mục tiêu chuẩn:
- `NAME`: tên lệnh và mô tả ngắn gọn
- `SYNOPSIS`: cú pháp lệnh, cho thấy cách viết lệnh và các đối số bắt buộc/ tùy chọn
- `DESCRIPTION`: giải thích chi tiết về lệnh đó
- `OPTIONS`: Danh sách  các tham số điều khiển hành vi của lệnh
- `SEE ALSO`: các lệnh liên quan hoặc tệp cấu hình tương ứng
**Các phím điều hướng trong Man**
Khi ta mở một `man page`, bạn đang trong trình xem văn bản `less`. Các phím cần nhớ
- `Phím mũi tên/Enter`: Di chuyển lên xuống
- `Phím cách (Space)`: Cuộn xuống một trang
- `Phím b`: cuộn ngược lại một trang
- `Phím /`: bắt đầu tìm kiếm từ khóa (nhập từ khóa rồi nhấn Enter, sau đó nhấn `n` để tìm kết quả tiếp theo)
- `Phím q`: thoát khỏi trang `man`
##### Các Section trong Man pages
Linux phân loại tài liệu thành các `sections` được đánh số từ 1 đến 9:
1. Các lệnh người dùng (User commands)
2. Các lệnh System calls (lập trình)
3. Các thư viện C (C library function)
4. Định dạng tệp tin và quy ước (File formats, ví dụ: `/etc/passwd`)
5. Các lệnh quản trị hệ thống (`System administrator, ví dụ: `fdisk`, iptables`)
Nếu bạn cần tìm file cấu hình thay vì lệnh (ví dụ: `passwd`) chỉ cần chạy `man passwd` có thể hiển thị lệnh đổi mật khẩu (Section 1). Để xem định dạng tệp `/etc/passwd` (Section 5), dùng `man 5 passwd`
![[Pasted image 20260330155413.png]]
### Hệ thống Info

Trong khi `man` tập trung vào tham chiếu nhanh, `info` cung cấp tìa liệu chi tiết hơn, thường dưới dạng một cây phân cấp(hyperlinked) giống như một cuốn sách điện tử nhỏ. Các dự án của GNU thường ưu tiên định `info`
Để mở tài liệu `info` của một lệnh: `info tên lệnh`
#### Khác biệt chính giữa Info và Man
`info` cho phép bạn di chuyển giữa các node (nút thông tin)
- Sử dụng phím Tab để di chuyển con trỏ đến các liên kết thường là các từ trong ngoặc nhọn 
- Nhấn Enter để đi vào liên kết đó
- Nhấn l (chữ L thường) để quay lại nút trước đó
- Nhất q để thoát
![[Pasted image 20260330162616.png]]
![[Pasted image 20260330163150.png]]
![[Pasted image 20260331074449.png]]
## Các lệnh tìm kiếm tài liệu thay thế

Nếu bạn không nhớ chính xác tên lệnh, bạn không thể sử dụng `man`. Lúc này, hãy dùng các công cụ tìm kiếm metadata:

- **`whatis [tên_lệnh]`**: Hiển thị một dòng mô tả ngắn về lệnh đó.
- **`apropos [từ_khóa]`**: Tìm kiếm trong toàn bộ cơ sở dữ liệu mô tả lệnh xem lệnh nào liên quan đến từ khóa của bạn. Ví dụ: `apropos network` sẽ liệt kê tất cả các lệnh có liên quan đến mạng.

> **Lưu ý:** `apropos` hoạt động bằng cách tìm kiếm trong các mô tả tóm tắt của Man pages. Nếu bạn mới cài đặt hệ thống, cơ sở dữ liệu này có thể chưa được tạo, bạn có thể cần chạy lệnh `mandb` để cập nhật.
# Thực hành: Thiết lập hệ thống và làm chủ các lệnh điều hướng cơ bản

Hệ thống tệp tin trong Linux tuân thủ cấu trúc cây phân cấp (File Hierarchy Standard - FHS), bắt đầu từ thư mục gốc `/`. Mọi thiết bị, tệp tin và cấu hình hệ thống đều được biểu diễn dưới dạng tệp tin nằm trong cấu trúc này. Việc điều hướng và thao tác thành thạo trong hệ thống này là kỹ năng cốt lõi để quản trị máy chủ.
## Thao tác với thư mục

Việc tạo và quản lý cấu trúc thư mục được thực hiện thông qua:

- `mkdir` (Make Directory): Tạo thư mục mới. Sử dụng `mkdir -p` để tạo cấu trúc thư mục lồng nhau cùng lúc, ví dụ: `mkdir -p /home/user/projects/web/src`.
- `rmdir`: Chỉ xóa thư mục nếu nó rỗng.
- `rm -r`: Xóa thư mục và toàn bộ nội dung bên trong nó (cẩn thận với lệnh này vì dữ liệu sẽ không nằm trong thùng rác).
# Các thao tác cơ bản với tệp tin và thư mục (cp, mv, rm, mkdir)

Hệ thống tệp tin trong Linux được tổ chức theo cấu trúc hình cây, bắt đầu từ thư mục gốc `/`. Việc làm chủ các thao tác thao túng tệp tin và thư mục là kỹ năng nền tảng để quản trị một File Server, nơi bạn phải liên tục tạo, sao chép, di chuyển và xóa các dữ liệu người dùng.
## Tạo và cấu trúc thư mục với mkdir
Lệnh `mkdir` (make directory) dùng để tạo thư mục. Bạn có thể tạo một thư mục đơn lẻ hoặc một cấu trúc phân cấp phức tạp ngay trong một dòng lệnh.![[Pasted image 20260331103105.png]]
#### Sao chép dữ liệu với cp
Lệnh copy `cp` dữ liệu tạo ra bản sao của tệp tin hoặc thư mục. Hiểu rõ các tùy chọn của `cp` giúp bạn bảo toàn dữ iệu khi di chuyển tệp vòa hệ thống lưu trữ.

![[Pasted image 20260331103412.png]]
`cp report.pdf /data/backup/`
![[Pasted image 20260331104102.png]]
```shell
# Sao chép tệp tin đơn lẻ
cp report.pdf /data/backup/

# Sao chép thư mục (bắt buộc dùng -r để đệ quy - recursive)
cp -r /home/user/documents /data/backup/

# Sao chép và giữ nguyên thuộc tính (quyền, thời gian tạo)
cp -a /var/www/html /mnt/backup_drive/
```
#### Di chuyển và đổi tên với mv
Trong Linux, không có lệnh riêng để đổi tên tệp. Lệnh `mv` đảm nhận cả hai vai trò: đổi tên(nếu đích đến cùng thư mục) và di chuyển(nếu đích đến khác thư mục)
```shell
# Đổi tên tệp
mv draft.txt final_report.txt

# Di chuyển tệp tin vào thư mục khác
mv final_report.txt /data/projects/finance/

# Di chuyển toàn bộ nội dung của một thư mục
mv /temp_data/* /data/storage/
```
`mv` hoạt động bằng cách thay đổi con trỏ (inode) của tệp tin trong hệ thống tệp, vì vậy nó diễn ra gần như tức thì bất kể dung lượng tệp là bao nhiêu.
#### Xóa dữ liệu an toàn với rm

`rm` là lệnh nguy hiểm nhất vì tệp tin bị xóa trong Linux CLI thường không nằm trong `Recycle Bin`
```bash
### xóa tệp tin
rm file.txt
### xóa thư mục và toàn bộ nội dung bên trong
rm -rf /data/projects
### xóa có xác nhận (an toàn hơn khi thao tác với file server)
rm -i sensitive_data.csv
```
Cảnh báo: `rm -rf` là lệnh `quyền năng` có thể xóa sạch hệ thống nếu bạn gõ nhầm đường dẫn 
`ví dụ rm -rf /` Luôn kiểm tra kỹ đường với `pwd` hạowc `ls` trước khi nhấn Enter
![[Pasted image 20260331120900.png]]

#### Exercise
1. Tạo cấu trúc thư mục sau bằng một lệnh duy nhất: `/data/server/logs`, `/data/server/config` và `/data/server/data`.
![[Pasted image 20260331122813.png]]
2. Sao chép tất cả các tệp có đuôi `.log` từ `/var/log` vào thư mục `/data/server/logs` vừa tạo.
![[Pasted image 20260331124547.png]]
3. Di chuyển tệp `config.yaml` từ thư mục hiện tại vào `/data/server/config` và đổi tên nó thành `production.yaml`.

4. Xóa thư mục `/data/server/data` một cách an toàn sau khi đã kiểm tra kỹ bằng lệnh `ls`.
![[Pasted image 20260331130138.png]]
### Cơ chế quản lý quyền truy cập tệp tin (chmod, chowm)
Mọi tệp tin và thư mục trong Linux đều gắn liền với quyền hạn (permission) và chủ sở hữu (ownership). Đây là cơ chế bảo mật cốt lõi ngăn chặn việc người dùng trái phép xem, chỉnh sửa hoặc xóa dữ liệu nhạy cảm trên máy chủ tệp tin của bạn
##### Cấu trúc quyền truy cập tệp tin (rwx)
Khi bạn chạy lệnh `ls -l` trong terminal, Linux hiển thị danh sách tệp kèm theo một chuỗi ký tự như `-rwxr-xr--`. Đây chính là `Chứng minh thư` quyền hạn của tệp đó. Chuỗi này được chia thành 4 phần chính:
1. `Loại tệp`: Ký tự đầu tiên (`-` là tệp thông thường, `d` là thư mục)
2. `Quyền của Chủ sở hữu (User)`: 3 ký tự tiếp theo
3. `Quyền của Nhóm (Group)`: 3 ký tự sau đó
4. `Quyền của Người khác (Others)`: 3 ký tự cuối cùng
Trong mỗi nhóm có 3 ký tự, thứ tự luôn là `r`, `w`,`x`:
`r(read)`: Đọc nội dung tệp hoặc liệt kê danh sách tệp trong thư mục
`w(write)`: Chỉnh sửa/xóa tệp hoặc tạo/xóa tệp bên trong thư mục
`x(exucute)`: Thực thi tệp(nếu script) hạowc truy cạp bên trong thư mục `cd`
##### Cơ chế quản lý quyền bằng con số (Octal)
Để thay đổi quyền nhanh chóng, Linux sử dụng hệ cơ số 8:
- `r = 4`
- `w = 2`
- `x = 1`
- Không có quyền = 0
![[Pasted image 20260331131315.png]]
#### Thay đổi quyền truy cập chmod
Lệnh `chmod` cho phép bạn thay đổi quyền hạn của tệp tin. Có hai cách để sử dụng:
##### Cách dùng mã số (Tuyệt đối)
Cách này thiết lập lại hoàn toàn quyền hạn hiện có:
```bash
### Thiết lập tệp data.txt cho phép chủ sở hữu quyền đọc ghi, nhóm quyền đọc, other đọc
chmod 644 data.txt
### Thiết lập Script `backup.sh` cho phép tất cả mọi người thực thi
chmod 755 backup.sh
```
![[Pasted image 20260331132209.png]]
#### Thay đổi chủ sở hữu với chown
Nếu `chmod` quản lý được làm gì thì `chown` quản lý ai sở hữu nó. Trên hệ thống đa người dùng, tệp tin thường thuộc về một người dùng `User` và một nhóm `Group` cụ thể:

Cấu trúc `chown [user]:[group] [file/folder]`
```shell
%% chuyển quyền sở hữu tệp cho user tên 'admin' %%
sudo chown admin data.txt
%% Chuyển cả user sở hữu và nhóm sở hữu %%
sudo chown admin:finance report.pdf
%% Thay đổi chủ sở hữu cho toàn bộ thư mục và các tệp con (-R: recursive) %%
sudo chơn -R admin:admin /srv/fileserver/data
```
> Lưu ý: Việc thay đổi chủ sở hữu tệp thường yêu cầu quyền quản trị `sudo`, vì ta đang thay đổi quyền truy cập của hệ thống

##### Thực hành xác định quyền
Hãy quan sát một ví dụ thực tế trên File Server:
![[Pasted image 20260331140901.png]]
![[Pasted image 20260331140933.png]]
Đầu tiên thì thư mục `shared_docs` sẽ được người sở hữu nó là `linuxserver` chuyển sở hữu cho nhóm `staff` . `linuxserver` sẽ set quyền lại `770` cho thư mục `shared_docs` lúc này `group staff` sẽ có toàn quyền. Tuy nhiên chỉ với thư mục `shared_docs` . Nhưng để vào được thư mục `shared_docs` thì cần phải đi qua `/home/linuxserver`. Lúc này những thằng thuộc group `staff` cần phải được `linuxserver` cho phép. Ta lại set quyền `711` tức là cho phép `x` (tưng ứng với là cho phép thực thi, đi qua chứ không được đọc hay viết ở `/home/linuxserver/`). Sau khi ta vào được đến `/home/linuxserver/shared_docs` thì tại `shared_docs` quyền của `staff` sẽ là tối thượng.
![[Pasted image 20260331141616.png]]
#### Exercises
1. Kiểm tra quyền hạn hiện tại của một tệp bất kỳ
![[Pasted image 20260331142059.png]]
### Sử dụng các trình soạn thảo văn bản trong terminal Nano và Vim

Nano và Vim là 2 công cụ soạn thảo văn bản mặc định trên hầu hết các hệ thống Linux. Dù cùng mục đích chỉnh sửa file cấu hình, các h tiếp cận của chúng hoàn toàn khác biệt: Nano hướng tới sự đơn giản , trực quan, trong khi Vim hướng tới tốc độ xử lý thông qua các phím tắt và chế độ làm viẹc chuyên sâu
#### Nano trình soạn thảo cho người mới
Nano là trình soạn thảo dòng lệnh WYSIWYG(What You See Is What You Get). Bạn không cần học cú pháp phức tạp; các lệnh điều khiển luon hiển thị ở hàng cuối cùng của màn hình
#### Vim sức mạnh từ chế độ (Models)
Vim (Vi improved) không giống bất kỳ trình soạn thảo nào bạn từng dùng như Nodepad hay VS Code. Nó hoạt động dựa trên các `chế độ`, giúp thao tác tay của ta không cần rời khỏi khu vực phím chính.
#### Các chế độ qua ntronjg nhất
1. `Normal mode`: chế độ mặc định khi mở file. Dùng để điều hướng, xóa, copy, tìm kiếm. Mọi phím đều là lệnh, ko được nhập văn bản
2. `Insert Mode`:Dùng để nhập văn bản, chuyển sang chế độ bằng phím `i` (insert)
3. `Command Mode`: Dùng để lưu hoặc thoát. Dùng bằng phím `:`
#### Thao tác vận hành chuyên nghiệp
Khi đang ở chế độ `Normal Mode`, bạn có thể thực hiện nuhwngx tác vụ cực nhanh:
`x`: xóa ký tự tại con trỏ
`dd`: xóa, cắt cả một dòng
`yy`: sao chép cả một dòng
`p`: dán sau dòng hiện tại
`u:` undo
`/từ khóa` : tìm kiếm
##### Lưu và thoát
Trong **Command Mode** (nhấn `:`):
- `:w`: Lưu (Write).
- `:q`: Thoát (Quit).
- `:wq`: Lưu và thoát.
- `:q!`: Thoát mà không lưu (áp dụng khi bạn lỡ tay chỉnh sửa sai).
### Kỹ thuật chuyển hướng luồng dữ liệu và đường ống (Redirection & Pipes)
Mọi tiến trình (process) trong linux khi khởi chạy đều đi kèm với `ba luồng dữ liệu chuẩn` 
`Standard Input (stdin - 0)` `Standard Output (stdout - 1)` và `Standard Error (stderr - 2)`
Việc quản lý hệ thống `File server` đòi hỏi bạn phải kiểm soát chính xác luồng dữ liệu này; ghi nhật ký lỗi, lưu trữ kết quả truy vấn vào tệp tin hoặc kết nối đầu ra của một lệnh này làm đầu vào cho lệnh khác
#### Chuyển hướng luồng dữ liệu (Redirection)
Chuyển hướng cho phpes bạn thay đổi đích đến mặc định của các luồng này. Mặc định, `stdout` và `stderr` hiển thị ra màn hình `terminal` , còn `stdin` lấy từ bàn phím
- `Ghi đè(>)`: Đẩy dữ liệu vào tệp tin, xóa sạch nội dung cũ
- `Ghi tiếp (>>)`: Ghi thêm dữ liệu vào cuối tệp tin mà không làm mất dữ liệu hiện có
- `Chuyển hướng lỗi (2>)`: Chuyển hướng luồng lỗi
![[Pasted image 20260331145539.png]]
![[Pasted image 20260331150520.png]]
![[Pasted image 20260331150841.png]]
```shell
# Ghi danh sách tệp tin vào file log, nếu file tồn tại sẽ bị ghi đè
ls -l /home/data > /var/log/file_server.log

# Ghi thêm thông tin người dùng mới vào danh sách truy cập mà không xóa dữ liệu cũ
echo "user_admin:rw" >> /etc/file_server/access_list

# Ghi lỗi của một lệnh tìm kiếm vào tệp riêng để phân tích sau
find / -name "config.sys" 2> /var/log/search_errors.log
```
Để xử lý chuyên sâu, bạn có thể kết hợp cả hai luồng vào một tệp:

- `command > log.txt 2>&1`: Đẩy cả đầu ra chuẩn và lỗi vào cùng một tệp.
- `command &> log.txt`: Cú pháp rút gọn hiện đại cho lệnh trên.
#### Kết nối luồng dữ liệu qua Đường ống (Pipes)
Đường ống `|` là công cụ mạnh mẽ nhất trong Linux để kết nối các lệnh đơn lẻ thành một chuỗi xử lý phứ tạp. Nó lấy `stdout` của lệnh bên trái và biến nó thành `stdin` cho lệnh bên phải
![[Pasted image 20260331151629.png]]
![[Pasted image 20260331151740.png]]
**Ví dụ thực tế trong quản trị File Server:** Khi cần tìm kiếm một tệp cấu hình có chứa từ khóa "backup" trong thư mục `/etc`:
![[Pasted image 20260331152251.png]]
```shell
# Liệt kê tất cả file, sau đó lọc các dòng có chứa từ khóa 'backup'
ls -R /etc | grep "backup"

# Đếm số lượng tệp tin hoặc thư mục đang nằm trong danh mục quản lý
ls /home/data | wc -l
```
![[Pasted image 20260331153238.png]]
![[Pasted image 20260331153351.png]]
![[Pasted image 20260331154419.png]]
### Kết hợp Redirection và Pipes
Sự kết hợp này tạo nên tư duy "xây dựng công cụ từ các mảnh ghép". Nếu bạn muốn tạo một báo cáo về các tệp tin có dung lượng lớn nhất và lưu trữ vào file `report.txt`:
![[Pasted image 20260331154948.png]]
```bash
# 'du' lấy dung lượng, 'sort' sắp xếp theo số, 'tail' lấy 10 dòng cuối
du -h /home/data | sort -h | tail -n 10 > /var/log/large_files_report.txt
```
**Lưu ý quan trọng:** `Pipe` chỉ chuyển `stdout`. Nếu bạn muốn chuyển cả `stderr` qua một đường ống, bạn phải chuyển hướng `stderr` sang `stdout` trước bằng `2>&1`.
![[Pasted image 20260331160146.png]]
`2>&1` có thể viết ngắn lại thành `ls -la ./koco &>> error.log`
![[Pasted image 20260331161056.png]]

2. Kiểm tra danh sách các tiến trình hệ thống bằng `ps aux`, sau đó dùng `grep` để lọc ra duy nhất tiến trình liên quan đến `sshd`.
![[Pasted image 20260331160749.png]]
`stdin-->grep sshd --->stdout >> sshd.log`
![[Pasted image 20260331161031.png]]

3. Tạo một danh sách các tệp tin trong thư mục `/etc` và ghi kết quả đó vào tệp `sys_structure.txt`.
```bash
ls /etc/ >> sys_structure.txt
```
# Thực hành: Cấu hình hệ thống lưu trữ tệp tin cho một dự án doanh nghiệp giả định

Hệ thống lưu trữ trong doanh nghiệp không chỉ là việc tạo thư mục; đó là thiết lập cấu trúc phân cấp đảm bảo tính nhất quán trong quyền truy cập và kiểm soát đảm bảo tính nhất quán trong quyền truy cập của từng bộ phận. Trong môi trường linux, chúng ta sử dụng các công cụ dòng lệnh để kiến tạo một cấu trúc tệp tin có tính huy hoạch cao
#### Kiến trúc File Server cho doanh nghiệp
Giải định doanh nghiệp của bạn có ba phòng ban chính: `IT`, `HR`, `Sales`. Mỗi bộ phòng cần có một khu vực lưu trữ riêng biệt. Đồng thời cần 1 thư mục chia sẽ `Public` để trao đổi dữ liệu. Chúng ta sẽ bắt đầu bằng việc thiết lập cấu trúc cây thư mục `/data`
#### Thiết lập quyền hạn và sở hữu (Owner and Permission)
Trong Linux, sự khác biệt giữa `owner`, `group` và `others` là `cốt lõi của bảo mật` . Đối với `File Server` chúng ta sẽ gán sở hữu các thư mục cho nhóm tương ứng
Giả sử chúng ta đã có các nhóm `it_dept`, `hr_dept`, và `sales_dept`. Chúng ta sử dụng `chown` để thay đổi chủ sở hữu nhóm và `chmod` để tinh chỉnh quyền truy cập.
```bash
# Gán nhóm sở hữu cho từng thư mục
sudo chgrp it_dept /data/it
sudo chgrp hr_dept /data/hr
sudo chgrp sales_dept /data/sales

# Thiết lập quyền: Người dùng trong nhóm có quyền đọc/ghi/thực thi, người khác không có quyền gì cả
sudo chmod 770 /data/it /data/hr /data/sales

# Thiết lập quyền cho thư mục công cộng: Ai cũng có thể đọc và viết, nhưng không thể xóa tệp của nhau (sticky bit)
sudo chmod 1777 /data/public
```
_Lưu ý:_ `1` trong `1777` là **Sticky Bit**. Nó đảm bảo rằng trong thư mục `public`, người dùng chỉ có thể xóa các tệp tin do chính họ tạo ra, ngăn chặn việc nhân viên xóa nhầm tệp của người khác.
#### Tự động hóa luồng dữ liệu (Redirection & Pipes)
Quản trị viên phải thường xuyên kiểm tra trạng thái lưu trữ và chuyển hướng kết quả vào tệp `log` để báo cáo. Thay vì xem trực tiếp trên màn hình, hãy kết hợp `ls` và `grep` và toán tử chuyển hướng
```shell
#Xuất danh sách tất cả tệp tin tỏng /data ra một báo cáo kiểm kê
ls -lR /data > /var/log/file_server_audit.txt
#Lọc nhanh các thư mục bị lỗi quyền hạn (nếu có) và ghi đè vào tệp báo cáo lỗi
find /data -type d -perm 777 2> /var/log/security_warnings.txt
```
Toán tử '>' sẽ tạo mới hoặc ghi đè tệp, trong khi `>>` dùng để thêm nội dung vào tệp. Việc kết nợp `|` (pipe) cho phép truyền kết quả từ lệnh tước ang lệnh sau một cách liền mạch
#### Luồng công việc xử lý dữ liệu

![[Pasted image 20260331192202.png]]
![[Pasted image 20260331192300.png]]
![[Pasted image 20260331192323.png]]
![[Pasted image 20260331192343.png]]
![[Pasted image 20260331192409.png]]
![[Pasted image 20260331192612.png]]
![[Pasted image 20260331192714.png]]
![[Pasted image 20260401103706.png]]
### Thực hành cấu hình hệ thống lưu trữ

Để hoàn thành việccaaus hình cho dự án doanh nghiệp này, ta thực hiện theo các bước sau trong terminal:
1. `Chuẩn bị môi trường`: Tạo cấu trúc thư mục như đã mô tả
2. `Thiết lập quyền tối ưu`: Sử dụng `chmod` để đảm bảo không ai ngoài nhân viên bộ phân đó có thể vào thư mục nội bộ
3. `Kiểm tra luồng`: Sử dụng lệnh `ls -ld /data/it` và quan sát các ký tự quyền (ví dụ: `drwxrwx---`). Giải thích tại sao cột thứ hai có quyền không cho phép `others` truy cập
4. `Giả lập sự cố`: Tạo một tệp `test.txt` trong `/data/public` với tư cách là một người dùng, sau đó xóa nó với tư cách là một người dùng khác để kiểm chứng hiệu quả của `Sticky Bit`
`tree /data`
![[Pasted image 20260402082613.png]]
Cấu trúc cây thư mục trong thư mục sẽ như vậy. Và những nhân sự thuộc bộ phận nào sẽ chỉ được truy cập vào thư mục của bộ phận đó thôi
#### Các bước thực hiện 
1. Create folder
```bash
sudo mkdir -p /data/hr /data/it /data/sales /data/public
```
2. Create group to assign folder
```bash
sudo groupadd -G 5000 it_dept hr_dept sales_dept
```
3. Assign folder **corresponding** 
```bash
sudo chgrp it_dept /data/it
sudo chgrp hr_dept /data/hr
sudo chgrp sales_dept /data/sales
```
4. Configure permission folder
```bash
sudo chmod 770 /data/it
sudo chmod 770 /data/hr
sudo chmod 770 /data/sales
# Số 1 ở đây là Sticky bit đảm bảo other được full quyền và chỉ được xóa những file mà chính họ tạo ra. 
sudo chmod 1777 /data/public
```
#### Bổ trợ 
`Xuất toàn bộ danh sách các file trong /data ra một báo cáo kiểm kê`
```bash
sudo ls -lR /data | sudo tee /var/log/file_server_audit.txt > /dev/null
```
`l`: long list
`R`: recursion, liệt kê đệ quy cả những file trong thư mục của thư mục
`>`: stdout ghi đè lên nội dung hiện có trong file đó luôn
Để ghi được vào file hệ thống thì bắt buộc `tee` chạy với sudo → có quyền ghi file 
`/dev/null` để không in ra màn hình
```bash
find /data -type d -perm 777 2> /var/log/security_warnings.txt
```
Bạn nghĩ rằng có chữ `sudo` đứng đầu thì cả câu lệnh sẽ được chạy bằng quyền `root` (quản trị viên cao nhất), nên việc ghi vào `/var/log/` sẽ thành công. **Nhưng thực tế thì hệ thống sẽ báo lỗi.** Tại sao?

1. **Cách Shell (Terminal) đọc lệnh:** Trước khi chạy lệnh, Shell hiện tại của bạn sẽ quét qua một lượt và thấy dấu chuyển hướng `>`.
    
2. **Ai là người thực hiện dấu `>`?** Chính là tài khoản người dùng bình thường của bạn (chứ không phải `root`). Shell của bạn cố gắng tạo ra file `/var/log/security_warnings.txt` **trước khi** nó kịp gọi đến lệnh `sudo find...`.
    
3. Vì bạn là người dùng bình thường, không có quyền tạo file trong thư mục hệ thống `/var/log/`, nên Shell lập tức báo lỗi và dừng lại. `sudo` ở đầu câu lúc này chỉ cấp quyền quản trị cho đúng chữ `find` mà thôi, chứ không cấp quyền cho dấu `>`.
    
**Và đây là lúc `sudo bash -c` ra tay cứu nguy:**
```bash
sudo bash -c 'find /data -type d -perm 777 > /var/log/security_warnings.txt'
```
Khi bạn viết như thế này, trình tự xử lý sẽ thay đổi hoàn toàn:

1. `sudo` sẽ cấp quyền quản trị viên (`root`) cho lệnh ngay sau nó là `bash`.
2. Lệnh `bash -c` (đang có quyền root) sẽ khởi tạo một Shell hoàn toàn mới với tư cách là `root`.
3. Shell `root` mới này bắt đầu đọc chuỗi `'find /data... > /var/log/...'` nằm trong dấu ngoặc nháy.
4. Nhờ đang là `root`, Shell mới này có thể thoải mái thực hiện dấu chuyển hướng `>` để tạo file trong `/var/log/` mà không gặp bất kỳ rào cản nào, sau đó nó chạy lệnh `find` và ghi kết quả vào file.
5. Hoàn thành xong, Shell phụ này tự động đóng lại.
`Ta tự tạo ra sự cố bằng cách cho IT vào Public và tạo 1 file. Sau đó cho HR vào đọc và xóa`
![[Pasted image 20260402191108.png]]
`Thấy được giá trị của Sticky Bit 1 trong 1777 chỉ cho phép người tạo ra nó xóa thôi`
### Quản lý tài khoản người dùng và nhóm người dùng (useradd, usermod, groupadd)

Tài khoản người dùng trong Linux chỉ là một tên đăng nhập; đó là định danh xác định quyền hạn, sở hữu tệp tin và giới hạn tài nguyên của một chủ thể trên hệ thống. Mọi tương tác của ạn với hệ thống đều được Linux ghi nhận qua UID và GID
#### Quản lý tài khoản người dùng với `useradd` và `usermod`
Khi bạn tạo một người dugnf mới bằng lệnh `useradd`, Linux thực hiện một loạt các thao tác ngầm: tạo mục nhập trong tệp `/etc/passwd`, thiết lập nhóm mặc định trong `/etc/group` và tạo thư mục cá nhân (home directory)
#### Khởi tạo người dùng với `useradd`
Cú pháp cơ bản là `useradd [option] username`. Tuy nhiên, để tạo một tài khoản có môi trường làm việc hoàn chỉnh, bạn nên sử dụng các tham số cụ thể:
`-m`: Tạo thư mục cá nhân tại `/home/username`. Nếu không có tham số này, người dùng sẽ không có nơi lưu trữ dữ liệu cá nhân
`-s`: Chỉ định shell mặc định sẽ là `/bin/bash`
`-G`: Thêm người dùng vào các nhóm phụ ngay khi tạo
Ví dụ: Tạo tài khoản nhân viên `nguyenvana` thuộc nhóm `developers`
```bash
sudo useradd -m -s /bin/bash -G developers IT
```
Sau khi tạo user xong thì phải tạo mk ngay nếu không thì user sẽ bị khóa `passwd IT`
#### Thay đổi thuộc tính người dùng với `usedmod`
Khi cấu hình thay đổi ví dụ như nhân viên đổi bộ phận, lệnh `usermod` cho phép chỉnh sửa `group` thông tin người dùng mà không cần xóa `user`
`-aG`: Thêm người dùng vào nhóm mới mà `không` loại bỏ những nhóm hiện tại của họ chữ a là `append`
`-l`: Đổi tên đăng nhập (login name)
`-d`: Thay đổi đường dẫn thư mục cá nhân
#### Cấu trúc nhóm người dùng và quản lý với `groupadd`
Nhóm người dugnf là công cụ quản trị quyền hạn hiệu quả nhất. Thay vì phân quyền cho từng cá nhân, bạn phân quyền cho nhóm, sau đó thêm người dùng vào nhóm đó
Lệnh `groupadd` tạo ra một nhóm mới trong tệp `/etc/group` 

```bash
sudo usermod userdev IT
```
![[Pasted image 20260402200655.png]]
Để kiểm tra các nhóm mà một người dùng đang tham gia, sử dụng lệnh `groups`:
```bash
groups IT
```
```bash
# Tạo nhóm 'finance' cho nhân viên kế toán
sudo groupadd finance

# Thêm người dùng 'nguyenvanb' vào nhóm này
sudo usermod -aG finance nguyenvanb
```
#### Kiểm soát thông tin tài khoản
Dữ liệu người dùng được lưu trữ trong các tệp văn bản thuần. Hiểu về chúng giúp bạn xử lý sự cố nhanh chóng:

1. `/etc/passwd`: Chứa thông tin người dùng (tên, UID, GID, home directory, shell).
2. `/etc/shadow`: Chứa mật khẩu đã mã hóa (chỉ root mới đọc được).
3. `/etc/group`: Chứa định nghĩa các nhóm và danh sách thành viên.

Bạn có thể kiểm tra định danh hiện tại của mình bằng lệnh `id`. Lệnh này sẽ hiển thị UID, GID và tất cả các nhóm mà tài khoản của bạn đang thuộc về.
Việc quản lý người dùng tập trung vào việc tạo định danh (useradd), điều chỉnh quyền truy cập thông qua nhóm (usermod, groupadd) và đảm bảo môi trường làm việc (home directory, shell) được thiết lập đúng cách. Các tệp cấu hình `/etc/passwd` và `/etc/group` là nơi lưu trữ cốt lõi. Trong phần tiếp theo, chúng ta sẽ tìm hiểu cách sử dụng quyền nâng cao với `sudo` để thực thi các tác vụ quản trị một cách an toàn mà không cần phải đăng nhập trực tiếp bằng tài khoản `root`.
![[Pasted image 20260402202641.png]]
### Hiểu và sử dụng quyền nâng cao với sudo

`sudo` `substitute User Do` hoặc `superuser do` là cơ chế cho phép người dùng thực thi các lệnh với quyền của người dùng cao nhât, thưognf là quyền `root` (siêu người dùng), mà không cần phải đăng nhập tực tiếp vào tài khoản `root` . Thay vì phải chia sẽ mật khẩu `root` cho nhiều nhân viên, bạn cấp quyền cho họ thông qua tệp cấu hình `/etc/sudoers`
![[Pasted image 20260402203754.png]]

#### Cơ chế hoạt động của Sudo
Khi bạn gõ `sudo <lệnh>`, hệ thống kiểm tra tệp `/etc/sudoers` để xác định xem người dùng hiện tại có quyền thực thi lệnh đó với tu cách là `root` hay không. Nếu có, hệ thống sẽ yêu cầu `mật khẩu của chính người dùng đó` (không phải mật khẩu `root`) để xác thực.
#### Luồng thực thi
`user` gõ `sudo apt update` ---> `bash shell` ---> `tệp /etc/sudoers` nếu kiểm tra thấy có quyền truy cập thì gửi ngược lại yêu cầu xác nhận quyền yêu cầu mật khẩu rồi shell hỏi `user`, `user` nhập mk của chính user đó kiểm thực hiện quyền root
#### Quản trị quyền sudo với tệp /etc/sudoers
`KHÔNG BAO GIỜ ĐƯỢC CHỈNH SỬA TRỰC TIẾP TỆP /ect/sudoers` bằng cách trình soạn thảo thông thường như `nano hay vim` nếu không cẩn thận gân lỗi sẽ khóa hoàn toàn khả năng quản trị của bạn. Luôn dùng `visudo` . Lệnh này giúp kiểm tra cú pháp trước khi lưu tệp
![[Pasted image 20260402204502.png]]
![[Pasted image 20260402204519.png]]
![[Pasted image 20260402204541.png]]
#### Cấp quyền cho người dùng
Để cấp quyền `sudo` cho một người dùng `nhavien1`, bạn thêm dòng  sau vào cuối tệp `visudo`:
```bash
nhanvien1 ALL=(ALL:ALL) ALL
```
Trong đó:
`nhanvien1`: tên người dùng
`ALL=(ALL:ALL)`: ngừo dùng có thể chạy lệnh từ bất kỳ máy chủ nào, dưới quyền bất kỳ người dùng và nhóm nào.
`ALL`: Quyền này áp dụng cho tất cả lệnh
![[Pasted image 20260402204623.png]]
#### Hạn chế quyền sudo
![[Pasted image 20260402204728.png]]
Bạn không nhất thiêt phải có quyền `toàn năng`. Bạn có thể chỉ định người dùng chỉ được phép chạy một lệnh cụ thể. Ví dụ, cho phép `nhanvien1` chỉ dược khởi động lại dịch vụ web
```bash
nhanvien1 ALL=(ALL) /usr/bin/systemctl restart nginx
```
nếu nhanvien1 gõ `sudo apt update` thì hệ thống sẽ từ chối
#### Sử dụng biến môi trường và quyền sudo
Một điểm cần lưu ý là `sudo` mặc định không giữ lại toàn bộ môi tường của người dùng hiện tại vì lý do bảo mật. Nếu bạn cần chuyển các biến môi trường vào phiên làm việc `root`, hãy sử dụng tham số `-E`
![[Pasted image 20260402205518.png]]
### 1. Tại sao `sudo` mặc định không giữ lại biến môi trường?

Khi bạn đang ở tài khoản bình thường (ví dụ: `trung`) và dùng `sudo` để chạy một lệnh, bạn đang tạm thời mượn quyền của tài khoản quản trị cao nhất (`root`).

- **Cơ chế:** Mặc định, `sudo` sẽ tạo ra một môi trường làm việc mới, sạch sẽ và **xóa bỏ hầu hết các biến môi trường** (như `$PATH`, `$USER`, các biến custom bạn tự tạo) của tài khoản `trung`.
    
- **Lý do bảo mật:** Việc này ngăn chặn mã độc. Giả sử ai đó lén thay đổi biến `$PATH` của bạn để trỏ đến một file mã độc. Khi bạn chạy `sudo`, nếu `sudo` giữ nguyên `$PATH` đó, vô tình quyền `root` sẽ thực thi file mã độc đó. Do đó, `sudo` reset lại môi trường cho an toàn.
### 2. Ý nghĩa của `sudo -E ./script.sh`

Chữ **`-E`** viết tắt của từ **"preserve Environment"** (Giữ lại môi trường).

- **Cách hoạt động:** Lệnh này ép `sudo` phải mang theo toàn bộ các biến môi trường của người dùng hiện tại (tài khoản `trung`) sang phiên làm việc của `root`.
    
- **Khi nào sử dụng?** Khi bạn có một script (`script.sh`) cần quyền `root` để chạy, nhưng bên trong script đó lại cần đọc các biến môi trường mà bạn đã thiết lập ở tài khoản thường (ví dụ: biến chứa API Key, biến đường dẫn đến project Node.js của bạn, v.v.).
Thông thường sẽ bị chặn quyền này
Ta cần vào 
`sudo visudo` 
```bash
linuxserver ALL=(ALL:ALL) SETENV: ALL
```
set quyền cho linuxserver như vậy không thì hệ thống vân chưa cho chạy. Vid việc truyền biến môi trường từ user vào root là rất nguy hiểm
Ta đã cấu hình cho phép `SETENV` rồi nhưng không có `env_keep` hoặc `!env_reset` , nên `sudo` vẫn reset tất cả mọi thứ mọi trường để tạo môi trường mới sạch nên nó sẽ bỏ qua `-E`
Có 4 cách khắc phục:
`CÁCH 1: TRUYỀN TRỰC TIẾP VÀO SUDO `
![[Pasted image 20260403073804.png]]
`CÁCH 2: THÊM env_keep vào sudoers`
```bash
Defaults env_keep += "MY_SECRET"
```
![[Pasted image 20260403074214.png]]
Chỉ nên dùng 2 cách này
#### Kiểm tra lịch sử sudo
Tất cả những hành động thực thi bằng `sudo` đều được hệ thống ghi nhận lại vào tệp log `/var/log/auth.log`
Việc giám sát tệp này rất quan trọng để đảm bảo tính minh bạch trong quản trị:
![[Pasted image 20260403075552.png]]
```bash
grep sudo /var/log/auth.log
```
### Exercises
1. Sử dụng `sudo visudo` để tạo một nhóm người dùng (ví dụ: `admins`) và cấp quyền cho tất cả thành viên trong nhóm này được chạy lệnh mà không cần nhập mật khẩu (`NOPASSWD`).
![[Pasted image 20260403091400.png]]
```bash
# Cho phép nhóm admins chạy mọi lệnh không cần mật khẩu
%admins ALL=(ALL:ALL) NOPASSWD: ALL
```
![[Pasted image 20260403091601.png]]

2. Kiểm tra xem người dùng hiện tại có quyền thực thi `sudo` hay không bằng lệnh `sudo -l`.
![[Pasted image 20260403092204.png]]
3. Tạo một script bash đơn giản, sau đó cấu hình để một người dùng không có quyền root vẫn có thể chạy script đó thông qua `sudo`.

```bash
WHO  WHERE=(AS_WHOM)  WHAT
```

#### Quản lý các tiến trình đang chạy (ps, top, htop, kill)
Mọi tiến trihf đang cahyj trong Linux, từ các dịch vụ hệ thống chạy ngầm đến trình soạn thảo văn bản ta đang mở, đều được hệ điều hành quản lý thông qua một cấu trúc phân cấp định danh gọi là PID. Để làm chủ hệ thống, ta phải biêt cách quan sát, đánh giá tài nguyên và can thiệp trực tiếp vào vòng đời của các tiến trình này
### Giám sát tiến trình với `ps` (Process Status)

Lệnh `ps` cung cấp một `ảnh chụp nhanh` snapshot về các tiến trình hiện có. Khác với các công cụ giám sát thời gian thực, `ps` chỉ xuất ra trnjag thái thời điểm bạn thực thi lệnh
Để xem toàn bộ tiến trình trên hệ với định dạng đầy đủ, hãy sử dụng:
```bash
ps aux
```
`a`: hiện thị tiến trình của tất cả người dùng
`u`: hiển thị chi tiết (User) sở hữu tiến trình, mức sử dụng CPU/RAM
`x`: bao gồm cả các tiến trình không có terminal (các tiến trình chạy ngầm)
![[Pasted image 20260403103855.png]]
`USER`: Người dùng sở hữu tiến trình 
`PID`: Mã định danh duy nhât của tiến trình. Bạn cần PID để điều khiển hoặc dừng tiến trình
`%CPU/%MEM`: Tỉ lệ sử dụng CPU và bộ nhớm RAM
`STAT`: trạng thái tiến trình `ví dụ: S, R, Z (zoombies)`
`COMMAND`: lệnh khởi chạy tiến trình đó
#### Giám sát thười gian thực hiện với `top` và `htop` 
Khi cần theo dõi sự biến động của tài nguyên, `top` là công cụ mặc định trên mọi hệ thống linux. Nó tự động làm mưới dữ liệu sau mỗi vài giây.

Khi chạy lệnh `top`, bạn có thể nhấn các phím sau để điều hướng;
`P`: Sắp xếp theo mức sử dụng CPU
`M`: Sắp xếp theo mức sử dụng RAM
`k` : Nhập `PID` để gửi tín hiệu dừng tiến trình
`q`: Thoát khỏi chương trình
![[Pasted image 20260403104936.png]]

`PID`: Process ID, mã định danh duy nhất của tiến trình
`USER`: Người dùng sở hữu tiến trình
`PR`: Priority độ ưu tiên của tiến trình, số càng nhỏ ưu tiên càng cao
`NI`: Nice value - giá trị điều chỉnh độ ưu tiên(-20 đến 19). Âm = ưu tiên coa hơn
`VIRT`: Virutal Memory- tổng bộ nhớ ảo tiến trình đang dùng (KB)
`RES`: Resident Memory - bộ nhớ RAM vật lý thực sự đang chiếm dụng (KB)
`SHR`: Shared Memory - phần bộ nhớ có thể chia sẻ với tiến trình khác
`S` : Status - trạng thái tiến trình: `S = sleeping` , `R = running` , `I = Idle`
`%CPU`: phần trăm CPU mà tiến trình đang sử dụng
`%MEM`: Phần trăm RAM vật lý mà tiến trình đang sử dụng
`TIME+`: tổng thời gian CPU đã tiêu thụ (phút: giây: phần trăm)
`COMMAND`: Tên lệnh, tiến trình đang chạy
![[Pasted image 20260403133120.png]]
![[Pasted image 20260403133214.png]]
![[Pasted image 20260403133252.png]]
![[Pasted image 20260403133356.png]]
![[Pasted image 20260403133702.png]]
![[Pasted image 20260403134156.png]]
`htop` là một phiên bản cải tiến, trực quan hơn với thanh tiến trình màu sắc và khả năng dùng chuột. Nếu chưa có chuột, nếu chưa có thì có thể cài đặt bằng `sudo apt install htop`. Cho cuộn danh sách, tìm kiếm `/`, quản lý và giết tiến trình bằng phím F9
#### Kiểm soát vòng đời tiến trình với `kill`
Khi một tiến trình bị treo hoặc chiếm dụng tài nguyên quá mức, bạn cần gửi một tín hiệu (signal) tới nó. Lệnh `kill` không thực sự dùng để giết tiến trình mà đúng hơn là gửi tín hiệu tới `PID` đó.
Các tín hiệu phổ biến:
- `SIGTERM`(mặc định tín hiệu 15): Yêu cầu tiến trình đóng lại 1 cách hoàn toàn(dọn dẹp dữ liệu, đóng file)
- `SIGKILL`(tín hiệu 9): Ép buộc tiến trình dừng ngay lập tức. Cẩn thận vì dữ liệu chưa kịp lưu sẽ bị mất
Ví dụ thực tế: Giả sử có một tiến trình `python3` bị treo với `PID` là 1234:
1. Yêu cầu dừng lịch sự:
```bash
kill 1234
```
2. Ép buộc dừng (nếu cách trên thất bại)
```bash
kill -9 1234
```
>>Ta chỉ có quyền gửi tín hiệu đến những tiến trình mà ta sở hữu. Để dừng các tiến trình của người dùng khác hoặc root thì ta phải dùng `sudo kill <PID>`

#### Thực hành
1. Sử dụng `ps aux | grep bash` để tìm kiếm PID của các phiên làm việc hiện tại.
2. Mở `htop`, quan sát cột `RES` (Resident Memory) để xem tiến trình nào đang chiếm RAM nhiều nhất.
3. Tạo một tiến trình giả lập bằng lệnh `sleep 1000 &`, sau đó tìm PID của nó và dùng lệnh `kill` để kết thúc nó.
![[Pasted image 20260403141924.png]]
![[Pasted image 20260403141942.png]]
![[Pasted image 20260403142010.png]]
![[Pasted image 20260403142117.png]]
### Giám sát tài nguyên hệ thống và xử lý các tác vụ ưu tiên

Tiến trình (process) trong linux không chỉ là các chương trình đang chạy, chúng là những thực thê được quản lý bởi `kernel` thông qua việc phân bổ tài nguyên `CPU` và bộ nhớ. Để duy trì sự ổn định của hệ thống, đặc biệt là trên các `File Server` chịu tải cao. Ta cần biết cách giám sát những gì đang xảy ra `ngốn` tài nguyên và điều khiển độ ưu tiên của chúng.
#### Phân tích hệ thống tài nguyên hệ thống với `top` và `htop`
Khi hệ thống có dấu hiệu chậm đi, lệnh đầu tiên ta cần thực thi là `top` . Nó cung cấp cái nhìn thiowf gian thực về trạng thái sức khỏe của toàn bộ hệ thống

Dòng đầu tiên của `top` hiển thị thời gian hoạt động `uptime` , số lượng người dùng và tải trung bình (load average). Load average gồm 3 con số tải trung bình trong 1,5,15 phút. Nếu con số này vượt quá số `core` của `CPU` trên máy chủ, hệ thống của ta đang bị quá tải 
`overload`
Để có cái nhìn trực quan và dễ thao tác hơn thì ta dùng `htop` . Công cụ vượt trội cho phép cuộn, sắp xếp và gửi tín hiệu `kill` trực tiếp bằng phím bấm mà không cần nhớ `PID`
- Cột `%CPU`: phần trăm CPU tiến trình đang chiếm dụng
- Cột `%MEM`: phần trăm bộ nhớ RAM vật lý tiến trình đang sử dụng
- Cột `TIME+`: Tổng thời gian CPU mà tiến trình đã tiêu thụ
#### Độ ưu tiên của tiến trình `Niceness`
Linux sử dụng giá trị `nice` để xác định mức độ ưu tiên của tiến trình. Giá trị này nằm trong khoảng `-20-->19` càng âm thì càng ưu tiên cao. Mặc định, các tiến trình mưới khởi tạo có giá trị `nice` là 0
##### Kiểm tra giá trị Nice
Sử dụng lệnh `ps` để xem giá trị `NI` (Nice) và `PRI` hiện tải của tiến trình:
```bash
ps -eo pid, ni, pri, comm
```
Thay đổi mức độ ưu tiên, nếu bạn có một tác vụ sao lưu dữ liệu lớn vi dụ (`rsync hoặc tar`) đang làm chậm các dịch vụ quan trọng khác như web server, hãy hạ thấp các ưu tiên của nó để nhường tài nguyên cho tiến trình quan trọng hơn.
1. Thiết lập khi bắt đầu chương trình:
```bash
nice -n 10 ./backup_script.sh
```
Lệnh này khởi chạy `backup_script.sh` với giá trị nice là 10 (ưu tiên thấp)
2. Thay đổi tiến trình đang chạy: Nếu tiến trình đã chạy ròi, hãy sử dụng `renice`
```bash
renice -n 15 -p 1234
```
Trong đó `1234` là PID của tiến trình. Lưu ý, chỉ có root mới có quyền hạ giá trị nice(tăng ưu tiên) hoặc thiết lập giá trị âm
### Thực hành: Phân quyền truy cập cho nhân viên dựa trên vai trò Case Study
Phân quyền dựa trên vai trò (Role-Based Access Control - RBAC) trong Linux là việc ánh xạ nhu cầu công việc thực tế của nhân viên vào các nhóm (groups) và quyền tệp tin (permissions). Thay vì cấp quyền thủ công cho từng cá nhân, bạn tao các nhóm chức năng, gán người dùng vào đó và áp đặt quyền lên thư mục dùng chung. 
##### Thiết lập cấu trúc Case Study: Phòng ban kỹ thuật
Giả sử bạn đang quản trị một máy chủ tệp tin cho một công ty. Chúng ta cần thiết lập cấu trúc sau:
- Nhóm `developers` : Được phép đọc, ghi và thực thi thư mục `/data/project`
- Nhóm `interns`: Chỉ được phép đọc trong thư mục `/data/project`, không được phép sữa đổi
- Thư mục `/data/project` phải được sở hữu bởi nhóm `developers` để đảm bảo tính bảo mật
![[Pasted image 20260403165056.png]]
