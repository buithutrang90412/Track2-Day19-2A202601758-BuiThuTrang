# Reflection — Lab 19

**Tên:** _Bùi Thu Trang_
**Cohort:** _A20-K4_
**Path đã chạy:** _lite_

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

Trên golden set 50 queries:
- **BM25 thắng ở exact queries**: vì các thuật ngữ kỹ thuật, mã lỗi xuất hiện chính xác nguyên văn trong tài liệu.
- **Vector (Semantic) thắng ở paraphrase queries**: do dùng từ đồng nghĩa, cấu trúc câu khác nhưng cùng ý nghĩa, vector mapping tốt ngữ nghĩa bất chấp mặt chữ.
- **Hybrid thắng tuyệt đối ở mixed queries**: kết hợp cả từ khóa chính xác và ý nghĩa ngữ cảnh.

**Khi nào KHÔNG dùng hybrid?**
- **Tra cứu bằng mã định danh (ID, mã lỗi cụ thể)**: Chỉ nên dùng BM25. Vector dễ đưa vào nhiễu (false positive) do các đoạn văn bản có "ngữ nghĩa" tương tự nhưng sai mã.
- **Hệ thống yêu cầu độ trễ (latency) cực thấp hoặc tiết kiệm chi phí**: Hybrid bắt buộc chạy cả dense + sparse sau đó rank lại, tốn kém tài nguyên gấp đôi.

---

## Điều ngạc nhiên nhất khi làm lab này

Điều ngạc nhiên nhất đối với mình là việc bảo mật dữ liệu (rò rỉ chéo tenant) lại mỏng manh đến vậy: chỉ cần quên truyền biến `namespaced=True` vào metadata filter của Cache, dữ liệu của khách hàng này lập tức bị lộ cho khách hàng khác mà code không hề báo bất kỳ lỗi nào.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _Không có_
