cd e:\code_hieu
dòng cài đặt

pip install -r requirements.txt

dòng chạy:

python run.py


chế độ demo
# Chạy toàn bộ test
python -m pytest

# Minh họa bug — test này sẽ FAIL ở chế độ buggy
set DEMO_MODE=buggy
python -m pytest tests/integration/test_order_payment_inventory.py::test_inventory_sync_after_payment
