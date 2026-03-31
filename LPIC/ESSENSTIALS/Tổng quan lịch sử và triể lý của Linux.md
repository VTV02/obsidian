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
