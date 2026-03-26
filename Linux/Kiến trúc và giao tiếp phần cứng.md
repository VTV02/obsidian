
Linux là một nhân (kernel) hệ điều hành nguyên khối (monolithic kernel), hoạt động như lớp trung gian tuyệt đối giữa phần cứng máy tính và phần mềm ứng dụng. Trong kiến trúc này, toàn bộ các chức năng cốt lõi của hệ điều hành—như quản lý tiến trình, quản lý bộ nhớ, driver thiết bị và hệ thống tệp—đều nằm chung trong một không gian địa chỉ duy nhất, được bảo vệ nghiêm ngặt bởi phần cứng.

Việc phân tách không gian thực thi thành **User Space** và **Kernel Space** là chiến lược then chốt để đảm bảo tính ổn định và bảo mật của hệ thống.

#### User Space và Kernel Space: Sự phân chia đặc quyền
Hệ điều hanh sử dung ác mức đặc quyền của CPU(thường gọi là Protection Rings) để thiết lập ranh giới giữa hai vùng này. Hầu hết các kiến trúc CPU hiện đại như x86 hỗ trựo 4 vòng, nhưng `Linux chỉ sử dụng hai: Ring 3 cho User Space và Ring 0` cho Kernel Space

#### User space(vòng 3 low Privilege)
Đây là môi trường nơi các ứng dụng người dùng như trình duyệt web, trình biên dịch, hoặc database server chạy
- Hạn chế: Các tiến trình tỏng User space không có quyền truy cập trực tiếp vào tài nguyên phần cứng(RAM vật lý, cổng I/O, thanh ghi CPU)
- Cách ly: Mỗi tiến trình chạy trong mọt không gian địa chỉ ảo riêng biệt. Nếu một ứng dụng bị crash ví dụ như truy cập bộ nhớ không hợp lệ, nó chỉ làm treo tiến trình đó, khong ảnh hưởng đến toàn bộ hẹ thống
#### Kernel Space (vòng 0 - High Privilege)
Đây là `trái tim` của hệ điều hành, nơi nhân Linux vận hành
- Quyền năng: Kernel có quyền truy cập không gian giới hạn vào mọi tài nguyên phần cứng. Nó quản lý bọ nhớ vật lý, lập lịch cho CPU và kiểm saots luòng dữ liệu giữa phần cứng và ứng dụng
- Rủi ro: Vì kernel chạy chung một không gian đạ chỉ, một lỗi lập trình nhỏ, trong kernel sẽ dẫn đến tình trạng Kernel Panic, làm dừng toàn bộ hệ thống ngay lập tức
![[Pasted image 20260322093420.png]]
#### Ranh giới thực thi Cách ứng dụng nói chuyện với Kernel 
Một ứng dụng không thể đơn giản là nhảu vào mã nguồn của Kernel để yêu cầu ghi dữ liệu xuống đĩa. Thay vòa đó, nó phải thông qua một cơ chế chuyển đổi ngữ cảnh được kiếm soát nghiêm ngặt
Khi một dngs udnjg cần thực hiện mọt tao tác như đọc file, nó gọi một `System call` cụ thể:
- Ứng dụng nạp các tham số cần thiết vào các than ghi CPU
- ứng dụng thực thi lệnh ,...
- CPU chuyển từ Ring 3 sáng Ring 0
- Quyền điền khiển được chuyển cho Kernel tại một địa chỉ bộ nhớ định trước
- Kernel kiểm tra tính hợp lệ của yêu cầu
- Kernel thực hiện tác vụ thay cho ứng dụng và trả lại kết quả
- CPU chuyển ngược lại về Ring 3 đẻ ứng dụng tiếp tục chạy
`Takeaway`: Việc chuyển đổi giữa User Space và Kernel Sapce tiêu tốn tài nguyên CPU, những ứng dụng hiệu năng cao thương giảm thiểu số lượng `System call` để tránh chi phí chuyển đổi ngữ cảnh không cần thiết
#### Tại sao kiến trúc Mônlithic lại hiệu quả
Dù có rủi ro nếu mộ thành phần tỏng Kernel bị lỗi, Linux vẫn hoin kién trúc `Monolithic` thay vì `Microkernel`(Nơi chi các dịch vụ tối thiểu nằm trong Kernel, còn lại chạy trong User space)
Lý do nằm ở hiệu ăng: Treong `Mônlithic kerna, cácd thành phần quyanr lý bộ nhớ file sýtyem, driver` liện liacj với nah hthoong qua lời gọi hàm trụctieeps trong bộ nhớ. Tỏng kiến tủvcMicrokernel các thành phần phải giao tiếp thông qua cơ chế truyền tin `IPC inter-process communication`, vốn châmh hơn rất nhbieef udo phải chuyển đổi ngữ cảnh liên tục
Linux quản lý sự phức tạp bằng cách đặt "bức tường" Ring 3/Ring 0 giữa người dùng và phần cứng. Mọi tương tác quan trọng đều phải đi qua System Call. Việc hiểu rõ ranh giới này giúp bạn định hình được tại sao các tiến trình đôi khi ở trạng thái "System Wait" (chờ đợi Kernel phản hồi) và tại sao các lỗi phần mềm lại có mức độ ảnh hưởng khác nhau lên hệ thống. Chúng ta sẽ đào sâu vào cơ chế chuyển đổi này trong phần tới.
![[Pasted image 20260322094411.png]]
![[Pasted image 20260322094534.png]]
![[Pasted image 20260322094545.png]]
