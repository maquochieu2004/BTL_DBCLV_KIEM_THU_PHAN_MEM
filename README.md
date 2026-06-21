# Higher-order Bugs và Giới hạn của Kiểm thử

Dự án minh họa thực nghiệm cho tiểu luận môn **Hệ quản trị CSDL phân tán**.

## Mô tả

Hệ thống demo gồm 3 module độc lập (Đơn hàng, Thanh toán, Kho hàng) minh họa **Higher-order Bugs** — lỗi chỉ xuất hiện khi các module tích hợp với nhau, dù từng module pass kiểm thử đơn vị.

## 5 module giao diện web

| Module | Mô tả |
|--------|-------|
| **Dashboard** | Tổng quan hệ thống và kết quả kiểm thử |
| **Hệ thống Demo** | Mô phỏng luồng đặt hàng E2E |
| **Kiểm thử** | Chạy Unit / Integration / System / Performance test |
| **Kịch bản lỗi** | Mô tả các Higher-order Bug theo tiểu luận |
| **Báo cáo** | Lịch sử kiểm thử và trạng thái tồn kho |

## Cài đặt

```bash
cd e:\code_hieu
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
copy .env.example .env
```

## Chạy ứng dụng

```bash
python run.py
```

Mở trình duyệt: http://localhost:5000

## Chế độ demo

Trong file `.env`:

- `DEMO_MODE=fixed` — luồng tích hợp đúng (trừ kho sau thanh toán)
- `DEMO_MODE=buggy` — mô phỏng Higher-order Bug (thanh toán OK, kho không trừ)

## Chạy kiểm thử

```bash
# Tất cả test (chế độ fixed)
set DEMO_MODE=fixed
pytest

# Minh họa Higher-order Bug — integration test sẽ FAIL
set DEMO_MODE=buggy
pytest tests/integration/test_order_payment_inventory.py::test_inventory_sync_after_payment
```

## Cấu trúc dự án

```
app/
  modules/          # Order, Payment, Inventory, IntegratedFlow
  routes/           # 5 module web
  templates/        # Giao diện Bootstrap
tests/
  unit/             # Kiểm thử đơn vị
  integration/      # Kiểm thử tích hợp (phát hiện HOB)
  system/           # Kiểm thử hệ thống E2E
  performance/      # Kiểm thử hiệu năng / đồng thời
.github/workflows/  # CI/CD pipeline
```

## Liên hệ đề tài

- **Sinh viên:** Ma Quốc Hiếu, Tạ Phạm Đình Hòa
- **GVHD:** Ths. Nguyễn Thị Hương
- **Trường:** ĐHKTCN - Khoa Điện tử
