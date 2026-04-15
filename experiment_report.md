# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600072
**Name:** Hoàng Sơn Lâm
**Date:** 2026-04-15

---

## 1. Kết quả thí nghiệm

Chạy `agent_simulation.py` với 2 bộ dữ liệu và ghi lại kết quả:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Trả lời chính xác, Laptop là sản phẩm electronics đắt nhất trong dữ liệu sạch |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 1 | Trả lời sai hoàn toàn, chọn outlier vô nghĩa làm kết quả |

---

## 2. Phân tích & nhận xét

### Tại sao Agent trả lời sai khi dùng Garbage Data?

Khi sử dụng garbage data, Agent đã trả lời hoàn toàn sai vì dữ liệu đầu vào chứa nhiều vấn đề nghiêm trọng về chất lượng. Thứ nhất, dữ liệu có Duplicate IDs (id=1 xuất hiện 2 lần với sản phẩm khác nhau), khiến Agent không thể phân biệt đâu là bản ghi chính xác. Thứ hai, có wrong data types như giá "ten dollars" thay vì số, gây lỗi khi tính toán. Thứ ba, outlier cực lớn như Nuclear Reactor giá 999999 đã làm lệch toàn bộ kết quả phân tích vì Agent đơn giản chỉ tìm sản phẩm có giá cao nhất. Thứ tư, null values (id=None, category=None) gây ra các bản ghi không hợp lệ làm nhiễm dữ liệu. Tất cả các vấn đề này chứng tỏ rằng nếu không có bước validation và cleaning dữ liệu trước khi đưa vào Agent, kết quả trả về sẽ hoàn toàn không đáng tin cậy, bất kể prompt có tốt đến đâu.

---

## 3. Kết luận

**Quality Data > Quality Prompt?** Đồng ý. Dữ liệu chất lượng quan trọng hơn prompt chất lượng. Như thí nghiệm đã chứng minh, cùng một câu hỏi và cùng một logic xử lý, Agent cho kết quả chính xác với dữ liệu sạch nhưng trả lời vô nghĩa với dữ liệu rác. Một pipeline ETL với bước validation là bắt buộc để đảm bảo chất lượng đầu ra của bất kỳ hệ thống AI nào.
