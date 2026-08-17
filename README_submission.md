# Báo cáo Lab 17: Multi-Memory Agent với Zep

## 3 Câu hỏi bắt buộc (Control Plane & Architecture)

1. **Layer quan trọng nhất trong bộ test này:**
   **Long-term memory** là layer quan trọng nhất trong bộ test này vì nó chiếm số lượng case nhiều nhất (E02, E03, E08, E09) và quản lý các thông tin cá nhân hóa (preferences, facts, constraints) kéo dài qua nhiều session của user.

2. **Trade-off giữa Context Block / Zep vs Redis + Qdrant:**
   Zep đóng vai trò như một Managed Memory Backend cung cấp sẵn Context Block (tổng hợp summary và facts một cách tối ưu, tự động cập nhật), giúp lập trình viên không phải tự xây dựng data pipeline phức tạp. Tuy nhiên, trade-off là phụ thuộc vào Zep Cloud API với độ trễ mạng cao hơn so với việc tự vận hành Redis (state lưu local) và Qdrant (vector DB) tại môi trường nội bộ, đồng thời ít quyền kiểm soát luồng nội bộ hơn.

3. **Guardrail chống memory poisoning:**
   Để chống memory poisoning, hệ thống sử dụng **Compiled KB** được curated riêng (ví dụ `data/knowledge.jsonl`) cho tri thức dùng chung (semantic), ngăn không cho user chèn prompt injection làm sai lệch chính sách (như rules về retry payment). Ngoài ra, policy giới hạn quyền hạn ghi đè dữ liệu của user vào system logic.

## Phân tích kết quả Benchmark

1. **Layer có hit rate thấp nhất (trong no-memory baseline):**
   Trong khi mô hình `student` đạt hit rate 100% ở mọi layer, mô hình `no_memory` có hit rate 0% ở tất cả các layer `long_term`, `episodic`, và `semantic`, chỉ pass được `short_term`.

2. **Query retrieve nhiều token nhất:**
   Theo `benchmark.md`, query **E03** (`Minh con open loop hay deadline nao chua hoan thanh?`) retrieve nhiều token nhất với **857 tokens**, theo sát là E02 với 856 tokens do phải lấy nhiều ngữ cảnh `long_term` tổng hợp.

3. **Case mixed (E07) kết hợp những memory nào? Evidence bắt buộc:**
   Case E07 kết hợp **long-term memory** (để biết user Minh prefer ngôn ngữ `Python`) và **semantic memory** (để lấy policy quy tắc retry payment `Idempotency-Key`). Evidence bắt buộc phải có để PASS là: `['Python', 'Idempotency-Key']`.

4. **Token reduction và hit rate của no-memory baseline:**
   Token reduction trung bình của bản student là **19.1%**. Bản `no-memory` có token reduction rất cao (**81.8%**) do nó gần như drop toàn bộ memory của các session trước. Tuy tiết kiệm token tối đa, cách này đánh đổi bằng hit rate thảm hại (chỉ **18.2%**) vì agent không còn đủ context để trả lời đúng câu hỏi dựa trên lịch sử.

## Hiểu về Scope-specific Conflict & Durable Constraint
- **E08 Recency (Xung đột ưu tiên):** Khi user thay đổi backend từ Python sang TypeScript cho project BLUEBIRD-42, Zep xử lý theo quy tắc *recency wins* (ưu tiên thông tin mới nhất). Nhờ đó, context block lấy đúng TypeScript cho dự án này thay vì sở thích Python ban đầu.
- **E10 Compaction (Rút gọn bộ nhớ):** Cơ chế sliding window đã loại bỏ các đoạn chat filler dài dòng (giảm token), nhưng vẫn bóc tách và lưu giữ an toàn mốc thời gian quan trọng (`REVIEW-DEADLINE-1600`) vào `DURABLE_NOTES`, đảm bảo không mất constraint cốt lõi.
