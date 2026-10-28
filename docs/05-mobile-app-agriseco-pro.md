---
title: Mobile App AgriSeco Pro - Hiện trạng & Khuyến nghị
authors:
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Initial creation — tổng hợp từ khảo sát app thực tế"
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Bổ sung quy trình đổi mật khẩu và các loại OTP (Matrix, SMS, Soft)"
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Phân tích chuyên sâu: VNeID/CCCD (chỉ cho eKYC), Device Binding, lộ trình sunset Matrix"
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Giải pháp đề xuất: Email OTP, Biometric thay thế Matrix - cần xem xét"
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Bổ sung: So sánh nộp tiền với TCBS, đề xuất deep link Agribank, đề xuất trái phiếu Agribank"
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Bổ sung: Đề xuất redesign UI/UX, tích hợp danh sách môi giới trong app"
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Bổ sung: Đề xuất thông tin thị trường, khuyến nghị có điểm mua/bán, khảo sát khẩu vị rủi ro"
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Tổng hợp đánh giá hiện trạng và 20 đề xuất theo độ ưu tiên P0-P3, roadmap"
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Bổ sung: Mobile Web nhúng app Agribank, chi tiết Đề án 06/C06 và deadline tuân thủ"
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Phân biệt 2 yêu cầu VNeID: liên kết TK hiện có (NĐ 320/2026) vs eKYC mở TK mới (Đề án 06)"
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Sắp xếp lại roadmap: Wave 1 (Pháp luật) → Wave 2 (Doanh thu) → Wave 3 (Trải nghiệm)"
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Tái cấu trúc bố cục: sắp xếp lại các section theo flow logic"
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Sửa priority: eContract/eSign và Sunset Matrix xuống P1 (chưa bắt buộc pháp lý). Thêm section 4.7 kiến trúc Auth Service (không phụ thuộc FSS), section 4.8 câu hỏi cần làm rõ với FSS"
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Làm rõ cơ sở pháp lý eContract (bảng trạng thái). Bổ sung section 4.8 phân tích chi tiết thay Matrix bằng Biometric: điều kiện tiên quyết, flow đề xuất, tóm tắt thay đổi"
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Cập nhật section 6.1: mapping đầy đủ 13 vấn đề hiện trạng ↔ giải pháp đề xuất theo priority"
---

# AgriSeco Pro - Mobile App

> Phân tích hiện trạng và khuyến nghị cải tiến

---

## 1. Hiện trạng (As-Is)

### 1.1 Cấu trúc App

```
AGRISECO PRO - 5 MENU CHÍNH
│
├── 1. TRANG CHỦ
│   ├── Header
│   │   ├── Chưa đăng nhập: [Đăng nhập] [Đăng ký]
│   │   └── Đã đăng nhập: [Số TK] [Tiểu khoản ▼]
│   │       └── Quick view: Sức mua | Tài sản dòng | Tiền được rút
│   ├── Banner quảng cáo (4 ảnh xoay)
│   ├── Tiện ích ưu tiên (thanh trượt, 4 shortcuts/lần)
│   │   └── Chọn từ 19 tính năng: Đặt lệnh, Sổ lệnh, Nộp tiền,
│   │       Ứng trước, Chuyển tiền, Danh mục, Tài sản, Dư nợ,
│   │       Khuyến nghị, Bảng giá, Cảnh báo, Tin tức, Soft OTP,
│   │       Hỗ trợ, Lịch sử đặt lệnh, Lịch sử khớp lệnh,
│   │       Danh mục ký quỹ, Ngôn ngữ, Giao diện
│   ├── Thị trường (2-5 thẻ chỉ số)
│   └── Tin tức khuyến nghị
│
├── 2. BẢNG GIÁ
│   ├── Lọc theo chỉ số / Yêu thích
│   ├── Danh mục khuyến nghị
│   │   ├── Báo cáo mới nhất
│   │   └── Tín hiệu giao dịch tuần
│   ├── Chi tiết chỉ số
│   │   ├── Biểu đồ
│   │   ├── Thông tin khối lượng
│   │   ├── Danh sách CK thành phần
│   │   ├── Lịch sử biến động
│   │   ├── Tin tức liên quan
│   │   └── Đồ thị full
│   └── Chi tiết mã cổ phiếu
│       ├── Tổng quan + Biểu đồ đơn giản
│       ├── Chi tiết: Giá | Sức mua | Lịch sử khớp lệnh
│       ├── Lịch sử biến động giá (theo ngày)
│       ├── Tin tức của mã
│       ├── Đồ thị full
│       ├── Thêm vào Yêu thích
│       └── Cảnh báo giá (biến động / khối lượng / giá trị)
│
├── 3. ĐẶT LỆNH
│   ├── Đặt lệnh
│   │   ├── Tabs: Mua | Bán | Hủy | Sửa
│   │   └── Danh sách lệnh đã đặt
│   ├── Sổ lệnh
│   │   └── Full list + Tổng mua, Tổng bán, Giá trị dòng
│   ├── Danh mục
│   │   └── CK trong tài khoản
│   └── Tài sản
│       └── Tài sản dòng, Tiền bán về, Tiền ứng,
│           Giá trị CK, Dư nợ, Sức mua, Trạng thái tiểu khoản
│
├── 4. TÌM KIẾM
│   ├── Tìm chứng khoán
│   ├── Tìm tin tức
│   └── Tìm chức năng
│
└── 5. MỞ RỘNG
    ├── Tài khoản: Switch/thêm TK khác
    ├── Giao dịch CK
    │   ├── Đặt lệnh
    │   ├── Chuyển chứng khoán
    │   └── Đăng ký quyền mua
    ├── Giao dịch tiền
    │   ├── Nộp tiền
    │   ├── Chuyển tiền
    │   └── Ứng trước tiền bán
    ├── Tài khoản
    │   ├── Thông tin cá nhân
    │   ├── Dư nợ ký quỹ
    │   ├── Chọn môi giới chăm sóc
    │   └── Quản lý đăng nhập
    ├── Tiện ích
    │   ├── Xác nhận số dư
    │   ├── Tra cứu danh mục ký quỹ
    │   └── Cảnh báo giá
    ├── Báo cáo
    │   ├── Sao kê tiền / CK
    │   ├── Lịch sử: Đặt lệnh | Điều kiện | Khớp lệnh
    │   ├── Lãi lỗ đã thực hiện
    │   ├── Lịch sử nộp rút tiền
    │   └── Tra cứu sự kiện quyền
    ├── Cài đặt
    │   ├── Đổi mật khẩu / PIN
    │   ├── Ngân hàng thụ hưởng
    │   ├── Đăng ký dịch vụ
    │   ├── Giao diện / Ngôn ngữ / Cỡ chữ
    │   ├── Vân tay / Khuôn mặt
    │   └── Soft OTP
    ├── Hỗ trợ
    │   ├── Tổng đài | Email | Messenger | Zalo
    │   ├── Danh sách môi giới chăm sóc
    │   └── Mạng lưới
    └── Thông tin phần mềm + Đăng xuất
```

### 1.2 Sản phẩm giao dịch được

| Sản phẩm | Trạng thái |
|----------|------------|
| CK cơ sở (Mua/Bán/Hủy/Sửa) | ✅ Có |
| Margin / Ứng trước tiền bán | ✅ Có |
| Chuyển chứng khoán | ✅ Có |
| Đăng ký quyền mua | ✅ Có |
| Nộp/Chuyển tiền | ✅ Có |
| Trái phiếu Agribank | ❌ Không có trong app |
| Chứng chỉ quỹ | ❌ Không có |
| Phái sinh | ❌ Không có |

### 1.3 Bảo mật hiện tại

```
TẦNG BẢO MẬT
│
├── 1. Mật khẩu đăng nhập
│   └── Xác thực danh tính
│
├── 2. Biometric (Vân tay / Khuôn mặt)
│   └── Thay thế mật khẩu đăng nhập
│
├── 3. PIN (Mật khẩu đặt lệnh)
│   └── Xác nhận giao dịch: Mua/Bán/Hủy/Sửa
│
├── 4. Thẻ ma trận (OTP cứng) ← CÒN DÙNG
│   └── 2FA cho: Rút tiền, Chuyển tiền, Đổi MK, GD lớn
│
└── 5. Soft OTP ← MỚI
    └── Thay thế thẻ ma trận (cùng vai trò)
```

**Ghi chú:** Hệ thống đang duy trì song song thẻ ma trận và Soft OTP.

### 1.4 eKYC hiện tại

| Bước | Trạng thái |
|------|------------|
| Chụp CCCD 2 mặt | ✅ Có |
| Chụp khuôn mặt | ✅ Có |
| Quét mã QR trên CCCD | ❌ Chưa có |
| Đọc chip NFC | ❌ Chưa có |
| Tích hợp VNID (C06) | ❌ Chưa có |

### 1.5 Quy trình mở tài khoản

```
HIỆN TẠI
│
├── 1. eKYC online (CCCD + Face)
├── 2. Nhận email hợp đồng
├── 3. In → Ký → Gửi lại (hoặc ra quầy ký)
├── 4. Chờ 30 ngày nhận hồ sơ
└── 5. Kích hoạt giao dịch

⚠️ VẪN CÒN KÝ BẢN CỨNG
```

### 1.6 Quy trình đổi mật khẩu đăng nhập

```
ĐỔI MẬT KHẨU
│
├── Bước 1: Nhập mật khẩu hiện tại
├── Bước 2: Nhập mật khẩu mới
├── Bước 3: Nhập lại mật khẩu mới
├── → Thành công
│
└── Bước 4: Đăng nhập lần đầu với MK mới
    │
    ├── Hệ thống hiển thị popup "Xác thực lần đầu"
    ├── Lựa chọn loại xác thực:
    │   ├── Matrix (Thẻ ma trận)
    │   └── SMS OTP
    └── Nhập mã OTP → Đăng nhập thành công
```

**Nhận xét:** Bắt buộc xác thực OTP sau đổi mật khẩu là **best practice** bảo mật - đảm bảo người đổi mật khẩu có quyền truy cập OTP.

### 1.7 Các loại OTP hỗ trợ

| Loại OTP | Trạng thái | Ghi chú |
|----------|------------|---------|
| **Thẻ ma trận** | ✅ Còn dùng | Legacy, nên sunset |
| **SMS OTP** | ✅ Có | Gửi qua số điện thoại đăng ký |
| **Soft OTP** | ✅ Có | Trong app, khuyến nghị dùng |

```
CÁC LOẠI OTP
│
├── 1. THẺ MA TRẬN (Matrix)
│   └── Tra cứu ô trên thẻ cứng
│
├── 2. SMS OTP
│   └── Gửi mã qua SMS đến SĐT đăng ký
│
└── 3. SOFT OTP
    └── Sinh mã tự động trong app (30-60 giây/mã)
```

### 1.8 Tại sao xác thực lần đầu không dùng Soft OTP?

**Phân tích:** Sau đổi mật khẩu, hệ thống chỉ cho phép Matrix hoặc SMS OTP - không cho Soft OTP.

```
LÝ DO: OUT-OF-BAND VERIFICATION
│
├── Soft OTP (TRONG app)
│   └── Nếu kẻ xấu chiếm TK và đổi MK
│       └── Kẻ xấu ĐANG Ở TRONG APP → mở Soft OTP được → KHÔNG AN TOÀN
│
└── Matrix / SMS OTP (NGOÀI app)
    └── Cần thẻ vật lý hoặc SIM điện thoại
        └── Kẻ xấu không có → AN TOÀN HƠN
```

| Loại OTP | Trong/Ngoài App | An toàn sau đổi MK |
|----------|-----------------|-------------------|
| Soft OTP | Trong app | ❌ Rủi ro |
| SMS OTP | Ngoài app (SIM) | ✅ An toàn |
| Matrix | Ngoài app (thẻ vật lý) | ✅ An toàn |

**Kết luận:** Đây là **best practice bảo mật** - xác thực sau thay đổi nhạy cảm phải dùng kênh ngoài app.

**Ghi chú:**
- Matrix được cấp ngay khi đăng ký tài khoản
- SMS phụ thuộc nhà mạng

### 1.9 Phương thức nộp tiền hiện tại

```
NỘP TIỀN - AGRISECO HIỆN TẠI (3 cách - cũ)
│
├── Cách 1: Chuyển khoản liên ngân hàng
│   └── Hướng dẫn dùng Internet Banking của Agribank/BIDV/VCB
│   └── → Tự mở app ngân hàng, tự nhập thông tin
│
├── Cách 2: Tài khoản định danh + QR
│   └── Tạo QR với mã TK chứng khoán
│   └── → Mở app ngân hàng → Quét QR
│
└── Cách 3: Chuyển thông thường
    └── Show QR tài khoản công ty
    └── → Tự chuyển + ghi cú pháp nội dung
```

**So sánh TCBS (5 cách - hiện đại):**

```
NỘP TIỀN - TCBS
│
├── Cách 1: Techcombank Mobile (Deep integration)
│   └── Trong app TCB → Chọn TCBS → Nhập số TKCK → Chọn tiểu khoản → Xong
│   └── KHÔNG cần thoát app, KHÔNG cần nhớ số TK ngân hàng
│
├── Cách 2: QR Code (Từ app TCInvest)
│   └── App CK tạo QR sẵn thông tin → Quét bằng bất kỳ app NH nào → Nhập số tiền → Xong
│
├── Cách 3: One-touch transfer ⭐ TIỆN NHẤT
│   └── Trong app CK → Chọn "Nộp tiền" → Chọn ngân hàng
│   └── → TỰ ĐỘNG mở app ngân hàng với thông tin ĐÃ ĐIỀN SẴN
│   └── → User chỉ nhập số tiền + Xác nhận
│
├── Cách 4: Chuyển thủ công (cú pháp)
│   └── Giống AgriSeco
│
└── Cách 5: Đối tác (BIDV, VPBank, TPBank, Viettel Money...)
    └── Tích hợp sâu với nhiều ngân hàng
```

**Nhận xét:** AgriSeco yêu cầu user tự thao tác nhiều bước, chưa có deep link tự động mở app ngân hàng với thông tin điền sẵn như TCBS.

### 1.10 Câu hỏi cần kiểm tra

| # | Câu hỏi | Trạng thái |
|---|---------|------------|
| Q1 | Bỏ qua xác thực lần đầu sau đổi MK → Chuyện gì xảy ra? Vẫn đăng nhập được? Lần sau có hỏi lại? Bị giới hạn tính năng? | ⏳ Chờ kiểm tra |
| Q2 | Sau khi xác thực lần đầu thành công, các lần đăng nhập sau có dùng Soft OTP được không? | ⏳ Chờ kiểm tra |

---

## 2. Gaps (Thiếu)

### 2.1 Sản phẩm

| Gap | Mức độ | Ghi chú |
|-----|--------|---------|
| Trái phiếu Agribank | 🔴 Critical | Sản phẩm của công ty mẹ |
| Chứng chỉ quỹ | 🟡 Medium | Mở rộng đầu tư |
| Phái sinh | 🟡 Medium | Cạnh tranh VPS, SSI, HSC |

### 2.2 Tính năng

| Gap | Mức độ | Ghi chú |
|-----|--------|---------|
| Thống kê thị trường nổi bật | 🟠 High | Top tăng/giảm, Khối ngoại, Thanh khoản |
| Phân tích mã (TA/FA) | 🟠 High | SSI, TCBS có |
| Tích hợp sâu Agribank | 🔴 Critical | Hiện chỉ redirect |

### 2.3 Bảo mật & Compliance

| Gap | Mức độ | Ghi chú |
|-----|--------|---------|
| eKYC chưa đáp ứng C06 | 🔴 Compliance | Thiếu QR, Chip, VNID |
| Còn dùng thẻ ma trận | 🟡 Tech Debt | Nên migrate sang Soft OTP |
| Còn ký hợp đồng giấy | 🟠 High | Đối thủ đã bỏ |

---

## 3. So sánh đối thủ

| Tính năng | AgriSeco | TCBS | SSI | VPS |
|-----------|:--------:|:----:|:---:|:---:|
| CK cơ sở | ✅ | ✅ | ✅ | ✅ |
| Phái sinh | ❌ | ✅ | ✅ | ✅ |
| Trái phiếu | ❌ | ✅ | ✅ | ✅ |
| CCQ | ❌ | ✅ | ✅ | ✅ |
| Thống kê thị trường | ❌ | ✅ | ✅ | ✅ |
| Phân tích mã | ❌ | ✅ | ✅ | ✅ |
| eKYC C06 | ❌ | ✅ | ✅ | ✅ |
| eContract | ❌ | ✅ | ✅ | ✅ |
| Thẻ ma trận | ✅ còn | ❌ bỏ | ❌ bỏ | ❌ bỏ |

---

## 4. Phân tích chuyên sâu

### 4.1 Đề án 06 / C06 - Yêu cầu bắt buộc từ Bộ Công an

**C06** = Cục Cảnh sát Quản lý hành chính về trật tự xã hội (Bộ Công an)

**Đề án 06** = "Đề án Phát triển ứng dụng dữ liệu về dân cư, định danh và xác thực điện tử phục vụ chuyển đổi số quốc gia giai đoạn 2022-2025, tầm nhìn đến năm 2030"

**Cơ sở pháp lý:**
- Nghị định 59/2022/NĐ-CP (05/09/2022)
- Nghị định 69/2024/NĐ-CP (25/06/2024)
- Luật Căn cước 26/2023/QH15 (hiệu lực 01/07/2024)

**3 nhóm nhiệm vụ UBCKNN phối hợp C06:**

| # | Nhiệm vụ | Mô tả |
|---|----------|-------|
| 1 | **Làm sạch dữ liệu** | Đối soát, xác thực thông tin nhà đầu tư với CSDL quốc gia về dân cư |
| 2 | **Kết nối hệ thống** | Kết nối với hệ thống định danh và xác thực điện tử (VNeID) |
| 3 | **Ứng dụng CCCD chip** | Định danh nhà đầu tư bằng thẻ căn cước gắn chip NFC |

**Deadline và hậu quả không tuân thủ:**

| Mốc thời gian | Yêu cầu | Hậu quả không tuân thủ |
|---------------|---------|------------------------|
| 01/07/2024 | Luật Căn cước có hiệu lực | CMND/CCCD không chip hết giá trị |
| **01/10/2024** | Chỉ cung cấp GD online cho TK đã cập nhật CCCD chip | **NGỪNG giao dịch CK online** |
| 01/01/2025 | Tăng cường yêu cầu | Hạn chế thêm |
| **31/12/2026** | 11 nhóm TK điện tử phải liên kết VNeID | TK chứng khoán bắt buộc VNeID |

**AgriSeco hiện tại:**

| Yêu cầu Đề án 06 | Trạng thái | Ghi chú |
|------------------|:----------:|---------|
| Chụp CCCD 2 mặt | ✅ | Đã có |
| Chụp khuôn mặt | ✅ | Đã có |
| Quét mã QR trên CCCD | ❌ | **Cần bổ sung** |
| Đọc chip NFC | ❌ | **Cần bổ sung** |
| Tích hợp VNeID | ❌ | **Cần bổ sung** |
| Đối soát CSDL quốc gia | ❌ | **Cần bổ sung** |

**Rủi ro nếu không tuân thủ:**
1. **Pháp lý**: Vi phạm quy định UBCKNN và Nghị định
2. **Kinh doanh**: Nhà đầu tư không giao dịch online được → Mất khách
3. **Cạnh tranh**: Đối thủ (TCBS, SSI, VPS) đã tuân thủ → AgriSeco tụt lại
4. **Uy tín**: Hình ảnh công nghệ lạc hậu

### 4.2 Hai yêu cầu khác nhau về VNeID

**Lưu ý:** Có 2 yêu cầu riêng biệt liên quan đến VNeID:

#### A. Liên kết tài khoản CK hiện có với VNeID

| Văn bản | Yêu cầu | Deadline |
|---------|---------|----------|
| Nghị định 69/2024/NĐ-CP (25/06/2024) | Quy định về định danh và xác thực điện tử | - |
| **Nghị định 320/2026/NĐ-CP** (13/08/2026) | Sửa đổi NĐ 69, bắt buộc liên kết VNeID | **31/12/2026** |

**11 loại tài khoản phải liên kết VNeID trước 31/12/2026:**
1. Tài khoản chứng khoán
2. Tài khoản viễn thông
3. Tài khoản thương mại điện tử (người bán, livestream, tiếp thị liên kết)
4. Tài khoản hóa đơn điện tử
5. Tài khoản du lịch
6. Tài khoản lĩnh vực dược
7. Tài khoản khám bệnh, chữa bệnh
8. Tài khoản mạng xã hội tại Việt Nam
9-11. Các lĩnh vực khác theo quy định bộ ngành

#### B. eKYC khi MỞ tài khoản mới (Đề án 06)

| Văn bản | Yêu cầu | Deadline |
|---------|---------|----------|
| Kế hoạch phối hợp UBCKNN - C06 (11/2023) | Làm sạch dữ liệu, kết nối CSDL quốc gia, ứng dụng CCCD chip | Đang triển khai |
| Luật Căn cước 26/2023/QH15 | CCCD gắn chip bắt buộc | 01/07/2024 |
| Yêu cầu UBCKNN | Giao dịch online phải có CCCD chip | 01/10/2024 |

**Lưu ý quan trọng:** 
- Chưa có thông tư **bắt buộc cụ thể** tích hợp VNeID cho luồng mở tài khoản CK mới
- Các công ty đang triển khai theo hướng dẫn của Đề án 06 
- Đối thủ (VNDIRECT, SSI, VPS) đã tích hợp để cạnh tranh và chuẩn bị cho tương lai

### 4.3 Xác thực VNeID / CCCD chip - Đối thủ đang dùng ở đâu?

**Lưu ý quan trọng:** VNeID/CCCD chip **KHÔNG** được dùng cho xác thực sau đổi mật khẩu.

```
VNEID / CCCD CHIP - PHẠM VI SỬ DỤNG
│
├── ✅ ĐANG DÙNG (đối thủ: VNDIRECT, DNSE, VPS, SSI...)
│   │
│   ├── eKYC mở tài khoản mới
│   │   └── Xác minh danh tính với CSDL Quốc gia
│   │
│   ├── Xác thực định danh (KYC nâng cao)
│   │   └── Liên kết TK với VNeID một lần
│   │
│   └── Cập nhật thông tin cá nhân quan trọng
│       └── Verify trước khi thay đổi
│
└── ❌ KHÔNG DÙNG CHO
    │
    ├── Xác thực sau đổi mật khẩu
    │   └── Vẫn dùng Matrix / SMS OTP
    │
    └── Xác thực giao dịch hàng ngày
        └── Vẫn dùng PIN / OTP
```

**Ví dụ VNDIRECT:**
- Chức năng: "Liên kết, xác thực tài khoản giao dịch chứng khoán với VNeID"
- Mục đích: Xác nhận thông tin KH khớp với Trung tâm dữ liệu Quốc gia
- Thời điểm: Một lần, sau khi mở TK hoặc khi cần nâng cấp
- Phương thức: VNeID app (Mức độ 2) hoặc quét NFC chip CCCD

### 4.4 Vấn đề khi sunset Matrix - Chỉ còn SMS OTP

Nếu loại bỏ Matrix, xác thực sau đổi MK chỉ còn SMS OTP:

```
SAU ĐỔI MK - XÁC THỰC LẦN ĐẦU
│
├── Hiện tại: Matrix HOẶC SMS OTP (2 lựa chọn)
│
└── Sau sunset Matrix: CHỈ CÒN SMS OTP
    │
    └── Rủi ro single point of failure:
        ├── SMS không nhận được (lỗi mạng, nhà mạng)
        ├── User đổi SĐT chưa cập nhật
        └── SIM bị khóa/mất
```

**Ghi chú:**
- Matrix được cấp ngay khi đăng ký tài khoản
- SMS phụ thuộc nhà mạng

### 4.5 Device Binding - Giải pháp cho Soft OTP (Khuyến nghị tương lai)

Nếu muốn cho phép Soft OTP cho xác thực sau đổi MK, cần triển khai Device Binding:

```
DEVICE BINDING (Thiết bị tin cậy)
│
├── 1. ĐĂNG KÝ THIẾT BỊ LẦN ĐẦU
│   │
│   ├── Thu thập Device Fingerprint
│   │   ├── Hardware ID
│   │   ├── Device Model
│   │   ├── OS Version
│   │   └── App Instance ID
│   │
│   └── Xác thực OUT-OF-BAND (bắt buộc)
│       ├── Matrix OTP hoặc
│       └── SMS OTP
│       → Thiết bị được đánh dấu "Trusted"
│
├── 2. SỬ DỤNG SAU KHI BIND
│   │
│   └── Thiết bị trusted → Cho phép dùng Soft OTP
│       cho các thao tác nhạy cảm (bao gồm sau đổi MK)
│
└── 3. THIẾT BỊ MỚI / CHƯA BIND
    │
    └── Bắt buộc Matrix/SMS OTP (out-of-band)
        → Sau đó mới có thể bind và dùng Soft OTP
```

**Ưu điểm:**
- Giữ nguyên bảo mật out-of-band cho thiết bị mới
- Cho phép Soft OTP trên thiết bị đã xác thực
- Chuẩn bị cho việc sunset Matrix

### 4.6 Lộ trình sunset Matrix (Khuyến nghị)

```
GIAI ĐOẠN 1: Bổ sung VNeID + NFC chip
└── Mục đích: Đáp ứng C06, dùng cho eKYC và xác thực định danh
└── KHÔNG dùng cho: Xác thực sau đổi MK

GIAI ĐOẠN 2: Triển khai Device Binding
└── Thiết bị trusted → dùng Soft OTP cho mọi thao tác
└── Thiết bị mới → vẫn cần SMS OTP

GIAI ĐOẠN 3: Giảm dần Matrix
└── Không cấp mới, chỉ hỗ trợ TK cũ

GIAI ĐOẠN 4: Sunset Matrix hoàn toàn
└── Còn lại: SMS OTP + Soft OTP (trusted device)
```

### 4.7 Kiến trúc triển khai - Không phụ thuộc Core FSS

**Lưu ý quan trọng:** Các giải pháp thay thế thẻ ma trận (Email OTP, Device Binding, Biometric) có thể triển khai RIÊNG, không cần sửa Core Trading (FSS).

```
KIẾN TRÚC ĐỀ XUẤT
│
├── Mobile App (AgriSeco Pro)
│   ├── UI: Nhập OTP, xác thực Biometric
│   ├── Thu thập Device Fingerprint
│   └── GỌI Auth Service TRƯỚC khi gọi FSS
│
├── Auth Service (VIẾT MỚI - Backend riêng)
│   ├── Device Binding management
│   ├── Email OTP generation/verification  
│   ├── SMS OTP (tích hợp nhà mạng)
│   ├── Soft OTP verification (TOTP)
│   ├── Biometric token validation
│   └── Trả về: Session Token nếu verify OK
│
└── Core Trading (FSS) ← GIỮ NGUYÊN
    └── Chỉ cần check Session Token hợp lệ
    └── KHÔNG CẦN biết user verify bằng cách nào
```

**Flow xác thực:**

```
1. User muốn rút tiền
   │
2. Mobile App → Auth Service
   │  └── "Verify OTP/Biometric cho user X"
   │
3. Auth Service verify → Trả Session Token
   │
4. Mobile App → Core FSS
   │  └── "Rút tiền, đây là Session Token"
   │
5. Core FSS check token hợp lệ → Thực hiện
```

**Ưu điểm:**
- Không phụ thuộc vendor FSS
- Có thể triển khai nhanh bằng team nội bộ
- Dễ mở rộng thêm phương thức xác thực mới
- Core FSS giữ nguyên, giảm rủi ro

### 4.8 Thay Matrix bằng Biometric (bound device) - Phân tích chi tiết

**Kịch bản:** Sau đổi MK, đăng nhập lần đầu với MK mới → Bỏ Matrix → Dùng Biometric (thiết bị đã bind)

#### Điều kiện tiên quyết

```
ĐỂ DÙNG BIOMETRIC THAY MATRIX:

1. Device đã được BIND với tài khoản từ TRƯỚC
   └── Bind bằng cách nào? → SMS OTP hoặc Matrix (lần đầu)

2. Biometric đã được ĐĂNG KÝ trên device đó
   └── FaceID/TouchID đã setup trên điện thoại
   └── App đã liên kết Biometric với tài khoản

3. Đang đăng nhập từ CHÍNH THIẾT BỊ ĐÃ BIND
   └── Nếu đổi điện thoại → không dùng Biometric được
   └── Phải fallback về SMS OTP
```

#### Phân tích thay đổi cần thiết

```
HIỆN TẠI (sau đổi MK, đăng nhập lần đầu):
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│  Mobile App  │────▶│     ???      │────▶│   Core FSS   │
│  Hiển thị    │     │  Verify OTP  │     │  Cho đăng    │
│  Matrix/SMS  │     │  Matrix/SMS  │     │  nhập        │
└──────────────┘     └──────────────┘     └──────────────┘

CÂU HỎI CHÍNH: Logic "hiển thị options Matrix/SMS" nằm ở đâu?

TRƯỜNG HỢP A: Logic nằm ở Mobile App
├── App tự quyết định hiển thị gì
├── App gọi API verify tương ứng
├── → CHỈ CẦN SỬA MOBILE APP + THÊM AUTH SERVICE
│   ├── Thêm logic check: Device đã bind chưa?
│   ├── Nếu đã bind → Hiển thị option Biometric
│   ├── Nếu chưa bind → Chỉ hiển thị SMS OTP
│   └── Gọi Auth Service để verify Biometric
└── → KHÔNG CẦN SỬA FSS

TRƯỜNG HỢP B: Logic nằm ở FSS
├── FSS trả về danh sách options cho App hiển thị
├── FSS handle verification
├── → CẦN SỬA FSS hoặc THÊM MIDDLEWARE
│   ├── Option 1: Đề nghị FSS thêm Biometric option
│   └── Option 2: Thêm Auth Gateway ở giữa
└── → Phụ thuộc FSS support
```

#### Flow đề xuất (nếu App kiểm soát logic)

```
SAU ĐỔI MK - ĐĂNG NHẬP LẦN ĐẦU (MỚI)
│
├── 1. User nhập MK mới → Đăng nhập
│
├── 2. App kiểm tra: Device này đã bind chưa?
│   │
│   ├── ĐÃ BIND (trusted device)
│   │   ├── Hiển thị: [Biometric] hoặc [SMS OTP]
│   │   ├── User chọn Biometric → Verify FaceID/TouchID
│   │   ├── App gửi token lên Auth Service
│   │   ├── Auth Service verify → Trả session token
│   │   └── App gọi FSS với session token → Đăng nhập OK
│   │
│   └── CHƯA BIND (thiết bị mới)
│       ├── Hiển thị: CHỈ CÓ [SMS OTP]
│       ├── User nhập OTP
│       ├── Verify xong → Hỏi: "Có muốn bind thiết bị này không?"
│       └── Nếu đồng ý → Bind device → Lần sau dùng Biometric được
│
└── 3. FSS nhận session token → Cho đăng nhập
    └── FSS KHÔNG CẦN BIẾT verify bằng gì
```

#### Tóm tắt thay đổi

| Component | Thay đổi | Phụ thuộc FSS? |
|-----------|----------|:--------------:|
| **Mobile App** | Thêm logic check device bind, hiển thị Biometric option | Không |
| **Auth Service** (mới) | Handle Biometric verification, Device Binding | Không |
| **Core FSS** | Không sửa - chỉ nhận session token | - |
| **Database** | Thêm bảng Device Binding | Không |

**Kết luận:** Nếu logic hiển thị authentication options nằm ở **Mobile App** (không phải FSS quyết định), thì có thể triển khai **KHÔNG CẦN SỬA FSS**.

### 4.9 Câu hỏi cần làm rõ với FSS

| # | Câu hỏi | Mục đích |
|---|---------|----------|
| 1 | Logic detect "first login after password change" nằm ở đâu? (App hay FSS?) | Xác định cần sửa FSS hay không |
| 2 | FSS có API riêng cho bước xác thực OTP sau đổi MK không? | Xem có thể gọi API từ Auth Service |
| 3 | FSS có hỗ trợ custom authentication provider không? | Tích hợp Biometric provider |
| 4 | Có thể thêm Auth Service làm middleware trước FSS không? | Kiến trúc đề xuất |

**Kịch bản triển khai:**

```
KỊCH BẢN A: Logic ở Mobile App (ưu tiên)
└── Sửa App + Thêm Auth Service
└── Không phụ thuộc FSS
└── Triển khai nhanh

KỊCH BẢN B: Logic ở FSS, FSS cho phép custom
└── Implement Biometric provider, plug vào FSS
└── Phụ thuộc FSS support

KỊCH BẢN C: Logic ở FSS, FSS không cho phép
└── Thêm Auth Gateway middleware
└── Hoặc: Giữ SMS OTP, bỏ Matrix
└── Biometric chỉ dùng cho đăng nhập thường
```

---

## 5. Giải pháp đề xuất (Cần xem xét)

### 5.1 Các phương thức thay thế Matrix

#### Email OTP có thể thay thế SMS OTP không?

**So sánh:**

| Tiêu chí | SMS OTP | Email OTP |
|----------|:-------:|:---------:|
| Out-of-band | ✅ | ✅ |
| Cần "sở hữu" gì | SIM vật lý | Password email |
| Rủi ro bị hack từ xa | Thấp hơn (SIM swap khó) | Cao hơn (phishing phổ biến) |
| Phụ thuộc nhà mạng | ✅ Có | ❌ Không |
| Chi phí | Có (SMS fee) | Thấp |

**Kết luận:** 
- Nếu chấp nhận SMS OTP đơn lẻ → Có thể chấp nhận Email OTP đơn lẻ
- Tùy vào **risk appetite** của tổ chức
- Email OTP có thể dùng làm **backup** khi SMS lỗi

#### Biometric (đã đăng ký) có thể thay thế SMS OTP không?

**Cách Biometric hoạt động với tài khoản:**

```
ĐĂNG KÝ BIOMETRIC (lần đầu)
│
├── Bước 1: Đăng nhập bằng Password + OTP
├── Bước 2: Vào Cài đặt → Bật Biometric
├── Bước 3: Xác thực FaceID/TouchID trên thiết bị
├── Bước 4: SERVER GHI NHẬN:
│   ├── Tài khoản A
│   ├── Device ID: xyz123
│   └── Biometric: Đã kích hoạt
│
└── → Biometric GẮN VỚI TÀI KHOẢN + THIẾT BỊ trên server
```

**Khi xác thực:**

```
XÁC THỰC BIOMETRIC
│
├── Thiết bị verify FaceID/TouchID locally
├── Gửi lên server: "Device xyz123, biometric OK"
├── Server kiểm tra:
│   ├── Device xyz123 có đăng ký với tài khoản A? ✅
│   └── Biometric đã kích hoạt? ✅
└── → Cho phép
```

**Phân tích kịch bản tấn công:**

```
KẺ XẤU ĐỔI MẬT KHẨU → ĐĂNG NHẬP LẦN ĐẦU

Nếu dùng THIẾT BỊ CỦA KẺ XẤU:
├── Device mới chưa đăng ký với tài khoản
├── Server: "Device này chưa được liên kết"
└── → KHÔNG THỂ dùng Biometric ✅

Nếu dùng THIẾT BỊ NẠN NHÂN (đã đăng ký):
├── Device đã đăng ký với tài khoản
├── Nhưng FaceID/TouchID không khớp (khác người)
└── → KHÔNG THỂ pass Biometric ✅
```

**So sánh:**

| Phương thức | Kẻ xấu cần gì để vượt qua |
|-------------|---------------------------|
| SMS OTP | SIM của nạn nhân (1 thứ) |
| Email OTP | Password email nạn nhân (1 thứ) |
| **Biometric (đã đăng ký)** | Thiết bị nạn nhân + Sinh trắc học nạn nhân (2 thứ) |

**Kết luận:**
- Biometric (đã đăng ký với tài khoản) **TƯƠNG ĐƯƠNG hoặc MẠNH HƠN** SMS OTP
- Có thể dùng cho xác thực sau đổi mật khẩu
- **Điều kiện:** Biometric phải được đăng ký TRƯỚC với tài khoản qua OTP

#### Tổng hợp các phương thức thay thế Matrix

| Phương thức | Độ mạnh | Dùng đơn lẻ | Ghi chú |
|-------------|:-------:|:-----------:|---------|
| SMS OTP | ⭐⭐⭐ | ✅ Có thể | Phụ thuộc nhà mạng |
| Email OTP | ⭐⭐ | ⚠️ Tùy risk appetite | Rủi ro phishing cao hơn |
| Biometric (đã ĐK) | ⭐⭐⭐⭐ | ✅ Có thể | Cần 2 yếu tố (device + sinh trắc) |
| Soft OTP (trusted device) | ⭐⭐⭐ | ✅ Có thể | Cần Device Binding trước |
| VNeID / NFC chip | ⭐⭐⭐⭐⭐ | ✅ Có thể | Mạnh nhất, dùng cho eKYC |

#### Khuyến nghị cho xác thực sau đổi mật khẩu

```
SAU SUNSET MATRIX - CÁC LỰA CHỌN XÁC THỰC
│
├── Ưu tiên 1: Biometric (nếu đã đăng ký)
│   └── Mạnh nhất, cần thiết bị + sinh trắc học
│
├── Ưu tiên 2: SMS OTP
│   └── Out-of-band, cần SIM
│
├── Ưu tiên 3: Email OTP (backup)
│   └── Khi SMS lỗi
│
└── Ưu tiên 4: Soft OTP (nếu Device đã Bind)
    └── Cho thiết bị đã xác thực trước đó
```

**Lưu ý:** Đây là giải pháp đề xuất, cần xem xét và đánh giá thêm trước khi áp dụng.

### 5.2 Đề xuất cải tiến nộp tiền (Cần xem xét)

| # | Giải pháp | Mô tả | Độ ưu tiên |
|---|-----------|-------|:----------:|
| 1 | **Deep link Agribank** | Trong app AgriSeco → Nộp tiền → Tự mở app Agribank với thông tin điền sẵn | P0 |
| 2 | **QR động** | Tạo QR chứa đủ thông tin (số TK, số tiền, nội dung) → Quét = xong | P1 |
| 3 | **Tích hợp trong app Agribank** | Từ app Agribank → Chọn AgriSeco → Nộp thẳng | P0 |
| 4 | **Mở rộng ngân hàng** | Deep link/tích hợp với BIDV, VCB, Techcombank, MBBank... như TCBS | P2 |

**Flow đề xuất (One-touch):**

```
FLOW NỘP TIỀN MỚI (Đề xuất)
│
├── Bước 1: User mở app AgriSeco Pro
├── Bước 2: Chọn "Nộp tiền"
├── Bước 3: Chọn ngân hàng nguồn (Agribank/BIDV/VCB...)
├── Bước 4: Nhập số tiền
├── Bước 5: App TỰ ĐỘNG:
│   ├── Mở app ngân hàng qua Deep Link
│   └── Điền sẵn: Số TK nhận, Tên, Nội dung, Số tiền
└── Bước 6: User chỉ XÁC NHẬN trong app ngân hàng
```

**Lợi thế của AgriSeco:** Agribank là công ty mẹ (sở hữu 74,92%) → **CÓ THỂ** tích hợp sâu như TCBS-Techcombank.

**Ghi chú về giải pháp #4 (Mở rộng ngân hàng):**
- P2 vì phụ thuộc đàm phán với các ngân hàng bên ngoài
- Ưu tiên Agribank trước (P0) vì là công ty mẹ, dễ hợp tác
- Sau khi có flow Agribank hoạt động tốt → mở rộng ra các ngân hàng khác
- Tham khảo: TCBS đã tích hợp với BIDV, VPBank, TPBank, Viettel Money...

### 5.3 Đề xuất tích hợp Trái phiếu Agribank (Cần xem xét)

**Hiện trạng:** Trái phiếu Agribank chưa có trong app AgriSeco Pro (xem Gap 2.1).

**Đề xuất:**

| # | Tính năng | Mô tả | Độ ưu tiên |
|---|-----------|-------|:----------:|
| 1 | **Xem danh mục trái phiếu** | Hiển thị các đợt phát hành, kỳ hạn, lãi suất | P0 |
| 2 | **Đặt mua trực tiếp** | Mua trái phiếu trong app, xác thực bằng OTP | P0 |
| 3 | **Theo dõi số dư** | Xem trái phiếu đang sở hữu, ngày đáo hạn, lãi dự kiến | P0 |
| 4 | **Bán/Chuyển nhượng** | Giao dịch thứ cấp (nếu có) | P1 |
| 5 | **Thông báo** | Nhắc đáo hạn, thông báo đợt phát hành mới | P1 |

```
FLOW GIAO DỊCH TRÁI PHIẾU (Đề xuất)
│
├── Xem danh mục
│   ├── Trái phiếu đang phát hành
│   │   ├── Mã TP, Kỳ hạn, Lãi suất
│   │   └── Số lượng còn, Ngày kết thúc đợt
│   └── Trái phiếu đang sở hữu
│       ├── Số lượng, Giá mua
│       ├── Ngày đáo hạn
│       └── Lãi dự kiến
│
├── Mua trái phiếu
│   ├── Chọn mã TP → Nhập số lượng
│   ├── Xác nhận bằng PIN/OTP
│   └── Trừ tiền từ TKCK → Cộng TP vào danh mục
│
└── Theo dõi
    ├── Dashboard: Tổng giá trị TP, Lãi đã nhận, Lãi dự kiến
    └── Thông báo: Đáo hạn sắp tới, Đợt phát hành mới
```

**Lợi thế:**
- Agribank là công ty mẹ → Dữ liệu trái phiếu sẵn có
- Khách hàng AgriSeco có nhu cầu đầu tư an toàn → Trái phiếu Agribank phù hợp
- Tăng tỷ lệ giữ chân khách (retention) - không cần ra ngoài hệ thống

### 5.4 Đề xuất Mobile Web nhúng trong app Agribank (Cần xem xét)

**Mục đích:** Khách hàng Agribank có thể sử dụng TKCK **ngay trong app Agribank** mà không cần mở app AgriSeco.

**Đề xuất:**

| # | Tính năng | Mô tả | Độ ưu tiên |
|---|-----------|-------|:----------:|
| 1 | **Mobile Web (WebView)** | Giao diện web responsive nhúng trong app Agribank | P0 |
| 2 | **SSO với Agribank** | Đăng nhập tự động qua session Agribank | P0 |
| 3 | **Đầy đủ tính năng cơ bản** | Xem danh mục, Đặt lệnh, Sổ lệnh, Nộp/Rút tiền | P0 |
| 4 | **Nộp tiền liền mạch** | Chuyển tiền từ TK Agribank → TKCK trong 1 flow | P0 |
| 5 | **Deep link ngược** | Từ WebView mở tính năng nâng cao trên app AgriSeco | P1 |

```
KIẾN TRÚC MOBILE WEB
│
├── App Agribank
│   └── WebView nhúng AgriSeco
│       ├── SSO: Tự động đăng nhập qua token Agribank
│       ├── Giao diện: Responsive, tối ưu cho mobile
│       └── Tính năng:
│           ├── Xem tài sản, danh mục
│           ├── Xem bảng giá
│           ├── Đặt lệnh Mua/Bán/Hủy/Sửa
│           ├── Sổ lệnh, Lịch sử
│           ├── Nộp tiền (chuyển từ TK Agribank)
│           └── Rút tiền (chuyển về TK Agribank)
│
└── Tính năng nâng cao → Deep link mở app AgriSeco
    ├── Phân tích chi tiết
    ├── Khuyến nghị
    ├── Cài đặt nâng cao
    └── ...
```

**Lợi ích:**

| Đối tượng | Lợi ích |
|-----------|---------|
| **Khách hàng Agribank** | Không cần cài thêm app, dùng ngay trong app quen thuộc |
| **AgriSeco** | Tiếp cận 40+ triệu KH Agribank, tăng conversion |
| **Agribank** | Mở rộng dịch vụ tài chính, tăng giá trị app |

**Tham khảo:**
- TCBS nhúng trong Techcombank Mobile
- VPS Mobile nhúng trong một số app ngân hàng đối tác

### 5.5 Đề xuất tích hợp danh sách môi giới trong app (Cần xem xét)

**Hiện trạng:** Khi xem danh sách môi giới, app mở ra trang web bên ngoài (arg.vn) → Trải nghiệm không tốt.

**Vấn đề:**

| # | Vấn đề | Mô tả |
|---|--------|-------|
| 1 | **Redirect ra ngoài app** | User phải thoát app để xem danh sách môi giới |
| 2 | **Không có quick action** | Muốn gọi điện/nhắn Zalo phải copy số → mở app khác |
| 3 | **Trải nghiệm rời rạc** | Mất context, khó quay lại app |

**Đề xuất:**

| # | Tính năng | Mô tả | Độ ưu tiên |
|---|-----------|-------|:----------:|
| 1 | **Danh sách trong app** | Hiển thị danh sách môi giới native, không redirect | P1 |
| 2 | **Click-to-call** | Nhấn số điện thoại → Mở app gọi điện ngay | P1 |
| 3 | **Click-to-Zalo** | Nhấn icon Zalo → Mở Zalo chat với môi giới | P1 |
| 4 | **Tìm kiếm/Lọc** | Tìm theo tên, khu vực, chi nhánh | P2 |
| 5 | **Môi giới chăm sóc** | Highlight môi giới đang phụ trách TK của user | P1 |

```
DANH SÁCH MÔI GIỚI (Đề xuất)
│
├── Hiển thị trong app (native)
│   ├── Ảnh đại diện
│   ├── Họ tên
│   ├── Chức vụ / Chi nhánh
│   └── Thông tin liên hệ
│
├── Quick Actions
│   ├── 📞 Gọi điện → tel://0912345678
│   ├── 💬 Zalo → zalo://chat?phone=0912345678
│   └── ✉️ Email → mailto:broker@agriseco.com.vn
│
└── Môi giới của tôi (highlight)
    └── Hiển thị đầu tiên, có badge "Đang chăm sóc"
```

**Lợi ích:**
- Trải nghiệm liền mạch, không thoát app
- Liên hệ môi giới nhanh hơn (1 chạm)
- Tăng tương tác giữa KH và môi giới

**Tổng đài AgriSeco:**
- Hiện tại: Nhấn "Tổng đài" → Mở trang web → Rồi mới gọi
- Đề xuất: Nhấn "Tổng đài" → **Gọi trực tiếp** (chỉ có 1 số, không cần mở trang)

**Zalo:**
- Hiện tại: Mở ra 2 tầng menu → Trông rất rối, UX kém
- Đề xuất: Nhấn Zalo → **Mở Zalo trực tiếp** (deep link đến OA AgriSeco)

### 5.6 Đề xuất làm giàu thông tin thị trường (Cần xem xét)

**Hiện trạng:** Thông tin thị trường và chi tiết mã CK còn cơ bản so với đối thủ.

**Đề xuất bổ sung:**

| # | Hạng mục | Nội dung | Độ ưu tiên |
|---|----------|----------|:----------:|
| 1 | **Bảng thống kê thị trường** | Top tăng/giảm, Top thanh khoản, Khối ngoại mua/bán ròng, Tự doanh CTCK | P1 |
| 2 | **Thống kê theo ngành** | Biến động theo ngành (Ngân hàng, BĐS, Công nghệ...), So sánh P/E ngành | P1 |
| 3 | **Chi tiết mã CK - Cơ bản** | P/E, P/B, EPS, ROE, ROA, Vốn hóa, Room ngoại | P1 |
| 4 | **Chi tiết mã CK - Kỹ thuật** | RSI, MACD, MA, Bollinger Bands, Volume profile | P2 |
| 5 | **Lịch sự kiện** | Chia cổ tức, ĐHCĐ, Phát hành thêm, Ngày GDKHQ | P1 |
| 6 | **Báo cáo tài chính** | BCTC tóm tắt, Biểu đồ doanh thu/lợi nhuận qua các quý | P2 |
| 7 | **So sánh mã** | So sánh 2-3 mã cùng ngành (chỉ số, biểu đồ) | P2 |

```
THÔNG TIN THỊ TRƯỜNG (Đề xuất)
│
├── Dashboard thị trường
│   ├── Chỉ số: VN-Index, HNX, UPCOM (có biểu đồ)
│   ├── Top tăng / giảm / thanh khoản
│   ├── Khối ngoại: Mua ròng / Bán ròng
│   └── Thống kê theo ngành
│
└── Chi tiết mã CK
    ├── Tab Tổng quan: Giá, KL, Biểu đồ đơn giản
    ├── Tab Phân tích cơ bản: P/E, P/B, EPS, ROE, BCTC
    ├── Tab Phân tích kỹ thuật: RSI, MACD, MA, BB
    ├── Tab Lịch sự kiện: Cổ tức, ĐHCĐ, Quyền mua
    └── Tab Tin tức: Tin liên quan đến mã
```

**Tham khảo đối thủ:**
- TCBS: Có đầy đủ TA/FA, so sánh mã, screener
- SSI: iBoard có thống kê chi tiết, heat map
- VPS: SmartOne có phân tích chuyên sâu

### 5.7 Đề xuất cải tiến phần Khuyến nghị (Cần xem xét)

**Hiện trạng:** Phần khuyến nghị chỉ hiển thị danh sách báo cáo mới nhất → Chưa actionable.

**Vấn đề:**

| # | Vấn đề | Mô tả |
|---|--------|-------|
| 1 | **Chỉ có báo cáo** | User phải đọc báo cáo để tìm khuyến nghị |
| 2 | **Thiếu tổng hợp** | Không có danh sách mã khuyến nghị tập trung |
| 3 | **Thiếu điểm mua/bán** | Không có giá mục tiêu, điểm vào/ra rõ ràng |

**Đề xuất:**

| # | Tính năng | Mô tả | Độ ưu tiên |
|---|-----------|-------|:----------:|
| 1 | **Danh sách khuyến nghị** | Bảng tổng hợp các mã đang khuyến nghị MUA/BÁN/GIỮ | P1 |
| 2 | **Giá mục tiêu** | Hiển thị giá dự báo, upside/downside % | P1 |
| 3 | **Điểm mua/bán** | Vùng giá khuyến nghị mua vào, giá cắt lỗ | P1 |
| 4 | **Trạng thái** | Đang theo dõi / Đã đạt mục tiêu / Cắt lỗ | P1 |
| 5 | **Lịch sử hiệu suất** | Tỷ lệ khuyến nghị đúng của phòng phân tích | P2 |

```
KHUYẾN NGHỊ (Đề xuất)
│
├── Danh sách khuyến nghị (Dashboard)
│   │
│   │  Mã   │ Khuyến nghị │ Giá hiện tại │ Giá mục tiêu │ Upside │ Điểm mua │
│   │───────┼─────────────┼──────────────┼──────────────┼────────┼──────────│
│   │  VNM  │     MUA     │    75,000    │    85,000    │ +13.3% │ 72-76k   │
│   │  FPT  │     GIỮ     │   125,000    │   130,000    │  +4.0% │    -     │
│   │  VIC  │     BÁN     │    42,000    │    38,000    │ -9.5%  │    -     │
│
├── Chi tiết khuyến nghị
│   ├── Mã CK + Khuyến nghị (MUA/BÁN/GIỮ)
│   ├── Giá mục tiêu + Upside/Downside
│   ├── Vùng giá mua vào (VD: 72,000 - 76,000)
│   ├── Giá cắt lỗ (VD: 68,000)
│   ├── Thời gian nắm giữ dự kiến
│   └── Link báo cáo chi tiết
│
└── Lịch sử & Hiệu suất
    ├── Các khuyến nghị đã đóng
    ├── Tỷ lệ đúng: X%
    └── Lợi nhuận trung bình: Y%
```

**Lợi ích:**
- User biết ngay mua gì, giá nào, bán khi nào
- Actionable - không cần đọc hết báo cáo
- Minh bạch hiệu suất khuyến nghị

### 5.8 Đề xuất khảo sát khẩu vị rủi ro (Cần xem xét)

**Mục đích:** Đánh giá profile khách hàng → Đưa ra lời khuyên về **lựa chọn sản phẩm đầu tư** phù hợp.

**Đề xuất:**

| # | Tính năng | Mô tả | Độ ưu tiên |
|---|-----------|-------|:----------:|
| 1 | **Bài khảo sát** | 10-15 câu hỏi về mục tiêu, thời gian, khả năng chịu lỗ | P1 |
| 2 | **Phân loại profile** | Bảo thủ / Cân bằng / Tăng trưởng / Mạo hiểm | P1 |
| 3 | **Khuyến nghị sản phẩm** | Gợi ý tỷ lệ phân bổ theo profile | P1 |
| 4 | **Đánh giá lại định kỳ** | Nhắc làm lại khảo sát sau 6-12 tháng | P2 |

```
KHẢO SÁT KHẨU VỊ RỦI RO
│
├── Bài khảo sát (10-15 câu)
│   ├── Mục tiêu đầu tư? (Bảo toàn / Tăng trưởng / Thu nhập)
│   ├── Thời gian đầu tư dự kiến? (<1 năm / 1-3 năm / >3 năm)
│   ├── Khả năng chịu lỗ tạm thời? (10% / 20% / 30%+)
│   ├── Kinh nghiệm đầu tư? (Mới / Trung bình / Giàu kinh nghiệm)
│   └── ...
│
├── Kết quả: Profile khách hàng
│   │
│   │  Profile      │ Đặc điểm                              │
│   │───────────────┼───────────────────────────────────────│
│   │  Bảo thủ      │ Ưu tiên bảo toàn vốn, chấp nhận lãi thấp │
│   │  Cân bằng     │ Cân đối rủi ro và lợi nhuận           │
│   │  Tăng trưởng  │ Chấp nhận rủi ro để tìm lợi nhuận cao │
│   │  Mạo hiểm     │ Sẵn sàng rủi ro cao, kỳ vọng lợi nhuận lớn │
│
└── Khuyến nghị sản phẩm (ví dụ)
    │
    │  Profile      │ Trái phiếu │ Cổ phiếu Blue-chip │ Cổ phiếu tăng trưởng │
    │───────────────┼────────────┼────────────────────┼──────────────────────│
    │  Bảo thủ      │    70%     │        25%         │          5%          │
    │  Cân bằng     │    40%     │        40%         │         20%          │
    │  Tăng trưởng  │    20%     │        40%         │         40%          │
    │  Mạo hiểm     │    10%     │        30%         │         60%          │
```

**Lưu ý:**
- Chỉ khuyến nghị **loại sản phẩm** (trái phiếu, cổ phiếu blue-chip, tăng trưởng...)
- **KHÔNG** khuyến nghị cụ thể mã nào, mua bao nhiêu (đó là việc của môi giới/tư vấn)
- Cần disclaimer: "Đây chỉ là gợi ý, không phải tư vấn đầu tư"

### 5.9 Đề xuất thiết kế lại giao diện (Cần xem xét - P2)

**Hiện trạng:** Giao diện app AgriSeco Pro đã khá cũ và quá cơ bản so với đối thủ.

**Vấn đề:**

| # | Vấn đề | Mô tả |
|---|--------|-------|
| 1 | **Giao diện cũ** | Thiết kế visual chưa theo xu hướng hiện đại |
| 2 | **UX cơ bản** | Nhiều bước thao tác, chưa tối ưu flow người dùng |
| 3 | **Thiếu data viz** | Chưa có biểu đồ, chart trực quan như đối thủ |
| 4 | **Thiếu cá nhân hóa** | Chưa có dashboard tùy chỉnh theo nhu cầu user |

**Đề xuất cải tiến:**

| # | Hạng mục | Mô tả | Độ ưu tiên |
|---|----------|-------|:----------:|
| 1 | **UI Refresh** | Thiết kế lại visual: màu sắc, typography, spacing | P2 |
| 2 | **UX Improvement** | Tối ưu flow: giảm số bước, thêm shortcuts | P2 |
| 3 | **Data Visualization** | Thêm biểu đồ danh mục, chart tăng/giảm, pie chart phân bổ | P2 |
| 4 | **Dashboard cá nhân** | Widget tùy chỉnh: mã yêu thích, cảnh báo, tin tức | P3 |
| 5 | **Dark mode** | Hỗ trợ giao diện tối | P3 |

**Ghi chú:**
- Đây là hạng mục P2/P3 - thực hiện sau các tính năng core (bảo mật, nộp tiền, trái phiếu)
- Cần nghiên cứu UX với nhóm người dùng thực tế trước khi redesign
- Tham khảo: TCBS, SSI có giao diện hiện đại hơn

### 5.10 Khuyến nghị bảo mật - Khi nào dùng PIN vs OTP

```
PIN (Xác nhận nhanh)
└── Dùng cho:
    ├── Đặt lệnh Mua/Bán/Hủy/Sửa
    └── Lý do: Tần suất cao, tiền vẫn trong TK, có thể hủy/sửa

OTP (Xác nhận mạnh)
└── Dùng cho:
    ├── Rút tiền, Chuyển tiền
    ├── Đổi mật khẩu, Đổi PIN
    ├── Thay đổi tài khoản ngân hàng thụ hưởng
    ├── Chuyển chứng khoán
    ├── Giao dịch vượt ngưỡng (VD: >500 triệu)
    └── Đăng nhập từ thiết bị mới
    
    Lý do: Rủi ro cao, không hoàn tác được
```

**Công thức:** `Rủi ro cao + Không hoàn tác = OTP`

### 5.11 Khuyến nghị eKYC - Đáp ứng Thông tư C06

```
SHOULD-BE
│
├── Chụp CCCD 2 mặt ✅ (đã có)
├── Chụp khuôn mặt ✅ (đã có)
├── Quét mã QR trên CCCD ← CẦN THÊM
├── Đọc chip NFC ← CẦN THÊM
└── Tích hợp VNID (Bộ Công an) ← CẦN THÊM
```

### 5.12 Khuyến nghị eContract + eSign - Bỏ ký giấy

```
SHOULD-BE
│
├── 1. eKYC đầy đủ (QR + Chip + VNID)
├── 2. Hợp đồng điện tử (eContract)
│   └── Xác thực bởi Bộ Công thương
├── 3. Chữ ký số (eSign)
│   └── Từ CA được công nhận (VNPT-CA, Viettel-CA, FPT.eContract...)
├── 4. Xác nhận bằng OTP + Biometric
└── 5. Kích hoạt tài khoản ngay

KHÔNG CẦN KÝ GIẤY
```

**Cơ sở pháp lý (cho phép, không bắt buộc):**

| Văn bản | Trạng thái | Nội dung | Bắt buộc? |
|---------|:----------:|----------|:---------:|
| Luật GDĐT 2005 (Điều 33) | ✅ Đã ban hành | Cho phép giao dịch điện tử | Không |
| **Luật GDĐT 2023** | ✅ Đã ban hành (hiệu lực 01/07/2024) | Thay thế luật 2005, quy định chữ ký số | Không |
| NĐ 130/2018/NĐ-CP | ✅ Đã ban hành | Hướng dẫn chữ ký số | Không |
| TT 16/2019/TT-BTTTT | ✅ Đã ban hành | Hướng dẫn chi tiết | Không |
| Dự thảo sửa Luật CK | ⚠️ Dự thảo (dự kiến 3/2027) | Chưa biết nội dung cụ thể | Chưa rõ |

**Kết luận:** Các văn bản CHO PHÉP dùng eContract/eSign, KHÔNG BẮT BUỘC cho mở TK chứng khoán. Đối thủ dùng vì cải thiện UX, không phải vì pháp luật bắt buộc.

---

## 6. Tổng hợp & Roadmap

### 6.1 Đánh giá hiện trạng (Mapping với giải pháp)

| # | Hạng mục | Hiện trạng | Vấn đề | Giải pháp | Priority |
|:-:|----------|:----------:|--------|-----------|:--------:|
| 1 | **eKYC** | ❌ | Chưa đạt C06: thiếu QR, NFC chip, VNeID | eKYC đáp ứng C06 | P0 |
| 2 | **Liên kết VNeID** | ❌ | TK CK chưa liên kết VNeID (NĐ 320/2026) | Liên kết TK với VNeID | P0 |
| 3 | **Tích hợp Agribank** | ❌ | Chỉ redirect, chưa nhúng trong app Agribank | Mobile Web nhúng app Agribank | P1 |
| 4 | **Trái phiếu Agribank** | ❌ | Không có trong app (sản phẩm công ty mẹ) | Trái phiếu Agribank | P1 |
| 5 | **Nộp tiền** | ⚠️ | Chỉ mở trang hướng dẫn, nhiều cách thủ công bên ngoài app | Deep link + QR động | P1 |
| 6 | **Mở tài khoản** | ⚠️ | Còn ký hợp đồng giấy | eContract + eSign | P1 |
| 7 | **Bảo mật OTP** | ⚠️ | Còn dùng thẻ ma trận, chưa Device Binding | Sunset Matrix → Biometric | P1 |
| 8 | **Khảo sát KH** | ❌ | Chưa có khảo sát khẩu vị rủi ro | Khảo sát khẩu vị rủi ro | P1 |
| 9 | **Hỗ trợ/Liên hệ** | ⚠️ | Redirect ra ngoài (arg.vn, Zalo 2 tầng) | Môi giới + Tổng đài trong app | P2 |
| 10 | **Thống kê thị trường** | ⚠️ | Thiếu Top tăng/giảm, Khối ngoại, Thống kê ngành (đối thủ có iBoard, SmartOne) | Thống kê + Chi tiết mã | P2 |
| 11 | **Khuyến nghị** | ⚠️ | Chỉ báo cáo, thiếu điểm mua/bán | Khuyến nghị có điểm mua/bán | P2 |
| 12 | **Giao diện** | ⚠️ | Thiết kế đã cũ, UX cơ bản | UI/UX Refresh | P3 |
| 13 | **Mở rộng ngân hàng** | ❌ | Chỉ hỗ trợ Agribank | Deep link BIDV, VCB, TCB... | P3 |
| - | **Giao dịch CK cơ sở** | ✅ | Đủ: Mua/Bán/Hủy/Sửa, Margin, Ứng trước | - | - |

**Tổng kết:**
- ❌ Chưa có / Chưa đạt: 6 hạng mục
- ⚠️ Cần cải tiến: 6 hạng mục  
- ✅ Đủ: 1 hạng mục (Giao dịch CK cơ sở)

### 6.2 Tổng hợp đề xuất theo độ ưu tiên

#### P0 - Ưu tiên cao nhất (Bắt buộc pháp lý)

| # | Đề xuất | Mô tả | Cơ sở pháp lý |
|---|---------|-------|---------------|
| 1 | **eKYC đáp ứng C06** | Quét QR, NFC chip, tích hợp VNeID | Đề án 06, Luật Căn cước 2023 |
| 2 | **Liên kết TK với VNeID** | TK CK phải liên kết VNeID | NĐ 320/2026 - Deadline 31/12/2026 |

#### P1 - Ưu tiên cao (Tăng doanh thu / Cải tiến trải nghiệm)

| # | Đề xuất | Mô tả | Section |
|---|---------|-------|:-------:|
| 3 | **Mobile Web nhúng app Agribank** | WebView đầy đủ tính năng, SSO với Agribank | 5.4 |
| 4 | **Trái phiếu Agribank** | Xem, mua, theo dõi số dư trong app | 5.3 |
| 5 | **Deep link Agribank** | Nộp tiền one-touch, mở app NH với thông tin sẵn | 5.2 |
| 6 | **eContract + eSign** | Bỏ ký hợp đồng giấy (cải tiến UX, chưa bắt buộc) | 5.12 |
| 7 | **Sunset thẻ ma trận** | Migrate sang Soft OTP + Device Binding | 4.4, 4.5 |
| 8 | **QR động nộp tiền** | QR chứa đủ thông tin, quét = xong | 5.2 |
| 9 | **Khảo sát khẩu vị rủi ro** | Profile KH, gợi ý phân bổ sản phẩm | 5.8 |

#### P2 - Ưu tiên trung bình

| # | Đề xuất | Mô tả | Section |
|---|---------|-------|:-------:|
| 10 | **Danh sách môi giới trong app** | Click-to-call, Click-to-Zalo | 5.5 |
| 11 | **Tổng đài gọi trực tiếp** | 1 chạm = gọi, không mở trang | 5.5 |
| 12 | **Thống kê thị trường** | Top tăng/giảm, Khối ngoại, Thống kê ngành | 5.6 |
| 13 | **Chi tiết mã CK** | P/E, EPS, ROE, Lịch sự kiện | 5.6 |
| 14 | **Khuyến nghị có điểm mua/bán** | Giá mục tiêu, vùng giá mua, cắt lỗ | 5.7 |

#### P3 - Thực hiện sau

| # | Đề xuất | Mô tả | Section |
|---|---------|-------|:-------:|
| 15 | **Mở rộng ngân hàng** | Deep link BIDV, VCB, TCB, MBBank... | 5.2 |
| 16 | **Phân tích kỹ thuật** | RSI, MACD, Bollinger Bands | 5.6 |
| 17 | **So sánh mã** | So sánh 2-3 mã cùng ngành | 5.6 |
| 18 | **UI/UX Refresh** | Thiết kế lại giao diện, tối ưu flow | 5.9 |
| 19 | **Lịch sử hiệu suất khuyến nghị** | Tỷ lệ đúng, lợi nhuận trung bình | 5.7 |
| 20 | **Dashboard cá nhân** | Widget tùy chỉnh | 5.9 |
| 21 | **Dark mode** | Giao diện tối | 5.9 |

### 6.3 Lợi thế cạnh tranh của AgriSeco

| Lợi thế | Cách tận dụng |
|---------|---------------|
| **Agribank là công ty mẹ (74,92%)** | Deep link, tích hợp 2 chiều, dữ liệu trái phiếu |
| **Mạng lưới Agribank rộng** | Hỗ trợ KH nông thôn, tích hợp chi nhánh |
| **Trái phiếu Agribank** | Sản phẩm đầu tư an toàn, phù hợp KH bảo thủ |

### 6.4 So sánh với đối thủ (Tóm tắt)

| AgriSeco | TCBS | SSI | VPS |
|:--------:|:----:|:---:|:---:|
| CK cơ sở ✅ | Đầy đủ sản phẩm | Đầy đủ sản phẩm | Đầy đủ sản phẩm |
| Thiếu: TP, CCQ, PS | eKYC C06 ✅ | eKYC C06 ✅ | eKYC C06 ✅ |
| Còn thẻ ma trận | Bỏ thẻ ma trận | Bỏ thẻ ma trận | Bỏ thẻ ma trận |
| Nộp tiền cũ | One-touch + 5 cách | Hiện đại | Hiện đại |
| Thống kê cơ bản | TA/FA đầy đủ | iBoard chuyên sâu | SmartOne |

### 6.5 Roadmap đề xuất (Theo thứ tự ưu tiên)

**Nguyên tắc sắp xếp:**
1. **WAVE 1**: Tuân thủ pháp luật (BẮT BUỘC - không làm = vi phạm)
2. **WAVE 2**: Tăng doanh thu & lợi nhuận (ROI cao)
3. **WAVE 3**: Thu hút khách hàng mới & tăng trải nghiệm

```
═══════════════════════════════════════════════════════════════════════
WAVE 1: TUÂN THỦ PHÁP LUẬT (BẮT BUỘC) [P0]
═══════════════════════════════════════════════════════════════════════
│
├── 1. eKYC đáp ứng Đề án 06 / C06 🔴
│   ├── Quét mã QR trên CCCD
│   ├── Đọc chip NFC
│   ├── Tích hợp VNeID
│   ├── Deadline: 01/10/2024 (GD online cần CCCD chip)
│   └── Rủi ro: Vi phạm UBCKNN, mất quyền GD online
│
└── 2. Liên kết TK chứng khoán với VNeID 🔴
    ├── Theo Nghị định 320/2026/NĐ-CP
    ├── Deadline: 31/12/2026
    └── Rủi ro: Vi phạm Nghị định, bị xử phạt

═══════════════════════════════════════════════════════════════════════
WAVE 2: TĂNG DOANH THU & CẢI TIẾN TRẢI NGHIỆM [P1]
═══════════════════════════════════════════════════════════════════════
│
├── 3. Mobile Web nhúng app Agribank ⭐⭐⭐
│   ├── Tiếp cận 40+ triệu KH Agribank NGAY
│   ├── Không cần KH cài app mới
│   ├── SSO với Agribank
│   └── ROI: Cao nhất - mở rộng thị trường lớn
│
├── 4. Trái phiếu Agribank ⭐⭐⭐
│   ├── Sản phẩm PHÙ HỢP KH bảo thủ (đặc điểm KH Agribank)
│   ├── Doanh thu mới từ sản phẩm có sẵn của công ty mẹ
│   └── ROI: Cao - margin tốt, KH sẵn có
│
├── 5. Deep link + Nộp tiền one-touch ⭐⭐
│   ├── GIẢM MA SÁT nộp tiền vào TKCK
│   ├── KH nộp tiền dễ hơn → giao dịch nhiều hơn
│   └── ROI: Trung bình - tăng volume giao dịch
│
├── 6. eContract + eSign
│   ├── Bỏ ký hợp đồng giấy
│   ├── Giảm chi phí vận hành, mở TK nhanh
│   └── Lưu ý: Chưa bắt buộc pháp lý, nhưng cải thiện UX
│
├── 7. Sunset thẻ ma trận
│   ├── Migrate sang Soft OTP + Device Binding
│   ├── Có thể triển khai riêng (Auth Service), không phụ thuộc FSS
│   ├── Giảm chi phí in/gửi thẻ
│   └── Xem kiến trúc đề xuất tại section 4.7
│
└── 8. Khảo sát khẩu vị rủi ro
    ├── Cross-sell hiệu quả hơn
    └── Gợi ý sản phẩm phù hợp

═══════════════════════════════════════════════════════════════════════
WAVE 3: THU HÚT KHÁCH HÀNG & NÂNG CAO TRẢI NGHIỆM [P2]
═══════════════════════════════════════════════════════════════════════
│
├── 9. Danh sách môi giới + Tổng đài trong app
│   └── 1 chạm gọi/Zalo → giảm churn
│
├── 10. Thống kê thị trường + Chi tiết mã
│   └── Cạnh tranh với TCBS, SSI, VPS
│
├── 11. Khuyến nghị có điểm mua/bán
│   └── ACTIONABLE - KH biết mua gì, giá nào
│
└── 12. QR động nộp tiền
    └── QR chứa đủ thông tin, quét = xong

═══════════════════════════════════════════════════════════════════════
WAVE 4: NICE-TO-HAVE [P3]
═══════════════════════════════════════════════════════════════════════
│
├── 13. UI/UX Refresh
├── 14. Mở rộng ngân hàng (BIDV, VCB...)
├── 15. Phân tích kỹ thuật nâng cao
├── 16. Dashboard cá nhân
└── 17. Dark mode
```

### 6.6 Tóm tắt ưu tiên

| Wave | Priority | Mục tiêu | Đề xuất chính | Deadline/Lý do |
|:----:|:--------:|----------|---------------|----------------|
| **1** | **P0** | Tuân thủ pháp luật | eKYC C06, Liên kết VNeID | 31/12/2026 (NĐ 320) |
| **2** | **P1** | Tăng doanh thu | Mobile Web Agribank, Trái phiếu, Deep link, eContract, Sunset Matrix | ROI cao |
| **3** | **P2** | Thu hút KH | Hỗ trợ trong app, Khuyến nghị, Thống kê | Cạnh tranh |
| **4** | **P3** | Nice-to-have | UI/UX, Mở rộng NH, Dashboard | Tùy nguồn lực |

**Lưu ý:** 
- **Wave 1 (P0):** BẮT BUỘC pháp lý, có deadline cụ thể
- **Wave 2 (P1):** Cải tiến quan trọng, ROI cao, nhưng không bắt buộc pháp lý
- **eContract/eSign:** Chưa có văn bản bắt buộc, chỉ có văn bản cho phép
- **Sunset Matrix:** Có thể triển khai Auth Service riêng, không phụ thuộc FSS (xem section 4.7)
- Cần làm rõ với FSS về flow xác thực sau đổi MK (xem section 4.8)

---

## Nguồn tham khảo

1. Khảo sát app AgriSeco Pro (App Store / Google Play)
2. Chứng khoán Rồng Việt - eContract/eSign (27/05/2024)
3. VnExpress - Đề xuất sửa Luật CK (05/06/2026)
4. Thông tư C06 - Bộ Công an

---

*Ghi chú: Phần "Khuyến nghị" là best practices, cần đối chiếu với hệ thống thực tế.*
