# Ví dụ: Từ "Tôi muốn tạo chatbot agent" đến tài liệu SRS hoàn chỉnh

Dưới đây là ví dụ minh họa quá trình sử dụng prompt "Chuyên Gia Đặc Tả và Khai Thác Yêu Cầu Phần Mềm" để chuyển đổi một yêu cầu mơ hồ thành tài liệu SRS đầy đủ.

## Đầu vào ban đầu

> "Tôi muốn tạo chat bot agent."

## Quá trình đặt câu hỏi của AI

### Bước 1: Đánh giá thông tin ban đầu

AI: "Cảm ơn bạn đã chia sẻ ý tưởng về việc tạo chatbot agent. Để có thể hỗ trợ bạn tốt hơn trong việc xác định yêu cầu cho dự án này, tôi có một số câu hỏi muốn hỏi bạn:

1. "Bạn có thể mô tả chi tiết hơn về mục đích chính của chatbot agent này không? Ví dụ như nó sẽ được sử dụng trong lĩnh vực nào (chăm sóc khách hàng, hỗ trợ bán hàng, trợ lý cá nhân, v.v.)?"
2. "Đối tượng người dùng chính của chatbot là ai? Họ có đặc điểm gì đặc biệt mà chúng ta cần lưu ý không?"
3. "Bạn đã có ý tưởng về các tính năng chính mà chatbot cần có chưa? Nếu có, bạn có thể liệt kê một vài tính năng quan trọng nhất không?"

### Bước 2: Đặt câu hỏi khám phá (sau khi người dùng trả lời)

User: "Chat bot để hỗ trợ developer quản lý task, tương tác được với JIRA, Slack, Confluence"

AI: "Cảm ơn bạn đã cung cấp thêm thông tin về mục đích của chatbot. Tôi hiểu rằng bạn muốn tạo một chatbot để hỗ trợ developer quản lý task, có khả năng tương tác với JIRA, Slack và Confluence. Đây là một ý tưởng rất thú vị và hữu ích. Để làm rõ thêm về yêu cầu của bạn, tôi có một số câu hỏi:

1. "Bạn có thể chia sẻ thêm về các tác vụ cụ thể mà bạn muốn chatbot thực hiện không? Ví dụ như tạo task mới trên JIRA, cập nhật trạng thái task, gửi thông báo qua Slack, hay tìm kiếm thông tin trên Confluence?"
2. "Chatbot này sẽ được tích hợp chủ yếu vào nền tảng nào? Ví dụ: nó sẽ là một bot Slack, một ứng dụng web độc lập, hay được tích hợp trực tiếp vào JIRA?"
3. "Bạn có yêu cầu cụ thể nào về bảo mật và quyền truy cập không? Ví dụ như xác thực người dùng, giới hạn quyền truy cập vào các dự án cụ thể trên JIRA?"

### Bước 3: Đặt câu hỏi làm rõ

User: "Ứng dụng web độc lập, jira thì xem task, cập nhật task, slack thì tóm tắt các thread dài, tự quan sát nội dung chat để logwork trên jira cho phù hợp..."

AI: "Cảm ơn bạn đã chia sẻ thêm chi tiết quan trọng. Để xây dựng chatbot đáp ứng chính xác yêu cầu, tôi cần làm rõ một số điểm sau:

#### Tích hợp Confluence
Bạn có muốn chatbot thực hiện các thao tác với Confluence không? Ví dụ:
- Tự động tạo/link tài liệu từ nội dung chat Slack
- Tìm kiếm thông tin trong Confluence khi developer hỏi
- Đồng bộ ghi chú công việc giữa JIRA và Confluence

#### Xử lý ngôn ngữ tự nhiên (NLP)
Với tính năng tự logwork dựa trên nội dung chat Slack:
- Bạn muốn chatbot phân tích theo cách nào?
  - Dựa trên từ khóa (ví dụ: "đã fix bug API" → log 2h vào task tương ứng)
  - Sử dụng AI để hiểu ngữ cảnh (ví dụ: "Mất 3h debug lỗi X" → tự động gán vào task JIRA có liên quan)
- Có cần xác nhận lại với user trước khi log work không?

#### Quyền truy cập và bảo mật
- Cơ chế xác thực bạn muốn sử dụng:
  - OAuth2 cho JIRA/Slack
  - API token
  - SSO (Single Sign-On)
- Phân quyền chi tiết:
  - Ai được phép tạo task mới?
  - Giới hạn quyền chỉnh sửa task theo role (Developer/PM/Admin)?"

### Bước 4: Đặt câu hỏi đào sâu và xác nhận

User: "Confluence thì trước mắt là tạo report tiến độ. Lấy thông tin từ jira và slack nếu cần. Slack thì hãy phân tích ngữ cảnh qua các đoạn chat để phán đoán task và số giờ."

AI: "Cảm ơn bạn đã làm rõ thêm yêu cầu. Dựa trên thông tin bạn cung cấp, tôi sẽ phân tích và đề xuất các tính năng chính cho chatbot, đồng thời đặt thêm một số câu hỏi để đảm bảo thiết kế hệ thống đáp ứng đúng nhu cầu của bạn."

*AI phân tích các yêu cầu và đặt các câu hỏi bổ sung:*

"### Về JIRA
1. Bạn có muốn chatbot hỗ trợ tạo mới task trên JIRA hay chỉ xem và cập nhật các task hiện có?
2. Khi log work tự động từ Slack, bạn có muốn chatbot gửi thông báo xác nhận trước khi ghi vào JIRA không?

### Về Slack
3. Bạn có yêu cầu cụ thể nào về cách tóm tắt thread không? Ví dụ: chỉ tóm tắt các thread có hơn X tin nhắn hoặc có mention đến bot?
4. Với tính năng phân tích ngữ cảnh, bạn muốn chatbot hoạt động như thế nào nếu không thể xác định được task liên quan? 
   - Hỏi lại user?
   - Ghi chú lại để xử lý sau?

### Về Confluence
5. Báo cáo tiến độ cần được cập nhật theo lịch (ví dụ: hàng tuần) hay theo yêu cầu thủ công từ người dùng?
6. Bạn muốn báo cáo ở mức độ chi tiết như thế nào? Ví dụ:
   - Báo cáo theo từng cá nhân hay tổng quan cả team?
   - Có cần biểu đồ minh họa không (ví dụ: biểu đồ Gantt hoặc biểu đồ Burn-down)?"

User: "Về JIRA, cần gửi thông báo xác nhận. Về slack, nếu AI không thể quyết định, hãy hỏi user. Nói chung là có human in the loop trong tất cả các case không quyết định được. Report trên confluence thì report cả team. Tôi đang hình dung là có cơ chế Agent gì gì đó đang thịnh hành ấy"

AI đề xuất công nghệ và kiến trúc cụ thể:

"Cảm ơn bạn đã làm rõ các yêu cầu bổ sung. Dựa trên thông tin của bạn, tôi sẽ điều chỉnh thiết kế chatbot để đảm bảo có cơ chế "Human-in-the-loop" trong mọi trường hợp không thể tự động quyết định, đồng thời tích hợp các tính năng báo cáo cho cả team trên Confluence. Ngoài ra, tôi sẽ đề xuất cách sử dụng cơ chế Agent-based architecture để triển khai chatbot."

*AI mô tả chi tiết về Agent-based Architecture và đề xuất một số framework như Rasa, LangChain hoặc Dialogflow CX.*

User: "Lang chain và openai. Hỗ trợ đa ngôn ngữ."

AI: "Cảm ơn bạn đã lựa chọn LangChain và OpenAI làm công nghệ cốt lõi, đồng thời yêu cầu hỗ trợ đa ngôn ngữ. Dựa trên các thông tin này, tôi sẽ điều chỉnh đề xuất kiến trúc và tính năng chatbot để phù hợp với định hướng công nghệ của bạn."

*AI mô tả chi tiết về kiến trúc sử dụng LangChain và OpenAI, cùng với khả năng hỗ trợ đa ngôn ngữ.*

User: "Ok, hãy tạo SRS"

## Tài liệu SRS cuối cùng

Sau khi hoàn thành quá trình đặt câu hỏi, AI tạo ra tài liệu SRS hoàn chỉnh như sau:

```
# Software Requirements Specification (SRS)  
**Hệ thống:** Chatbot Agent hỗ trợ Developer quản lý task  
**Ngày:** 21/03/2025  

## 1. Giới thiệu

### 1.1 Mục đích
Chatbot agent được thiết kế để hỗ trợ các developer trong việc quản lý task, tự động log work, tóm tắt nội dung thread trong Slack, và tạo báo cáo tiến độ trên Confluence. Hệ thống sử dụng công nghệ LangChain và OpenAI GPT để phân tích ngữ cảnh và xử lý đa ngôn ngữ.

### 1.2 Phạm vi
Hệ thống sẽ là một ứng dụng web độc lập, tích hợp với các nền tảng:
- **JIRA**: Quản lý task và log work.
- **Slack**: Phân tích nội dung chat, tóm tắt thread, và hỗ trợ log work tự động.
- **Confluence**: Tạo báo cáo tiến độ cho cả team dựa trên dữ liệu từ JIRA và Slack.

### 1.3 Định nghĩa thuật ngữ
- **Task Agent**: Thành phần chịu trách nhiệm tương tác với JIRA.
- **Chat Analysis Agent**: Thành phần phân tích nội dung chat trong Slack.
- **Report Agent**: Thành phần tạo báo cáo tiến độ trên Confluence.
- **Human-in-the-loop**: Cơ chế yêu cầu xác nhận từ user khi AI không thể tự động quyết định.

## 2. Mô tả tổng quan

### 2.1 Mục tiêu hệ thống
- Tự động hóa quản lý task và log work cho developer.
- Tóm tắt thread dài trong Slack để tiết kiệm thời gian.
- Tạo báo cáo tiến độ chi tiết trên Confluence.
- Hỗ trợ đa ngôn ngữ để đáp ứng nhu cầu của các nhóm quốc tế.

### 2.2 Các ràng buộc
- Hệ thống phải tuân thủ chính sách bảo mật của JIRA, Slack, và Confluence.
- Chatbot phải hoạt động mượt mà trên giao diện web và Slack.
- Dữ liệu phải được xử lý nhanh chóng (thời gian phản hồi dưới 3 giây).

## 3. Yêu cầu hệ thống

### 3.1 Yêu cầu chức năng

#### 3.1.1 Tích hợp JIRA
- **FR-01**: Hiển thị danh sách task theo trạng thái (To Do, In Progress, Done).
- **FR-02**: Lọc task theo người thực hiện hoặc priority.
- **FR-03**: Chuyển đổi trạng thái task.
- **FR-04**: Thêm comment vào task.
- **FR-05**: Phân tích nội dung chat Slack để xác định task và số giờ làm việc.
- **FR-06**: Gửi thông báo xác nhận đến user trước khi log work vào JIRA.

#### 3.1.2 Tích hợp Slack
- **FR-07**: Tóm tắt thread dài có hơn X tin nhắn hoặc có mention đến bot.
- **FR-08**: Phân tích ngữ cảnh chat bằng OpenAI GPT.
- **FR-09**: Hỏi lại user khi không thể xác định task hoặc số giờ (Human-in-the-loop).
- **FR-10**: Gửi thông báo nhắc nhở log work.

#### 3.1.3 Tích hợp Confluence
- **FR-11**: Tạo báo cáo tiến độ cho cả team.
- **FR-12**: Bao gồm thông tin về task hoàn thành, task chậm tiến độ và giờ làm việc.
- **FR-13**: Báo cáo tự động theo lịch định kỳ hoặc theo yêu cầu.
- **FR-14**: Hỗ trợ xuất file PDF/Excel.

#### 3.1.4 Đa ngôn ngữ
- **FR-15**: Giao diện web chuyển đổi giữa các ngôn ngữ.
- **FR-16**: Báo cáo Confluence bằng ngôn ngữ do user chỉ định.

### 3.2 Yêu cầu phi chức năng
- **NFR-01**: Thời gian phản hồi dưới 3 giây.
- **NFR-02**: Xác thực OAuth2 với JIRA, Slack và Confluence.
- **NFR-03**: Mã hóa dữ liệu khi truyền tải.
- **NFR-04**: Uptime tối thiểu 99%.

## 4. Kiến trúc hệ thống

### 4.1 Tổng quan kiến trúc
Hệ thống sử dụng kiến trúc agent-based với các thành phần chính:
1. **Frontend**:
   - Giao diện web độc lập.
   - Tích hợp trực tiếp với Slack.
2. **Backend**:
   - Task Agent: Quản lý tương tác với JIRA.
   - Chat Analysis Agent: Phân tích nội dung chat bằng OpenAI GPT.
   - Report Agent: Tạo báo cáo trên Confluence.
   - NLP sử dụng LangChain kết hợp OpenAI GPT.
3. **Database**:
   - Lưu trữ lịch sử tương tác và dữ liệu báo cáo.

## 5. Kế hoạch triển khai

### Giai đoạn 1: Chức năng cơ bản
- Xem/cập nhật task trên JIRA.
- Tóm tắt thread dài trong Slack.

### Giai đoạn 2: Tự động hóa
- Phân tích nội dung chat để log work.
- Tạo báo cáo tiến độ cơ bản.

### Giai đoạn 3: Hoàn thiện
- Hỗ trợ đa ngôn ngữ.
- Báo cáo nâng cao với khả năng xuất file.

## 6. Rủi ro tiềm năng
1. Sai sót khi phân tích nội dung chat → giảm thiểu bằng Human-in-the-loop.
2. Quá tải API từ JIRA/Slack/Confluence → tối ưu hóa số lượng yêu cầu.
```

## Nhận xét

Từ một yêu cầu ban đầu chỉ có "Tôi muốn tạo chat bot agent", quá trình đặt câu hỏi có cấu trúc đã giúp:

1. Làm rõ mục đích và phạm vi của chatbot: Hỗ trợ developer quản lý task
2. Xác định nền tảng tích hợp cụ thể: JIRA, Slack, Confluence
3. Làm rõ các tính năng chi tiết: Xem/cập nhật task, phân tích chat để log work, tạo báo cáo tiến độ
4. Xác định yêu cầu kỹ thuật: Sử dụng LangChain, OpenAI, hỗ trợ đa ngôn ngữ
5. Xây dựng kiến trúc Agent-based phù hợp với yêu cầu

Kết quả là một tài liệu SRS hoàn chỉnh, có thể được sử dụng làm cơ sở cho việc phát triển sản phẩm. AI đã thành công trong việc biến một ý tưởng ban đầu mơ hồ thành một đặc tả kỹ thuật chi tiết thông qua việc đặt câu hỏi có cấu trúc và khai thác thông tin theo từng bước. 