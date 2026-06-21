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

## Giao Diện

<img width="1902" height="981" alt="Screenshot 2026-06-22 015850" src="https://github.com/user-attachments/assets/7b5afe3e-fba9-4814-99ee-9f04c7c58bef" />

## Hệ thống Demo - Thương mại điện tử đa module

<img width="1919" height="843" alt="Screenshot 2026-06-22 015934" src="https://github.com/user-attachments/assets/e5c842d5-0976-4c00-91bb-33d8229de4c1" />

## Kiểm thử phần mềm

<img width="1908" height="991" alt="Screenshot 2026-06-22 020034" src="https://github.com/user-attachments/assets/6a6e5c84-a026-4f7c-866a-5029f45744b9" />

## Kịch bản Higher-order Bugs

<img width="1905" height="1020" alt="Screenshot 2026-06-22 020143" src="https://github.com/user-attachments/assets/6cb4e307-4f05-49ae-ac07-bbd68308e0a1" />

## Báo cáo kiểm thử

<img width="1905" height="999" alt="Screenshot 2026-06-22 020244" src="https://github.com/user-attachments/assets/567927a8-6218-484d-98b1-6ac8df7b3def" />


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

- **Sinh viên:** Ma Quốc Hiếu, 
- **GVHD:** Ths. Nguyên Tiến Linh
- **Trường:** ĐHKTCN - Khoa Điện tử
