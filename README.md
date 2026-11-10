# 📚 Learning Skill Analysis

Tổng hợp các notebook thực hành **kỹ năng phân tích dữ liệu kinh doanh bằng Python**. Mỗi notebook tập trung vào một phương pháp, đi từ khái niệm, công thức đến cách đọc kết quả và ứng dụng thực tế.

## 🗂️ Danh sách kỹ năng

| Bài | Kỹ năng | Câu hỏi mà phương pháp trả lời | Notebook |
|---|---|---|---|
| B3 | **Pareto (80/20)** | Một số ít yếu tố nào tạo ra phần lớn kết quả? | [B3-Pareto Analysis](./B3-Pareto%20Analysis.ipynb) |
| B4 | **ABC Analysis** | Nên ưu tiên nguồn lực cho nhóm đối tượng nào? | [B4-ABC-Analysis](./B4-ABC-Analysis.ipynb) |
| B5 | **RFM Analysis** | Khách hàng nào giá trị, khách nào sắp rời bỏ? | [B5-RFM-Analysis](./B5-RFM-Analysis.ipynb) |
| B6 | **Cohort Analysis** | Khách hàng có quay lại theo thời gian không? | [B6-Cohort-Analysis](./B6-Cohort-Analysis.ipynb) |
| B7 | **Market Basket Analysis (MBA)** | Sản phẩm nào thường được mua cùng nhau? | [B7_MBA](./B7_MBA.ipynb) |
| B8 | **Funnel Analysis** | Khách hàng rơi rụng nhiều nhất ở bước nào? | [B8_Funnel](./B8_Funnel.ipynb) |
| B9 | **Sankey Diagram** | Dòng chảy giữa các giai đoạn/nhóm diễn ra thế nào? | [B9 Sankey](./B9%20Sankey.ipynb) |
| — | **Template Python** | Khung notebook chuẩn để bắt đầu một bài phân tích mới | [Template_Python](./Template_Python.ipynb) |

---

## 1. 📊 Pareto Analysis (Quy tắc 80/20)

**Khái niệm:** Nguyên lý do Vilfredo Pareto đề xuất: khoảng **80% kết quả đến từ 20% nguyên nhân**. Tỷ lệ 80/20 chỉ mang tính tham khảo, con số thực tế có thể là 70/30 hay 90/10.

**Cách thực hiện:**
1. Tính giá trị (doanh thu, số lượng, phí...) cho từng nhóm.
2. Sắp xếp giảm dần.
3. Tính **% đóng góp** và **% lũy kế**.
4. Vẽ biểu đồ Pareto: cột (giá trị) kết hợp đường (% lũy kế) và mốc 80%.

**Ứng dụng:** Tìm sản phẩm tạo ra phần lớn doanh thu, khách hàng đóng góp nhiều nhất, loại lỗi gây ra đa số sự cố.

**Lưu ý:** Nếu cần nhiều nhóm mới đạt 80% (dữ liệu phân bố đều), điều đó cũng là một kết luận: *không có nhóm nào thống trị*.

---

## 2. 🔤 ABC Analysis

**Khái niệm:** Phân loại đối tượng (sản phẩm, khách hàng, chi nhánh...) thành 3 hạng theo mức đóng góp giá trị:

| Hạng | Đóng góp lũy kế (tham khảo) | Ý nghĩa |
|---|---|---|
| **A** | ~70–80% giá trị đầu tiên | Quan trọng nhất, ưu tiên quản lý chặt |
| **B** | ~15–20% tiếp theo | Quan trọng vừa, theo dõi định kỳ |
| **C** | ~5–10% cuối | Đóng góp thấp, quản lý tối giản hoặc xem xét cắt giảm |

**Khác biệt với Pareto:** Pareto *chỉ ra* sự tập trung bằng biểu đồ; ABC *gán nhãn* A/B/C cho từng đối tượng để ra quyết định hành động. Ngưỡng phân hạng có thể điều chỉnh theo từng doanh nghiệp.

**Ứng dụng:** Quản lý tồn kho, phân bổ ngân sách marketing, đánh giá hiệu quả chi nhánh/kênh bán hàng.

---

## 3. 🧑‍🤝‍🧑 RFM Analysis

**Khái niệm:** Phân khúc khách hàng dựa trên hành vi mua hàng qua 3 chỉ số:

* **R – Recency:** Số ngày kể từ lần mua gần nhất (càng nhỏ càng tốt).
* **F – Frequency:** Số lần mua trong kỳ phân tích (càng lớn càng tốt).
* **M – Monetary:** Tổng giá trị chi tiêu (càng lớn càng tốt).

**Cách thực hiện:**
1. Chọn mốc thời gian phân tích (snapshot date).
2. Tính R, F, M cho từng khách hàng.
3. Chấm điểm mỗi chỉ số từ 1–5 (thường chia theo phân vị).
4. Gán nhãn phân khúc theo tổ hợp điểm.

**Một số phân khúc phổ biến:**

| Phân khúc | Đặc điểm | Hướng hành động |
|---|---|---|
| Champions | Mua gần đây, thường xuyên, chi nhiều | Chăm sóc, ưu đãi độc quyền |
| Loyal Customers | Mua đều đặn | Upsell, chương trình thành viên |
| Potential Loyalists / New Customers | Mới mua, tiềm năng | Khuyến khích mua lần 2 |
| At Risk | Từng chi nhiều nhưng lâu không quay lại | Chiến dịch win-back |
| Hibernating / Lost | Lâu không hoạt động, giá trị thấp | Chi phí thấp hoặc loại khỏi chiến dịch |

---

## 4. 🔁 Cohort Analysis

**Khái niệm:** Chia khách hàng thành các **cohort** (nhóm cùng thời điểm bắt đầu, ví dụ cùng tháng mua lần đầu) rồi theo dõi hành vi của từng nhóm qua thời gian.

**Cách thực hiện:**
1. Xác định tháng giao dịch đầu tiên của mỗi khách (cohort).
2. Tính "tuổi" của từng giao dịch: số tháng kể từ tháng đầu tiên (period index).
3. Đếm số khách hoạt động theo (cohort × period).
4. Chia cho quy mô cohort để có **Retention Rate (%)** và vẽ heatmap.

**Cách đọc:** Mỗi hàng là một cohort, mỗi cột là số tháng kể từ lần đầu. Màu đậm ở các cột đầu và nhạt dần cho thấy khách rời bỏ theo thời gian. Nếu các cohort mới có retention cao hơn cohort cũ, chiến lược giữ chân đang hiệu quả.

**Ứng dụng:** Đo khả năng giữ chân, đánh giá hiệu quả chiến dịch theo từng đợt, so sánh chất lượng khách theo kênh thu hút.

---

## 5. 🛒 Market Basket Analysis (MBA)

**Khái niệm:** Khai phá **luật kết hợp** (association rules) để tìm các sản phẩm thường xuất hiện cùng nhau trong một giỏ hàng/đơn hàng. Thuật toán phổ biến: **Apriori** (thư viện `mlxtend`).

**Ba chỉ số cốt lõi** cho luật *A → B*:

| Chỉ số | Công thức | Ý nghĩa |
|---|---|---|
| **Support** | P(A ∩ B) | Tỷ lệ giỏ hàng chứa cả A và B |
| **Confidence** | P(A ∩ B) / P(A) | Khi đã mua A, xác suất mua B |
| **Lift** | Confidence / P(B) | Mức tăng khả năng mua B khi có A so với ngẫu nhiên |

**Cách đọc Lift:** `> 1` hai sản phẩm hay đi cùng nhau, `= 1` độc lập, `< 1` ít đi cùng nhau hơn ngẫu nhiên.

**Ứng dụng:** Bán chéo (cross-sell), gợi ý sản phẩm, thiết kế bundle/combo, bố trí kệ hàng.

---

## 6. 🔻 Funnel Analysis

**Khái niệm:** Phân tích **phễu chuyển đổi**: chuỗi các bước người dùng đi qua để hoàn thành mục tiêu (ví dụ: Xem trang → Xem sản phẩm → Thêm giỏ hàng → Thanh toán → Mua hàng).

**Chỉ số chính:**
* **Conversion rate theo bước:** % người đi tiếp từ bước trước.
* **Overall conversion:** % người hoàn thành so với bước đầu.
* **Drop-off:** % người rơi rụng tại mỗi bước.

**Cách đọc:** Bước có drop-off lớn nhất là **điểm nghẽn** cần ưu tiên tối ưu. Có thể so sánh phễu giữa các nhóm (thiết bị, kênh, sản phẩm) để tìm nhóm có trải nghiệm kém.

**Ứng dụng:** Tối ưu website/app, đánh giá hiệu quả marketing, tìm ma sát trong hành trình khách hàng.

---

## 7. 🌊 Sankey Diagram

**Khái niệm:** Biểu đồ **dòng chảy** nhiều tầng, trong đó độ rộng của mỗi luồng tỷ lệ với số lượng/giá trị chuyển từ nhóm này sang nhóm khác.

**Thành phần:**
* **Node:** Các nhóm/trạng thái (ví dụ: nguồn truy cập, trang đích, sản phẩm).
* **Link:** Luồng nối giữa các node, độ dày thể hiện khối lượng.

**Ứng dụng:** Trực quan hóa hành trình khách hàng (nguồn → trang đích → sản phẩm), phân bổ ngân sách, chuyển dịch giữa các phân khúc. Dùng `plotly.graph_objects.Sankey`.

**Lưu ý:** Nên giới hạn số node/tầng để biểu đồ dễ đọc, nhóm các giá trị nhỏ thành "Khác".

---

## 🧩 Chọn phương pháp nào?

| Mục tiêu | Phương pháp phù hợp |
|---|---|
| Tìm nhóm đóng góp chính | Pareto, ABC |
| Phân khúc khách hàng theo giá trị | RFM |
| Đo mức độ giữ chân theo thời gian | Cohort |
| Tìm sản phẩm bán kèm | MBA |
| Tìm điểm nghẽn trong hành trình | Funnel |
| Trực quan dòng chảy giữa các nhóm | Sankey |

## 💻 Công nghệ sử dụng

`Python` · `pandas` · `numpy` · `matplotlib` · `seaborn` · `plotly` · `scipy` · `mlxtend` · `Google Colab / Jupyter Notebook`
