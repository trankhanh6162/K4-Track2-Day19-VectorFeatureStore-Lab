# Reflection — Lab 19

**Tên:** Trần Ngọc Khánh
**Mã sinh viên:** 2A202602923
**Cohort:** A20-K4
**Path đã chạy:** lite

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

Trên golden set 50 queries, hybrid đạt Precision@10 cao nhất (78,6%), so
với BM25 77,8% và vector 73,2%. Với `exact`, BM25 và hybrid cùng đạt 96,7%
vì từ khóa kỹ thuật xuất hiện trực tiếp trong corpus. Với `mixed`, hybrid
thắng rõ nhất (100%), do kết hợp tín hiệu lexical của BM25 và tín hiệu ngữ
nghĩa của vector. Riêng `paraphrase`, kết quả lite lần này cho thấy BM25
33,3%, hybrid 32,0% và vector 24,0%. Nguyên nhân là model
`BAAI/bge-small-en-v1.5` chủ yếu được huấn luyện cho tiếng Anh nên biểu diễn
paraphrase tiếng Việt chưa tốt; một model multilingual phù hợp có thể đảo
chiều kết quả này.

Tôi không dùng hybrid khi truy vấn là mã lỗi, ID hoặc thuật ngữ cần khớp
chính xác, vì BM25 nhanh hơn và đủ tốt. Tôi chọn pure vector khi người dùng
diễn đạt tự nhiên, từ vựng khác corpus và model embedding đã được đánh giá
tốt trên tiếng Việt. Hybrid phù hợp nhất khi traffic có nhiều loại query và
cần chất lượng ổn định hơn là latency tối thiểu.

---

## Điều ngạc nhiên nhất khi làm lab này

Model embedding ảnh hưởng trực tiếp đến chất lượng retrieval: semantic
search không tự động thắng paraphrase nếu model không phù hợp ngôn ngữ.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_
