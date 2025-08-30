# Tối ưu việc viết Requirement với AI: Từ mơ hồ đến chi tiết

### Trong bối cảnh phát triển sản phẩm ngày càng nhanh chóng và cạnh tranh khốc liệt như hiện nay, việc tối ưu hóa công đoạn khai thác và đặc tả yêu cầu bằng cách sử dụng AI là xu hướng tất yếu.

[](https://substack.com/@phucnt)

[Phúc](https://substack.com/@phucnt)

Mar 21, 2025

[](https://phucnt.substack.com/p/toi-uu-viec-viet-requirement-voi/comments)

Trong vai trò Product Owner (PO) hay Business Analyst (BA), chắc hẳn bạn đã từng gặp tình huống khách hàng hoặc stakeholder (hoặc chính bản thân mình) đưa ra những yêu cầu rất chung chung như:

> "Tôi muốn tạo một chatbot agent."

Thông thường, bạn sẽ cần tổ chức nhiều buổi họp, đặt hàng loạt câu hỏi, và mất rất nhiều thời gian để làm rõ yêu cầu trước khi có thể bắt đầu viết tài liệu yêu cầu phần mềm (Software Requirements Specification - SRS). Nhưng giờ đây, với sự hỗ trợ của AI, bạn hoàn toàn có thể tối ưu hóa quy trình này một cách nhanh chóng và hiệu quả.

[

![](https://substackcdn.com/image/fetch/$s_!aI6q!,w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F4404227c-720c-4cec-a440-3b57a599b660_1618x1128.png)

](https://substackcdn.com/image/fetch/$s_!aI6q!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F4404227c-720c-4cec-a440-3b57a599b660_1618x1128.png)

Trợ lý mà ai cũng cần (Ảnh tạo bởi AI)

## Prompt AI - "Chuyên Gia Đặc Tả và Khai Thác Yêu Cầu Phần Mềm"

Một trong những cách hiệu quả nhất để khai thác sức mạnh của AI chính là sử dụng một **prompt chuyên biệt** được thiết kế dành riêng cho việc đặc tả và khai thác yêu cầu phần mềm. Prompt này định hướng AI hoạt động như một **chuyên gia phân tích nghiệp vụ** với hơn 15 năm kinh nghiệm, thành thạo các chuẩn mực quốc tế như IEEE 830, IREB, ISO/IEC/IEEE 29148:2018 và các phương pháp luận Agile (User Stories).

Prompt này bao gồm các phần chính:

- **Giới thiệu vai trò và nhiệm vụ**: Xây dựng nhận thức cho AI về trách nhiệm, phạm vi công việc.

- **Kỹ năng đặt câu hỏi có cấu trúc**: Hướng dẫn AI cách đặt câu hỏi theo từng bước rõ ràng, từ tổng quan đến chi tiết.

- **Quy trình khai thác yêu cầu bài bản**: 5 bước từ đánh giá thông tin ban đầu tới khi tạo ra tài liệu yêu cầu hoàn chỉnh.

- **Tiêu chuẩn chất lượng yêu cầu**: Đảm bảo yêu cầu rõ ràng, cụ thể, ưu tiên rõ ràng và không mâu thuẫn.

**Nội dung prompt đầy đủ xem ở đây:** [Chuyên gia viết Requirement](https://github.com/phuc-nt/prompt_collection/blob/main/prompts/product-management/product_owner_srs_prompt.md)

## Từ ý tưởng mơ hồ đến tài liệu SRS hoàn chỉnh với AI

Hãy cùng xem qua một ví dụ thực tế để hiểu rõ hơn về hiệu quả của prompt này. Giả sử bạn bắt đầu với một yêu cầu rất chung chung:

> "Tôi muốn tạo chatbot agent."

Nếu không có sự hỗ trợ của AI, bạn sẽ phải tự mình đặt ra hàng loạt câu hỏi để làm rõ mục tiêu, đối tượng sử dụng, tính năng mong muốn,... Nhưng với prompt chuyên biệt này, AI sẽ chủ động đặt các câu hỏi có cấu trúc để khai thác thông tin từ bạn:

1. **Câu hỏi khám phá**:
   
   - "Bạn có thể mô tả chi tiết hơn về mục đích chính của chatbot này không?"
   
   - "Ai là người dùng chính? Họ mong đợi điều gì?"

2. **Câu hỏi làm rõ**:
   
   - "Bạn muốn chatbot tích hợp với nền tảng nào? Ví dụ JIRA, Slack hay Confluence?"
   
   - "Các tác vụ cụ thể mà chatbot cần thực hiện là gì?"

3. **Câu hỏi đào sâu và xác nhận**:
   
   - "Bạn muốn chatbot xử lý ngôn ngữ tự nhiên (NLP) theo cách nào?"
   
   - "Có cần xác nhận từ người dùng trước khi chatbot thực hiện hành động nào đó không?"

Chỉ sau vài lượt tương tác ngắn gọn như vậy, từ một ý tưởng ban đầu rất mơ hồ ("tạo chatbot agent"), bạn đã có ngay một tài liệu SRS hoàn chỉnh theo chuẩn IEEE 830:

- Mục tiêu dự án rõ ràng

- Các tính năng chi tiết (tích hợp JIRA xem/cập nhật task; Slack phân tích nội dung chat tự động log work; Confluence tự động tạo báo cáo tiến độ)

- Yêu cầu phi chức năng (hiệu suất phản hồi dưới 3 giây, bảo mật OAuth2)

- Kiến trúc hệ thống đề xuất (Agent-based với LangChain và OpenAI GPT)

- Lộ trình triển khai theo từng giai đoạn cụ thể

**Chi tiết về ví dụ xem ở đây:** [Từ "Tôi muốn tạo chatbot agent" đến tài liệu SRS hoàn chỉnh](https://github.com/phuc-nt/prompt_collection/blob/main/examples/product-management/chatbot_agent_srs_example.md)

## Những kỹ năng PO mà Prompt AI đang sử dụng

Việc sử dụng prompt chuyên biệt này chính là việc áp dụng các kỹ năng cốt lõi của một PO chuyên nghiệp:

**Khai thác yêu cầu (Elicitation)**: Prompt giúp AI đặt câu hỏi mở theo từng bước để làm rõ thông tin từ người dùng, từ nhu cầu tổng quát đến chi tiết cụ thể.

**Phân tích nghiệp vụ**: AI được hướng dẫn chuyển đổi thông tin thu thập từ người dùng thành các yêu cầu có cấu trúc, phân loại thành chức năng và phi chức năng một cách rõ ràng.

**Ưu tiên hóa**: Thông qua các câu hỏi định hướng, AI có thể giúp xác định mức độ ưu tiên của các tính năng, giúp stakeholder tập trung vào những yếu tố quan trọng nhất.

**Tài liệu hóa yêu cầu**: AI có khả năng tạo ra tài liệu SRS hoàn chỉnh theo chuẩn IEEE 830, đảm bảo tính chuyên nghiệp và đầy đủ thông tin.

**Giao tiếp hiệu quả**: Prompt hướng dẫn AI đặt câu hỏi đơn giản, dễ hiểu và phù hợp với người dùng cuối, tạo điều kiện thuận lợi cho việc thu thập thông tin chính xác.

## Lợi ích vượt trội khi sử dụng AI trong viết Requirement

Việc áp dụng AI vào quá trình viết requirement mang lại những lợi ích thiết thực:

- **Tiết kiệm thời gian**: Chỉ sau vài lượt tương tác ngắn gọn đã có ngay tài liệu SRS chi tiết.

- **Giảm thiểu sai sót & thiếu sót**: Với quy trình đặt câu hỏi bài bản giúp đảm bảo không bỏ sót thông tin quan trọng.

- **Tăng cường giao tiếp & cộng tác**: Các câu hỏi rõ ràng giúp stakeholder dễ dàng cung cấp thông tin chính xác.

- **Dễ dàng bắt đầu với các ý tưởng chưa rõ ràng**: Không cần chuẩn bị quá chi tiết ban đầu vẫn có thể nhanh chóng làm rõ yêu cầu.

## Làm thế nào để bắt đầu?

Để bắt đầu áp dụng ngay prompt này vào công việc của bạn:

1. Chuẩn bị một ý tưởng hoặc yêu cầu ban đầu dù chỉ là sơ bộ.

2. Nhập prompt vào công cụ AI (như ChatGPT hoặc Gemini).

3. Bắt đầu tương tác trả lời các câu hỏi do AI đặt ra.

4. Sau vài lượt tương tác ngắn gọn, bạn sẽ nhận được một tài liệu yêu cầu hoàn chỉnh.

## Kết luận

Trong bối cảnh phát triển sản phẩm ngày càng nhanh chóng và cạnh tranh khốc liệt như hiện nay, việc tối ưu hóa công đoạn khai thác và đặc tả yêu cầu bằng cách sử dụng AI là xu hướng tất yếu. Với prompt chuyên biệt này, bạn hoàn toàn có thể biến những ý tưởng ban đầu mơ hồ thành những tài liệu requirement chất lượng cao chỉ trong thời gian ngắn.

Hãy thử áp dụng ngay hôm nay để cảm nhận sự khác biệt!

## Tham khảo

1. Prompt đầy đủ: [Chuyên gia viết Requirement](https://github.com/phuc-nt/prompt_collection/blob/main/prompts/product-management/product_owner_srs_prompt.md)

2. Ví dụ ứng dụng thực tế: [Từ "Tôi muốn tạo chatbot agent" đến tài liệu SRS hoàn chỉnh](https://github.com/phuc-nt/prompt_collection/blob/main/examples/product-management/chatbot_agent_srs_example.md)
