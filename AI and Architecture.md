### Cẩm nang Prompt Engineer

#### Kỹ sư AI
Prompt engineer không chỉ là mọt kỹ năng mới mẻ mà còn là một nghề nghiệp đang bùng nổ với mức thu nhập khủng lên đến 335.000USD/y/. Điều thú vị là bạn khong nhất thiết phải có nền tảng lập trình đeer làm chủ lĩnh vực này. Tại sao các doanh nghiệp lại seaxn sàng chi trả lương cao như vậy? Đó là vì sự `Sự mờ mịt(opaqueness)` trong ác hcacs mô hình AI vận hành bên dưới hệ thống; các công ty cần những chuyên gia có thể điều khiển `chiếc hộp đen` đó để tạo ra kết quả chính xác nhất.
=> `Prompt engineering involves human writing, refining, and optimizing prompts in a structured and way to perfect the interaction between humans and AI to the highest degree posible`
Ba nhiệm vụ cốt lõi:
+ `Theo dõi hiệu quả`: Liên túc giám sát và đảm bảo các câu lệnh vẫn haowjc động tốt khi AI tến hóa theo thời gian
+ `Duy trì thư viện câu lệnh`: Xây dựng và cập nhật kho lưu trữ các câu lệnh mẫu tối ưu cho tổ chức
+ `Lãnh đạo tư duy`: Báo cáo các phát hiện mới và định hướng chiến lược sử dụng AI hiệu quả
=> `Hãy xem việc viết câu lệnh như kỹ năng Googling. Các đây vài năm, chúng ta phải học cách chọn từ khóa để tìm kiếm hiệu quả. Prompt Engineering cũng vậy - đó là sự chuyển đổi từ việc đặt câu hỏi hteo trực giác sang một quy trình có chiếc lược và chuyên sâu`
#### Giải mã AI
AI thực tế là một sự mô phỏng (simulation) trí tuệ con người chứ không phải là một thực thể có tri giác(sentient). Khi chúng ta nói về ChatGPT, thực chất là đang nói về Machine Learning(Học máy) - một hệ thống dự đoán dựa trên các mẫu (patterns) từ dữ liẹu khổng lồ để đưa ra kết quả.
Dưới đây alf sự tién háo từ những ảo thuật sơ khai đến các mô hình ngôn ngữ lớn (LLM) hiện đại;

Cơ chế hoạt động 
|Đặc điểm|AI Truyền thống (Ví dụ: Eliza/Shudlu)|LLM Hiện đại (Ví dụ: GPT-4)|
|---|---|---|
|**Cơ chế hoạt động**|Dựa trên quy tắc (rules) và khớp mẫu (pattern matching) cứng nhắc.|Dự đoán từ ngữ tiếp theo dựa trên xác suất từ dữ liệu khổng lồ.|
|**Khả năng hiểu**|Tạo ra ảo giác về sự thấu hiểu thông qua các mẹo lập trình.|Nắm bắt ngữ nghĩa và ngữ cảnh sâu sắc nhờ hàng tỷ tham số.|
|**Tính linh hoạt**|Giới hạn trong kịch bản hẹp (như trị liệu tâm lý hoặc xếp khối).|Đa năng: Viết lách, lập trình, giải toán và tư vấn chuyên sâu.|
- **2010:** Kỷ nguyên của **Deep Learning** bắt đầu bùng nổ mạnh mẽ.
- **2018:** OpenAI giới thiệu **GPT-1**, bắt đầu hành trình chinh phục ngôn ngữ.
- **2020:** **GPT-3** xuất hiện với **175 tỷ tham số**, thay đổi hoàn toàn cách thế giới nhìn nhận về AI.
**AI chỉ làm một hệ thống dự đoán xác suất, chúng ta sẽ thấy ngông ngữ học chính là chìa khóa để điều hướng những dự đoán đó đi đúng lộ trình**
#### Ngôn ngữ học(Linguistics)
Ngôn ngữ học là nền tảng của `Prompt Engineer`. `AI được huấn luyện trên khối lượng dữ liệu khổng lồ tuân theo các cấu trúc ngôn ngữ chuẩn hóa`. Vì vậy, khi bạn sử dụng ngôn ngữ chuẩn mực và đúng cấu trúc, AI sẽ dễ dàng khớp câu lệnh của bạn với dữ liệu chất lượng cao nhất mà nó sở hữu
Dưới đây là 04 khái niệm ngôn ngữ học then chốt: 
1. Syntax(Cấu trúc câu): Cách sắp xếp từ ngữ để tạo thành câu đúng ngữ pháp. AI phản hồi tốt hơn khi câu lệnh có cấu trúc mạch lạc
2. Sematics(Ngữ nghĩa):Tạp trung vào ý nghĩa của từ ngữ. Chọn từ chính xác giúp AI hiểu đúng ý định thay vì hiểu nhầm sang các từ đồng âm khác nghĩa
3. Pragmatics(Ngữ cảnh): Cách ngôn ngữ thay đổi tùy theo tình huống. Cung cấp ngữ cảnh giúp AI chọn tông giọng và phong cách phù hợp nhất
4. Computational Linguistics(Ngôn ngữ học tính toán): Cầu nối giữa ngôn ngữ tự nhiên và các h máy tính xử lý dữ liệu
#### Kỹ thuật cốt lõi
`Zero-shot Prompting(câu lệnh không mẫu)`
Đây làm ột kỹ thuật đặt lệnh mà không cung cấp ví dụ, dựa hao toàn vào kiến thức sẵn có của AI
`Khi nào là ngày Giáng sinh ở Mỹ?`
`Flew-shot Prompting(Câu lệnh có mẫu)`
Kũ thuạt này `huấn luyện` AI tức thì bằng cách cung cấp vài ví dụ. Hãy xem sự khác biệt qua ví dụ về sở thíchcuar Ania:
Bước 1(`Zero-shot failure`): Nếu ta muốn hỏi: "Món ăn yêu thích của Anina là gì?", AI sẽ trả lời: `Tôi không biết Ania là ai và sở thích của cô ấy`
Bước 2 (Few-shot prompting): Bạn cung cấp dữ liệu "Sở thích của Ania là burger, khoai tây chiên và pizza". Dựa vào đó, hãy gợi ý một nhà hàng tại Dubai cho cô ấy cuối tuần này. AI sẽ ngay lập tứcddeef xuất các quán burge hoặc pizza nổi tiếng tại Dubai thay vì gợi ý chung chung
`Lưu ý về cái giá cảu câu lệnh`: `Tokens` mọi tương tác đều tốn Tokens(đơn vị tính toán)
- Quy tắc: 1 Token sắp xỉ 4 kỹ tự hoặc 0.5 từ tiếng Anh
- Quản lý: Bạn có thể dugnf `Tokenizer tool` để đo lường độ dài lệnh và kiemer tra chi phí trong phần Account/Billing của hệ thống AI. Viết lệnh ngắn gọn, síc tích là cách tốt nhất để tiết kiệm tài nguyên và tiền bạc
=> `Dù kỹ thuật có tốt đến đâu thì ta phải luôn cảnh giác rằng là AI có thể *Nằm mơ giữa ban ngày*` 
#### Cảnh giác với Hallucination (Ảo tưởng AI)
Hallucination là hiện tương AI tạo ra thông tin sai lệch nhưng trình bày cực kỳ tự tin. Điều này xảy ra khi AI `vượt mức và tăng cường các mẫu` *`Over-interpreting and enhancing patterns`*
để lấp đầy khoảng trống dữ liệu. Ví dụ điển hình là dự án `Deep Dream của Google` , nơi AI tự ý "điền" thêm các khuôn mặt chó vào hình ảnh một cách kỳ dị

[!CAUTION] Cảnh báo: `AI có thể bịa đặt trắng trợn về các nhân vật lịch sử hoặc sự kiện nếu không có dữ liệu thực tế. Đừng bao giờ tin tưởng tuyệt đối mà không có bước kiểm chứng lại`
02 lời khuyên để giảm thiểu ảo tưởng:
1. `Cung cấp dữ liệu thực`: Hãy dán nội dung văn bản cụ thể và yêu cầu AI làm việc trên đó thay vì để nó tự tìm kiến thức
2. `Kiếm chứng độc lập`: Luôn đối chiếu các con số, tên gọi và mốc thời gian với các nguồn tin cậy
#### Bộ quy tắc vàng để viết câu lệnh hiệu quả
1. `Cung cấp chi tiết cụ thể`: Đừng giả định AI biết những gì ta nghĩ
	- `Viết code lọc tuổi từ dữ liệu`. (Sai. AI có thể đưa ra Python trong khi ta đang cần JS)
	- `Viết một hàm Js nhận 1 mảng đối tượng và lọc thuộc tính *age* vào một mảng mới. Giả thích từng bước code`
2. `Sử dụng Persona(vai trò)`: `Gán cho AI một danh tính rõ ràng`. Ví dụ `Hãy đóng vai là một giáo viên tiếng Anh bản ngữ` hoặc `Viết một bài thơ theo phong cách của William Sakespeare` 
3. `Chỉ định định dạng đầu ra`: Nêu rõ bạn muốn kết quả đầu ra là gì, checklist, Bullet points, hay bảng so sánh
4. `Đặt câu lệnh lặp lại(iterative Prompting)`: AI có khả năng xây dựng dựa trên lịch sử đối thoại. Ví dụ: 4+4 bằng mấy. AI trả lời sau đó bạn hỏi nó cộng thêm 5 thì nó lấy ngữ cảnh trước để trl tiếp
5. `Tránh dẫn dắt (Avoid Leading)`:  Đừng đặt câu hỏi khiến AI thiên vị theo định kiến các nhân của bạn. Hãy để AI đưa ra nhận định khách quan nhất
#### Phía sau những con chữ: Vectors và Text Embeddings
