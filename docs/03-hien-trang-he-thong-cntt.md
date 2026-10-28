---
title: Hiện trạng hệ thống CNTT Agriseco
authors:
  - date: 2026-10-27
    email: "hang.do@difisoft.com"
    change: "Initial creation — tổng hợp từ khảo sát thực tế và phỏng vấn"
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Cập nhật: Trái phiếu Agribank KHÔNG CÓ trên mobile app (không phải chỉ giới thiệu)"
  - date: 2026-10-28
    email: "hang.do@difisoft.com"
    change: "Thêm mục 5: Nhân sự CNTT — phụ thuộc vendor cao, đội dev mỏng"
---

# Hiện trạng CNTT Agriseco

## Bản đồ tư duy

```
                              AGRISECO
                                 │
        ┌────────────────────────┼────────────────────────┐
        │                        │                        │
   ┌────▼────┐             ┌─────▼─────┐            ┌─────▼─────┐
   │  CORE   │             │  KÊNH     │            │  TÍCH HỢP │
   │ TRADING │             │  PHÂN PHỐI│            │  BÊN NGOÀI│
   └────┬────┘             └─────┬─────┘            └─────┬─────┘
        │                        │                        │
        │                   ┌────┼────┐              ┌────┼────┐
        ▼                   ▼    ▼    ▼              ▼         ▼
   ┌─────────┐         ┌────┐ ┌────┐ ┌────┐    ┌─────────┐ ┌────────┐
   │  FLEX   │         │App │ │Web │ │Web │    │ Kế toán │ │Ngân hàng│
   │  (FSS)  │         │Pro │ │GD  │ │GT  │    └─────────┘ └────┬───┘
   └─────────┘         └────┘ └────┘ └────┘                     │
                          │                               ┌─────▼─────┐
                          │                               │ Agribank? │
                     ┌────▼────┐                          │(chưa chắc)│
                     │ Vệ tinh │                          └───────────┘
                     │ eKYC,   │
                     │ mở TK   │
                     └─────────┘
```

---

## 1. Hệ thống Core

```
FLEX (FSS)
├── Giao dịch chứng khoán cơ sở ✅
├── Giao dịch phái sinh         ❌ chưa có
└── Giao dịch trái phiếu        ❌ chưa có (không có trên mobile app)
```

**Nhà cung cấp:** FSS (FPT Software Solutions)

---

## 2. Kênh phân phối

```
MOBILE APP
└── AgriSeco Pro (FSS)
    ├── Giao dịch CK cơ sở ✅
    └── Trái phiếu Agribank ❌ KHÔNG CÓ trên app

WEBSITE
├── Web giới thiệu công ty
└── Web giao dịch cho khách hàng

VỆ TINH
└── Trang mở tài khoản online (eKYC)
```

---

## 3. Tích hợp

```
ĐÃ CÓ
├── Kế toán ↔ Back Office
└── Ngân hàng (thanh toán, chuyển tiền)

AGRIBANK (?)
└── Chưa chắc chắn mức độ tích hợp
```

---

## 4. Quan sát trên App Agribank

```
APP AGRIBANK
│
└── Shortcut "AgriSeco" (6-7 items)
    ├── Mở tài khoản
    ├── Nộp tiền
    ├── Đặt lệnh
    └── ...
    
    ⚠️ NHƯNG:
    └── Nhấn vào → MỞ TRANG AGRISECO → THOÁT KHỎI APP AGRIBANK
        (chưa được nhúng embedded)
```

**Nghĩa là:** Khách hàng dùng app Agribank, nhấn AgriSeco → bật ra ngoài → phải quay lại app Agribank sau. Chưa liền mạch.

---

## 5. Nhân sự CNTT

```
PHÒNG CNTT (~17 người)
│
├── NHÂN SỰ HIỆN TẠI
│   ├── Trưởng phòng (tuyển mới 2025)
│   ├── Phó phòng Hạ tầng/Vận hành
│   ├── Phó phòng Phát triển (vị trí mới)
│   ├── 1 BA
│   ├── 3 Developers
│   └── Còn lại: Hạ tầng, vận hành
│
├── ĐẶC ĐIỂM
│   ├── Chủ yếu là nhân sự VẬN HÀNH & HẠ TẦNG
│   ├── Nhân sự PHÁT TRIỂN rất MỎNG
│   ├── Chưa có nhân sự cứng về mảng phát triển
│   └── Đang trong quá trình xây dựng đội ngũ
│
└── PHỤ THUỘC VENDOR
    ├── Core (FLEX) → FSS
    ├── Mobile App (AgriSeco Pro) → FSS
    ├── Web trading → ?
    └── Chưa rõ đội in-house đã phát triển được gì
```

### Đánh giá

| Hạng mục | Hiện trạng | Rủi ro |
|----------|------------|--------|
| **Hạ tầng/Vận hành** | ✅ Đủ | Thấp |
| **Phát triển** | ⚠️ Rất mỏng (3 dev) | Cao |
| **BA** | ⚠️ Chỉ có 1 | Trung bình |
| **Phụ thuộc vendor** | ❌ Cao (Core, App, Web) | Rất cao |
| **In-house capability** | ❌ Chưa rõ ràng | Cao |

### Câu hỏi cần làm rõ

1. Đội in-house đã phát triển được những gì?
2. Lộ trình xây dựng đội phát triển như thế nào?
3. Có kế hoạch giảm phụ thuộc vendor không?
4. Budget cho tuyển dụng và đào tạo dev?

---

## 6. Tóm tắt hệ thống

| Cái gì | Có chưa | Vendor |
|--------|---------|--------|
| Core CK cơ sở | ✅ Flex | FSS |
| Mobile App | ✅ AgriSeco Pro | FSS |
| Web trading | ✅ | ? |
| Phái sinh | ❌ | - |
| Trái phiếu Agribank | ❌ không có trên app | - |
| Tích hợp Agribank sâu | ❌ chỉ redirect | - |

---

## 7. Cơ hội / Việc cần làm

```
❌ CHƯA CÓ                          → 🎯 CƠ HỘI
─────────────────────────────────────────────────
Phái sinh                           → Mở rộng sản phẩm
Trái phiếu Agribank không có        → Thêm vào app + cho GD
Tích hợp Agribank chưa sâu          → Deep integration
UX rời rạc Agribank ↔ AgriSeco     → Embedded trong app Agribank
```

---

## 8. Cần hỏi thêm

1. Flex đang version mấy? Có roadmap nâng cấp không?
2. Khi nào triển khai phái sinh?
3. Tích hợp API với Agribank đang ở mức nào?
4. Có kế hoạch làm SDK nhúng vào app Agribank không?
5. Website, eKYC dùng tech stack gì?

---

*Ghi chú: Thông tin từ quan sát bên ngoài + phỏng vấn. Cần verify với CNTT Agriseco.*
