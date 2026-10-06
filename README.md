# Spec_wri — Digital IC Specification Notebook

Repo này là **sổ tay học cách xây dựng specification cho Digital IC / RTL IP** và đồng thời là một **AI reference pack tái sử dụng**.

Mục tiêu: khi có một bài toán mới (Counter, FIFO, GPIO, UART, SPI, DMA, ...), không yêu cầu AI “tự nghĩ một spec chuyên nghiệp”, mà buộc AI làm việc theo **nguồn yêu cầu + chuẩn tham chiếu + spec mẫu + TBD/traceability**.

---

## Cách dùng nhanh với một chat AI mới

Mỗi lần cần xây spec cho một bài toán mới:

1. Đính kèm `AI_PACK/01_STANDARD_PROFILE.md`
2. Đính kèm `AI_PACK/02_REFERENCE_SPEC_PROFILE.md`
3. Đưa **đề bài / requirement / datasheet / notes** của project
4. Copy prompt trong `PROMPTS/01_BUILD_SPEC.md`
5. Sau khi có spec, mở một chat khác và dùng `PROMPTS/02_REVIEW_SPEC.md`

> Hai file trong `AI_PACK/` là bộ đính kèm cố định. **Đề bài của project luôn có độ ưu tiên cao nhất.**

---

## Cấu trúc repo

```text
Spec_wri/
├── README.md
│
├── AI_PACK/
│   ├── 01_STANDARD_PROFILE.md
│   └── 02_REFERENCE_SPEC_PROFILE.md
│
├── PROMPTS/
│   ├── 01_BUILD_SPEC.md
│   └── 02_REVIEW_SPEC.md
│
├── TEMPLATES/
│   └── DIGITAL_IP_SPEC_TEMPLATE.md
│
├── CHECKLISTS/
│   └── SPEC_READY_FOR_RTL_DV.md
│
└── NOTES/
    ├── 00_LEARNING_ROADMAP.md
    ├── 01_CORE_IDEAS.md
    ├── 02_REQUIREMENT_WRITING.md
    └── NOTE_TEMPLATE.md
```

---

## Nguồn tham chiếu chính

### 1. ECSS-E-ST-20-40C (2023)

**ASIC, FPGA and IP Core engineering** — chuẩn ECSS dành trực tiếp cho ASIC, FPGA và IP Core.

Trang chính thức:  
https://ecss.nl/standard/ecss-e-st-20-40c-asic-fpga-and-ip-core-engineering-11-october-2023/

Phần đặc biệt hữu ích: **DEVICE Requirements Specification (DRS)** / Annex A.

### 2. ISO/IEC/IEEE 29148:2018

**Requirements engineering** — dùng để học discipline khi tạo, quản lý và đánh giá requirement.

Trang chính thức:  
https://www.iso.org/standard/72089.html

### 3. OpenTitan HWIP Technical Specifications

Spec Digital IP công khai, có cấu trúc đủ chi tiết để học cách trình bày.

UART:  
https://opentitan.org/book/hw/ip/uart/

GPIO:  
https://opentitan.org/book/hw/top_earlgrey/ip_autogen/gpio/

### 4. NASA/JPL ASIC Design Guidelines

Nguồn tham khảo thực tế về ASIC technical specification.

https://parts.jpl.nasa.gov/asic/Sect.3.1.html

---

## Nguyên tắc trung tâm của repo

```text
SOURCE REQUIREMENTS
        ↓
Requirement extraction
        ↓
Ambiguity / TBD / conflicts
        ↓
Specification
        ↓
Independent review
        ↓
Traceability + readiness check
        ↓
RTL / DV handoff
```

Sơ đồ trên là **workflow học tập/tổng hợp của repo**, không được tuyên bố là sơ đồ nguyên văn của một standard.

---

## Quy tắc chống AI “bịa spec”

- Không có nguồn → **TBD**, không tự điền.
- Mọi giả định → ghi **ASSUMPTION**.
- Mọi requirement suy ra → ghi **DERIVED**.
- Requirement từ đề bài → ghi **SOURCE**.
- Không copy width, reset, timing, register address, FIFO depth... từ spec mẫu.
- Spec mẫu chỉ giúp học **structure, granularity và cách diễn đạt**.
- Không tuyên bố READY FOR RTL/DV nếu còn TBD làm thay đổi observable hardware behavior.
- Requirement quan trọng phải trace được tới source và verification target.

---

## Definition of Done ngắn gọn

Một Digital IP spec được xem là đủ để handoff khi:

> Một RTL designer có thể implement và một DV engineer có thể viết testcase/assertion mà **không phải tự đoán các hành vi phần cứng quan trọng**.

Chi tiết xem: `CHECKLISTS/SPEC_READY_FOR_RTL_DV.md`.

---

## Ghi chú bản quyền

Repo này **không sao chép toàn văn các standard**. Các file AI pack chỉ tóm tắt workflow/checklist để học và trỏ về nguồn chính thức. Khi compliance thực sự cần thiết, phải đọc bản standard gốc áp dụng cho project.
