---
title: Phân tích 4 phương án phát triển Mobile App AgriSeco
authors:
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Initial creation — so sánh 4 phương án: vendor, mua source, tự build, hybrid"
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Cập nhật bảng so sánh 5 tiêu chí nhất quán, sắp xếp lại bố cục"
---

# Phân tích 4 Phương án Phát triển Mobile App AgriSeco

> **Bối cảnh:** App AgriSeco Pro hiện do FSS (FPT Software Solutions) phát triển và nắm giữ toàn bộ mã nguồn. AgriSeco phụ thuộc hoàn toàn vào vendor cho mọi thay đổi.

---

## 1. Đánh giá Hiện trạng Mobile App

### Các vấn đề hiện tại

| Mức độ | Vấn đề | Chi tiết |
|:------:|--------|----------|
| **P0** | eKYC C06, VNeID | Deadline pháp lý 31/12/2026 |
| **P1** | Thiếu sản phẩm | Không có trái phiếu Agribank trên app |
| **P1** | Nộp tiền thủ công | Chỉ mở trang hướng dẫn, không có deep link |
| **P1** | Thiếu tích hợp Agribank | Chưa embedded trong app Agribank |
| **P2** | UI đã cũ | Thiết kế chưa hiện đại so với đối thủ |
| **P2** | UX nhiều bước | Quy trình phức tạp, thiếu shortcuts |
| **P3** | Thiếu dashboard | Không có widget cá nhân hóa |

### Sản phẩm hiện có

- ✅ Chứng khoán cơ sở
- ❌ Phái sinh (chưa có)
- ❌ Trái phiếu (chưa có trên app)

---

## 2. Tổng quan 4 Phương án

| # | Phương án | Mô tả |
|:-:|-----------|-------|
| **1** | **Tiếp tục đối tác (FSS)** | Mọi thay đổi yêu cầu FSS thực hiện. AgriSeco chỉ đặt hàng và nghiệm thu. |
| **2** | **Mua mã nguồn** | Mua source code FE + BFF từ FSS + quyền sử dụng API lõi. Đội ngũ AgriSeco tự chỉnh sửa. |
| **3** | **Tự xây dựng từ đầu** | Chỉ mua quyền sử dụng API lõi (FLEX). Tự xây dựng toàn bộ FE + BFF mới. |
| **4** | **Kết hợp: Web trước → App sau** | Team tự build Mobile Web nhúng Agribank trước (4-5 tháng). App vẫn do FSS quản lý (chỉ sửa cấp bách). Sau thành công → tự build App. |

---

## 3. So sánh Tổng thể (Theo chuẩn đánh giá phương án)

Đánh giá theo các tiêu chí chuẩn ngành: Chi phí, Thời gian, Rủi ro, Lợi ích, Nguồn lực, Kiểm soát, Chất lượng

### 💰 CHI PHÍ

| Tiêu chí | PA1: Vendor | PA2: Mua Source | PA3: Tự Build | PA4: Hybrid |
|----------|-------------|-----------------|---------------|-------------|
| Chi phí ban đầu | 🟢 Thấp (0) | 🟡 TB (đàm phán) | 🔴 Cao (~9 tỷ) | 🟡 TB→Cao (~1-2 + 9 tỷ) |
| Chi phí vận hành/năm | 🔴 Cao (phí FSS + CR) | 🟡 TB (đội ngũ + API) | 🟢 Thấp (đội ngũ + API) | 🟡 TB (FSS giảm dần) |
| ROI dài hạn | ❌ Thấp | 🟡 Trung bình | ✅ Cao | ✅ Cao |

### ⏱️ THỜI GIAN

| Tiêu chí | PA1: Vendor | PA2: Mua Source | PA3: Tự Build | PA4: Hybrid |
|----------|-------------|-----------------|---------------|-------------|
| Ra sản phẩm đầu tiên | Theo yêu cầu FSS | 4-6 tháng | 6-9 tháng | **4-5 tháng** ✅ |
| Hoàn thiện toàn bộ | — | 4-6 tháng | 6-9 tháng | 10-14 tháng |

### ⚠️ RỦI RO

| Tiêu chí | PA1: Vendor | PA2: Mua Source | PA3: Tự Build | PA4: Hybrid |
|----------|-------------|-----------------|---------------|-------------|
| Rủi ro kỹ thuật | 🟢 Thấp | 🟡 TB (nợ kỹ thuật) | 🔴 Cao | 🟢 Thấp (scope nhỏ) |
| Rủi ro triển khai | 🟢 Thấp | 🟡 TB | 🔴 Cao | 🟢 Thấp → TB |
| Phụ thuộc vendor | 🔴 Cao | 🟡 TB | 🟢 Thấp | 🟢 Giảm dần |

### 📈 LỢI ÍCH

| Tiêu chí | PA1: Vendor | PA2: Mua Source | PA3: Tự Build | PA4: Hybrid |
|----------|-------------|-----------------|---------------|-------------|
| Lợi ích ngắn hạn | ✅ Ổn định (không đầu tư) | 🟡 TB (đang đầu tư) | ❌ Âm (đang đầu tư) | ✅ Có sản phẩm sớm |
| Lợi ích dài hạn | ❌ Kém | ✅ Khá | ✅ Tốt nhất | ✅ Tốt |
| Lợi thế cạnh tranh | ❌ Không có | 🟡 Một phần | ✅ Cao | ✅ Cao (Agribank) |

### 👥 NGUỒN LỰC

| Tiêu chí | PA1: Vendor | PA2: Mua Source | PA3: Tự Build | PA4: Hybrid |
|----------|-------------|-----------------|---------------|-------------|
| Nhân sự cần | 0 | 4-5 người | 8-10 người | 4-5 → 8-10 |
| Kỹ năng yêu cầu | Nghiệm thu | Mobile dev + QA | Full-stack + DevOps | Web → Mobile dần |

### 🔐 KIỂM SOÁT

| Tiêu chí | PA1: Vendor | PA2: Mua Source | PA3: Tự Build | PA4: Hybrid |
|----------|-------------|-----------------|---------------|-------------|
| Sở hữu mã nguồn | ❌ Không | 🟡 Một phần (FE) | ✅ Hoàn toàn | ✅ Dần dần |
| Độc lập công nghệ | ❌ Không | 🟡 Một phần | ✅ Hoàn toàn | ✅ Hoàn toàn (web) |
| Tích hợp Agribank | 🟡 Thuê FSS | ✅ Tự làm | ✅ Sau 6-9 tháng | ✅ **Ngay** |

### ⭐ CHẤT LƯỢNG

| Tiêu chí | PA1: Vendor | PA2: Mua Source | PA3: Tự Build | PA4: Hybrid |
|----------|-------------|-----------------|---------------|-------------|
| Khả năng mở rộng | ❌ Phụ thuộc FSS | 🟡 Giới hạn | ✅ Cao | ✅ Cao |
| Khả năng bảo trì | ❌ Không kiểm soát | 🟡 Kế thừa code cũ | ✅ Tốt (code mới) | ✅ Tốt (code mới) |
| Nợ kỹ thuật | ❌ Không trả được | 🟡 Kế thừa | ✅ Không có | ✅ Không có |

*Tham khảo: App (FE + BFF) ~9 tỷ | Mobile Web FE ~1 tỷ + CCQ ~400tr (chưa gồm BFF, case BSC)*

---

## 4. So sánh Chi tiết theo 5 Tiêu chí

Mỗi tiêu chí được so sánh với **cùng các điểm đánh giá** cho cả 4 phương án.

### 4.1 Làm được gì?

| Điểm đánh giá | PA1: Vendor | PA2: Mua Source | PA3: Tự Build | PA4: Hybrid |
|---------------|-------------|-----------------|---------------|-------------|
| **Phát triển tính năng mới trên app hiện tại** | 🟡 Qua FSS (2-6 tháng/yêu cầu) | ✅ Tự làm (2-4 tuần) | ✅ Tự làm (sau 6-9 tháng) | ✅ Web: 4-5 tháng → App sau |
| **Sản phẩm mới tích hợp Agribank** | 🟡 Thuê FSS làm | ✅ Tự làm | ✅ Sau 6-9 tháng | ✅ **Ưu tiên ngay** (4-5 tháng) |
| **Sửa lỗi / Cải tiến UX** | 🟡 Chờ FSS | ✅ Tự sửa nhanh | ✅ Sau hoàn thành | ✅ Web: tự sửa / App: FSS |
| **Kiểm soát mã nguồn** | ❌ Không sở hữu | 🟡 Một phần (FE) | ✅ Hoàn toàn | ✅ Web: toàn bộ / App: dần |
| **Chọn công nghệ** | ❌ FSS quyết định | 🟡 Kế thừa cũ | ✅ Tự chọn mới | ✅ Tự chọn mới |

### 4.2 Thay đổi được gì?

| Điểm đánh giá | PA1: Vendor | PA2: Mua Source | PA3: Tự Build | PA4: Hybrid |
|---------------|-------------|-----------------|---------------|-------------|
| **Giao diện người dùng (UI)** | 🟡 Thay đổi nhỏ qua FSS | ✅ Toàn bộ | ✅ Thiết kế mới hoàn toàn | ✅ Web: mới / App cũ: giữ |
| **Luồng trải nghiệm (UX Flow)** | ❌ Không đổi được | ✅ Tái cấu trúc | ✅ Thiết kế lại | ✅ Web: mới / App cũ: giữ |
| **Kiến trúc hệ thống** | ❌ Không | 🟡 Một phần (kế thừa nợ kỹ thuật) | ✅ Kiến trúc mới, sạch | ✅ Kiến trúc mới từ đầu |
| **Công nghệ sử dụng** | ❌ Không | 🟡 Giới hạn bởi code cũ | ✅ Công nghệ hiện đại | ✅ Công nghệ hiện đại |
| **Lõi giao dịch (Core API)** | ❌ Không | ❌ Không | ❌ Không | ❌ Không |

### 4.3 Lợi ích gì?

| Điểm đánh giá | PA1: Vendor | PA2: Mua Source | PA3: Tự Build | PA4: Hybrid |
|---------------|-------------|-----------------|---------------|-------------|
| **Tốc độ ra tính năng mới** | ❌ Chậm (2-6 tháng/yêu cầu) | ✅ Nhanh (2-4 tuần) | ✅ Nhanh (sau 6-9 tháng) | ✅ Nhanh (sau 4-5 tháng) |
| **Rủi ro triển khai** | 🟢 Thấp | 🟡 Trung bình | 🔴 Cao | 🟢 Thấp → TB (scope nhỏ) |
| **Xây dựng đội ngũ kỹ thuật** | ❌ Không | ✅ 4-5 người | ✅ 8-10 người (áp lực cao) | ✅ 4-5 → 8-10 (từ từ) |
| **Lợi thế cạnh tranh** | ❌ Không có | 🟡 Một phần | ✅ Cao | ✅ Cao (tích hợp Agribank) |
| **Kiểm soát chất lượng** | ❌ Phụ thuộc FSS | 🟡 Một phần | ✅ Hoàn toàn | ✅ Web: toàn bộ / App: hạn chế |
| **Chứng minh năng lực với BLĐ** | ❌ Không | 🟡 Qua thời gian | 🟡 Sau 6-9 tháng | ✅ **Sau 4-5 tháng** |

### 4.4 Phục vụ ai?

| Nhóm khách hàng | PA1: Vendor | PA2: Mua Source | PA3: Tự Build | PA4: Hybrid |
|-----------------|-------------|-----------------|---------------|-------------|
| **Khách hàng hiện tại** | ✅ Phục vụ (không cải thiện) | ✅ Phục vụ + cải thiện UX | ✅ Trải nghiệm mới (sau 6-9 tháng) | ✅ App cũ giữ + Web mới |
| **41.000 nhân viên Agribank** | 🟡 Nếu thuê FSS làm | ✅ Tự tích hợp | ✅ Sau 6-9 tháng | ✅ **Ưu tiên số 1** (4-5 tháng) |
| **Khách hàng Agribank** | 🟡 Nếu thuê FSS làm | ✅ Tự tích hợp | ✅ Sau 6-9 tháng | ✅ **Ưu tiên số 1** (4-5 tháng) |
| **Khách hàng mới (qua UX tốt)** | ❌ UX không đổi | ✅ Cải thiện được | ✅ Trải nghiệm tốt nhất | ✅ Web mới → App mới sau |
| **2.218 chi nhánh Agribank** | 🟡 Nếu thuê FSS | ✅ Có thể khai thác | ✅ Sau 6-9 tháng | ✅ **Khai thác ngay** |

### 4.5 Chi phí

| Hạng mục | PA1: Vendor | PA2: Mua Source | PA3: Tự Build | PA4: Hybrid |
|----------|-------------|-----------------|---------------|-------------|
| **Chi phí xây dựng / Mua** | 0 (không mua) | *Đàm phán FSS* | ~9 tỷ (FE + BFF) | GĐ1: ~1-2 tỷ / GĐ2: ~9 tỷ |
| **Chi phí nhân sự (đội ngũ)** | 0 | 4-5 người | 8-10 người | 4-5 → 8-10 người |
| **Chi phí bảo trì hàng năm** | Phí FSS (hiện tại) | Phí API lõi + đội ngũ | Phí API lõi + đội ngũ | Phí FSS (giảm dần) + API lõi |
| **Chi phí yêu cầu thay đổi** | Tính theo yêu cầu (FSS) | Chỉ công đội ngũ | Chỉ công đội ngũ | Chỉ công đội ngũ |
| **Thời gian hoàn thành** | — | 4-6 tháng | 6-9 tháng | GĐ1: 4-5 tháng / Tổng: 10-14 tháng |
| **Thời gian ra giá trị đầu tiên** | — | 4-6 tháng | 6-9 tháng | **4-5 tháng** ✅ |

*Tham khảo BSC: Mobile Web cơ bản ~1 tỷ + phân phối CCQ ~400tr (chưa gồm BFF). App đầy đủ (FE + BFF) ~9 tỷ.*

---

## 5. Góc nhìn theo Vai trò

### 5.1 Góc nhìn Lãnh đạo (CEO)

| Tiêu chí | PA1: Vendor | PA2: Mua source | PA3: Tự xây | PA4: Kết hợp |
|----------|-------------|-----------------|-------------|--------------|
| **Lợi nhuận ngắn hạn** | ✅ Tốt (không đầu tư) | ⚠️ Trung bình | ❌ Âm (đang đầu tư) | ✅ Khá (ra sản phẩm sớm) |
| **Lợi nhuận dài hạn** | ❌ Kém | ✅ Khá | ✅ Tốt nhất | ✅ Tốt |
| **Lợi thế cạnh tranh** | ❌ Không có | 🟡 Một phần | ✅ Cao | ✅ Cao (tích hợp Agribank) |
| **Phụ thuộc đối tác** | 🔴 Cao | 🟡 Trung bình | 🟢 Thấp | 🟢 Giảm dần |
| **Rủi ro** | 🟢 Thấp | 🟡 Trung bình | 🔴 Cao | 🟢 Thấp → TB |

*Ghi chú: PA4 cho phép chứng minh năng lực với Ban lãnh đạo qua sản phẩm nhỏ (4-5 tháng) trước khi đầu tư lớn.*

### 5.2 Góc nhìn Kỹ thuật

| Tiêu chí | PA1: Vendor | PA2: Mua source | PA3: Tự xây | PA4: Kết hợp |
|----------|-------------|-----------------|-------------|--------------|
| **Kiểm soát mã nguồn** | ❌ Không | 🟡 Một phần | ✅ Hoàn toàn | ✅ Dần dần (web → app) |
| **Công nghệ sử dụng** | ❌ Đối tác chọn | 🟡 Kế thừa cũ | ✅ Tự chọn mới | ✅ Tự chọn từ đầu |
| **Nợ kỹ thuật** | ❌ Không trả được | 🟡 Kế thừa | ✅ Không có | ✅ Không có |
| **Xây dựng đội ngũ** | ❌ Không | ✅ Có | ✅ Có (áp lực cao) | ✅ Có (từ từ) |
| **Học nghiệp vụ** | ❌ Không | 🟡 Qua code cũ | 🟡 Vừa làm vừa học | ✅ Học qua dự án nhỏ trước |

*Ghi chú: PA4 giúp đội ngũ học nghiệp vụ chứng khoán qua dự án nhỏ (web) trước khi làm dự án lớn (app).*

### 5.3 Góc nhìn Kinh doanh

| Tiêu chí | PA1: Vendor | PA2: Mua source | PA3: Tự xây | PA4: Kết hợp |
|----------|-------------|-----------------|-------------|--------------|
| **Thời gian ra tính năng mới** | ❌ 2-6 tháng/tính năng | ✅ 2-4 tuần | ✅ 2-4 tuần (sau 6-9 tháng) | ✅ 2-4 tuần (sau 4-5 tháng) |
| **Tích hợp Agribank (sản phẩm mới)** | 🟡 Thuê FSS làm | ✅ Tự làm | ✅ Sau 6-9 tháng | ✅ **Ngay từ đầu** |
| **Tiếp cận 41K nhân viên Agribank** | 🟡 Phụ thuộc FSS | ✅ Chủ động | ✅ Sau 6-9 tháng | ✅ **Sau 4-5 tháng** |
| **Cá nhân hóa trải nghiệm** | ❌ Không | ✅ Có | ✅ Có | ✅ Có |
| **Thử nghiệm A/B** | ❌ Không | ✅ Có | ✅ Có | ✅ Có |

*Ghi chú: Tích hợp Agribank là **sản phẩm mới**, cần viết từ đầu. PA1 thuê FSS làm, PA2/3/4 tự làm. PA4 ưu tiên làm ngay để tiếp cận 41.000 nhân viên Agribank.*

---

## 6. PA4: Hybrid - Mobile Web trước → App sau (Chi tiết)

> **Tương tự case BSC:** Team tự làm Mobile Web nhúng Agribank trước, sau đó quay lại build App.

### Lộ trình 2 giai đoạn

```
GIAI ĐOẠN 1: Mobile Web nhúng Agribank (4-5 tháng)
│
├── Team AgriSeco tự build Mobile Web
├── Tích hợp nhúng vào App Agribank  
├── App AgriSeco Pro vẫn do FSS quản lý (chỉ sửa cấp bách nhất)
├── Chi phí: ~1-1,5 tỷ (tham khảo case BSC)
└── Mục tiêu: Tiếp cận 41.000 NV + KH Agribank

═══════════════════════════════════════════════════

GIAI ĐOẠN 2: Tự build lại Mobile App (6-9 tháng sau)
│
├── Sau khi Mobile Web thành công
├── Team đã có kinh nghiệm + hiểu nghiệp vụ
├── Tự build App mới hoàn toàn
├── Chi phí: ~9 tỷ
└── Dần thay thế app FSS
```

### So sánh PA3 vs PA4

| Tiêu chí | PA3: Tự build App ngay | PA4: Mobile Web trước |
|----------|------------------------|----------------------|
| **Thời gian ra sản phẩm đầu** | 6-9 tháng | **4-5 tháng** ✅ |
| **Rủi ro** | Cao (scope lớn) | **Thấp hơn** ✅ |
| **Tích hợp Agribank** | Sau 6-9 tháng | **Ngay từ đầu** ✅ |
| **Xây dựng team** | Áp lực cao ngay | **Từ từ** ✅ |
| **Chứng minh ROI** | Chờ 6-9 tháng | **4-5 tháng** ✅ |
| **Tổng thời gian hoàn thiện** | 6-9 tháng | 10-14 tháng |
| **Chi phí** | ~9 tỷ | ~1-2 tỷ (web) + ~9 tỷ (app sau) |

### Ưu điểm PA4

1. **Giảm rủi ro:** Scope nhỏ hơn, dễ kiểm soát
2. **Nhanh ra giá trị:** 4-5 tháng có sản phẩm tích hợp Agribank
3. **Xây team dần:** Học nghiệp vụ qua thực chiến, không áp lực cao ngay
4. **App cũ vẫn chạy:** Không gián đoạn dịch vụ
5. **Chứng minh năng lực:** Trước khi đầu tư lớn cho app
6. **Tận dụng Agribank:** 2.218 chi nhánh, 41.000 nhân viên

### Lưu ý PA4

- Vẫn trả phí FSS cho app cũ (song song)
- Cần phối hợp với Agribank (nhúng SDK)
- Team cần 4-5 người ngay từ đầu
- Tổng thời gian dài hơn PA3 thuần
- Chi phí tổng có thể cao hơn một chút

### Khi nào chọn PA4?

```
PA4 (HYBRID) PHÙ HỢP KHI:
│
├── ✅ Ban lãnh đạo ưu tiên tích hợp Agribank là CẤP BÁCH
├── ✅ Muốn giảm rủi ro bằng cách làm scope nhỏ trước
├── ✅ Cần chứng minh năng lực trước khi đầu tư lớn
├── ✅ Chưa có team mạnh sẵn, cần xây dựng từ từ
└── ✅ Chấp nhận timeline tổng dài hơn để đổi lấy an toàn
```

---

## 7. Phân tích thêm: PA2 - Mua mã nguồn có đáng không?

Với hiện trạng app nhiều vấn đề như trên, việc mua source code để sửa cần cân nhắc kỹ:

### Đáng mua NẾU

| Điều kiện | Lý do |
|-----------|-------|
| Code base còn tốt, clean | Dễ maintain, dễ onboard team mới |
| Architecture tách biệt rõ (FE/BFF/Core) | Có thể sửa từng phần độc lập |
| Vấn đề chủ yếu ở UI/UX | Chỉ cần redesign FE, không động core |
| Có thể sửa incremental | Không cần rewrite toàn bộ |
| Tiết kiệm 6-9 tháng so với build mới | Time-to-market nhanh hơn |

### KHÔNG đáng NẾU

| Điều kiện | Lý do |
|-----------|-------|
| Code legacy, coupling cao | Sửa 1 chỗ vỡ chỗ khác |
| Nợ kỹ thuật lớn | Chi phí maintain cao |
| Không có tài liệu, không có test | Team mất nhiều tháng để hiểu |
| Framework/library cũ | Không cập nhật được, security risk |
| Chi phí sửa ≈ chi phí build mới | Không có lợi về thời gian/tiền |

### PA2 còn tối ưu không khi phải fix TẤT CẢ vấn đề?

Source hiện tại đã cũ. Nếu cần fix toàn bộ vấn đề (P0→P3), khối lượng công việc rất lớn:

| Hạng mục cần fix | Effort ước tính | Ảnh hưởng đến code |
|------------------|-----------------|-------------------|
| eKYC C06, VNeID | 1-2 tháng | Flow đăng ký, xác thực |
| Trái phiếu Agribank | 1-2 tháng | Thêm module mới |
| Deep link ngân hàng | 2-4 tuần | Module nộp tiền |
| Tích hợp sâu Agribank | 2-3 tháng | SDK, auth, session |
| UI/UX Refresh | 2-3 tháng | Gần như toàn bộ UI |
| **TỔNG** | **6-10 tháng** | **~70-80% code** |

### Kết luận quan trọng

```
NẾU PHẢI SỬA ~70-80% CODE:
│
├── PA2 (Mua source) KHÔNG CÒN TỐI ƯU
│   ├── Vẫn kế thừa nợ kỹ thuật của phần còn lại
│   ├── Framework/library có thể đã cũ
│   ├── Thời gian: 6-10 tháng
│   └── Chi phí: mua + sửa có thể tương đương build mới
│
└── PA3/PA4 CÓ THỂ HIỆU QUẢ HƠN
    ├── Không kế thừa nợ kỹ thuật
    ├── Tech stack mới, clean architecture
    ├── Thời gian: tương đương
    └── Chi phí: tương đương
```

**→ Khuyến nghị:** Cần **code audit** trước khi quyết định mua. Nếu code quá tệ, PA3/PA4 có thể hiệu quả hơn.

---

## 8. Khuyến nghị

### Khi nào chọn phương án nào?

| PA2 phù hợp NẾU | PA3 phù hợp NẾU | PA4 phù hợp NẾU |
|-----------------|-----------------|-----------------|
| Code audit cho kết quả tốt | Cần fix >60% code | **Agribank là ưu tiên cấp bách** |
| Chỉ cần fix <50% code | Có budget + team mạnh | Muốn giảm rủi ro |
| Không có team đủ mạnh | Muốn kiểm soát hoàn toàn | Chứng minh năng lực trước |
| Muốn ship nhanh | Đội ngũ sẵn sàng | Xây team dần dần |

### Đề xuất

**PA4 (Hybrid) có thể là lựa chọn tối ưu** nếu tích hợp Agribank là chiến lược ưu tiên.

PA4 cho phép:
- Ra sản phẩm nhanh (4-5 tháng)
- Giảm rủi ro (scope nhỏ)
- Xây team từ từ (gradual)
- Sau đó tự tin build lại app hoàn chỉnh

### Bước tiếp theo

1. **Xác định:** Tích hợp Agribank có phải ưu tiên cấp bách?
2. **Nếu có** → PA4 (Mobile Web trước)
3. **Nếu không** → Code audit để chọn PA2 vs PA3
4. **Đàm phán** quyền sử dụng API FLEX với FSS

### Ma trận Quyết định

```
                        NGUỒN LỰC TÀI CHÍNH
                    Thấp (<5 tỷ/năm)    Cao (>8 tỷ/năm)
                    ─────────────────────────────────────
THAM VỌNG     Thấp │   PA1: Vendor    │   PA2: Mua Source
CÔNG NGHỆ         │                   │
                  │─────────────────────────────────────
              Cao │   PA2: Mua Source │   PA3/PA4: Tự Build
                  │   (giảm scope)    │
                    ─────────────────────────────────────
```

---

*Cập nhật: 28/10/2026*
