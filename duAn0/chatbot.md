KẾ HOẠCH & LỘ TRÌNH TRIỂN KHAI DỰ ÁN TRỢ LÝ TRI THỨC NỘI BỘ
Tóm tắt Dự án
Dự án nhằm xây dựng một hệ thống Trợ lý AI (Chatbot) để tra cứu tài liệu nội bộ, giúp nhân viên tiếp cận thông tin một cách nhanh chóng, chính xác. Báo cáo này sẽ trình bày chi tiết về các yêu cầu hạ tầng và lộ trình triển khai theo 4 giai đoạn chính trong 12 tuần.
Định hướng thiết kế:
Định hướng xây dựng một hệ thống AI dựa trên dữ liệu, cách tiếp cận "data-centric" (lấy dữ liệu làm trung tâm).
Bước 1: Lựa chọn Embedding Models 
•	Mục tiêu: Đây là bước khởi đầu quan trọng nhất. Việc thử nghiệm trên chính dữ liệu nội bộ sẽ đảm bảo mô hình được chọn thực sự hiểu "ngôn ngữ" của Công ty. Lựa chọn embedding models để đưa ra embedding models tốt nhất cho việc xử lý tài liệu nội bộ bằng cách cho một vài bài test với nhiều embedding models trên một số dữ liệu nội bộ, chấm điểm và so sánh kết quả, đưa ra 2-3 embedding models tốt nhất đưa vào bước sau.
•	Định hướng kỹ thuật: Khi test, tập trung vào các chỉ số như hit rate (tỷ lệ truy xuất đúng tài liệu trong top K kết quả) và MRR (Mean Reciprocal Rank). Nên chuẩn bị một bộ câu hỏi và câu trả lời mẫu (Q&A dataset) để việc chấm điểm được khách quan.
Bước 2: Thiết kế cấu trúc cơ sở dữ liệu (metadata) 
•	Mục tiêu: Việc này thường bị bỏ qua nhưng lại cực kỳ quan trọng cho việc lọc và phân quyền. Đưa ra cấu trúc cơ sở dữ liệu phù hợp với loại tài liệu nội bộ, kiểm tra với các dữ liệu mẫu. Có thể đưa ra nhiều kiến trúc cơ sở dữ liệu khác nhau để dễ tra cứu và lưu trữ nếu kiểu dữ liệu quá khác nhau nhưng hệ quản trị thì chỉ có 1.
•	Định hướng kỹ thuật: Cấu trúc này nên tập trung vào metadata (siêu dữ liệu). Ví dụ, mỗi chunk/document nên có các trường như: document_id, source_file, version, department_owner, author, last_updated, và quan trọng nhất là access_level (VD: "public", "employee_only", "manager_only", "rd_department").
Bước 3: Xây dựng hệ quản trị cơ sở dữ liệu 
•	Mục tiêu: Việc tách biệt các CSDL theo nghiệp vụ (bán hàng, kỹ thuật) nhưng thống nhất qua một API là một thiết kế linh hoạt và dễ mở rộng. Xây dựng hệ quản trị cơ sở dữ liệu theo thiết kế cấu trúc ở bước 2, có phân quyền và API để module khác kết nối tới.
•	Định hướng kỹ thuật: Ví dụ cần làm rõ ở đây chúng ta có 2 loại CSDL: 
1.	Vector Database (VD: FAISS, Chroma, Weaviate): Để lưu trữ các embeddings và thực hiện tìm kiếm ngữ nghĩa.
2.	Relational Database (VD: PostgreSQL): Để lưu trữ metadata (ở bước 2) và quản lý người dùng, phân quyền. Hệ quản trị sẽ phải tích hợp và điều phối cả hai.
Bước 4: Xây dựng công cụ chuyển đổi raw -> clean data 
•	Mục tiêu: 
Việc 1 là xây dựng một vài tài liệu mẫu sạch, loại tài liệu này có thể thiết kế ngay từ đầu làm tài liệu mẫu cho cả hệ thống. 
Việc 2 là giao công cụ và mẫu cho các phòng ban tự làm sẽ giảm tải cho đội dự án và tăng tính chủ động cho các bên.
Tài liệu sau xử lý chính là tài sản có thể cất đi và sử dụng cho mọi hệ thống khác về sau nên sạch vẫn phải đảm bảo tính thô để có thể ứng dụng vào nhiều mục đích khác nhau hoặc các bước còn lại thất bại thì bước này vẫn không phải làm lại.
•	Định hướng: Công cụ này nên là một web form hoặc một template có cấu trúc, giúp người dùng điền các trường metadata (ở bước 2) một cách dễ dàng và bắt buộc.

Bước 5: Xây dựng công cụ đánh giá dữ liệu clean 
•	Mục tiêu: Đây là chốt chặn đảm bảo chất lượng, xây dựng công cụ đánh giá dữ liệu clean hay mơ hồ, trùng lặp. Đầu ra bước này là một dạng tài liệu sạch như việc 1 đã làm ở bước 4. 
•	Định hướng kỹ thuật: Công cụ này sẽ tích hợp cả Embedding Models (để quét trùng lặp ngữ nghĩa) và LLM (để quét các câu mơ hồ, mâu thuẫn). Kết quả nên được hiển thị trực quan để phòng ban dễ dàng sửa lỗi.
Bước 6: Xây dựng module nạp dữ liệu (Ingestion Pipeline) 
•	Mục tiêu: xây dựng module nạp dữ liệu ở bước 5 vào cơ sở dữ liệu ở bước 2, tương thích hệ quản trị cơ sở dữ liệu ở bước 3. Ban đầu sẽ nạp dữ liệu sạch mẫu.
•	Định hướng: Module này sẽ tự động hóa các bước: Chunking (tách nhỏ tài liệu) -> Embedding (vector hóa) -> Lưu trữ (đẩy vector vào Vector DB và metadata vào Relational DB).

Bước 7: Xây dựng lõi truy xuất và tổng hợp (RAG Core Engine) 
•	Mục tiêu: Đây là bộ não xử lý logic chính của hệ thống, nằm giữa CSDL và Chatbot UI.
•	Định hướng chức năng:
Tiếp nhận câu hỏi từ người dùng và thông tin phân quyền của họ.
Truy xuất (Retrieval): Dùng Embedding Model đã chọn (bước 1) để tìm kiếm các văn bản liên quan nhất trong Vector DB, đồng thời lọc kết quả dựa trên quyền truy cập của người dùng từ Relational DB.
Tổng hợp (Synthesis): Xây dựng "siêu câu lệnh" (mega prompt) bao gồm câu hỏi của người dùng và ngữ cảnh đã truy xuất được.
Tạo sinh (Generation): Gọi đến LLM (nội bộ hoặc bên ngoài) để tạo ra câu trả lời cuối cùng.
Cung cấp API: Tạo ra một API endpoint duy nhất (ví dụ: /ask) để module chatbot ở bước 8 có thể gọi tới.
Bước 8: Xây dựng giao diện chatbot (UI) và tích hợp 
•	Mục tiêu: là bước cuối cùng, kết nối chatbot vào hệ cơ sở dữ liệu để lấy thông tin (chatbot sẽ là một module riêng, tương tác với API của hệ cơ sở dữ liệu).
•	Định hướng: tập trung vào việc xây dựng giao diện người dùng (khung chat, hiển thị lịch sử,...) và gọi đến API /ask đã được xây dựng ở bước 7. Không cần biết logic phức tạp bên trong CSDL hay RAG Core.

Phân bổ công việc: song song và nối tiếp
Các luồng có thể thực hiện SONG SONG :
•	Luồng 1: Nghiên cứu Model & Dữ liệu (Research)
o	Bước 1: Lựa chọn Embedding Models
o	Bước 2: Thiết kế Cấu trúc CSDL (Metadata)
•	Luồng 2: Xây dựng Nền tảng & Công cụ (Platform & Tools)
o	Bước 3: Xây dựng Hệ quản trị CSDL
o	Bước 4: Xây dựng Công cụ Raw -> Clean Data
•	Luồng 3: Phát triển Giao diện (Frontend)
o	Bước 8 (phần UI): Xây dựng Giao diện Chatbot có thể bắt đầu sớm, làm việc với các API giả (mock API).
Các công đoạn cần thực hiện NỐI TIẾP :
1.	Hoàn thành Nền tảng CSDL (Bước 3) là điều kiện tiên quyết cho hầu hết các bước sau.
2.	Chuỗi công cụ xử lý dữ liệu: Bước 4 -> Bước 5 -> Bước 6 phải thực hiện tuần tự.
3.	Xây dựng Lõi RAG (Bước 7) là bước tích hợp lớn nhất. Nó đòi hỏi:
o	Đã chọn được Embedding Model (Bước 1).
o	CSDL đã sẵn sàng (Bước 3).
o	Đã có dữ liệu mẫu được nạp vào (Bước 6).
4.	Tích hợp cuối cùng (Bước 8): Kết nối UI Chatbot thật vào API của Lõi RAG (Bước 7) là bước cuối cùng sau khi mọi thứ đã sẵn sàng.
