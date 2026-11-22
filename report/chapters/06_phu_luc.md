# PHỤ LỤC {.unnumbered}

## Phụ lục A. Từ điển dữ liệu {.unnumbered}

Xem tệp `docs/tu_dien_du_lieu.md` trong repository (được chèn tự động khi dựng báo cáo).

## Phụ lục B. Nhật ký làm sạch dữ liệu {.unnumbered}

Xem tệp `docs/nhat_ky_lam_sach.md` (được chèn tự động khi dựng báo cáo).

## Phụ lục C. Mã nguồn {.unnumbered}

Toàn bộ dữ liệu, mã nguồn, hình và bảng của báo cáo được lưu trong repository GitHub của nhóm:
<https://github.com/khoaminh2957/XSTK> (nhánh `main`). Mọi notebook đọc cùng tệp `data/processed/cleaned_cars.csv` v1.0
(6.693 dòng × 22 cột) và dùng chung quy ước $\alpha = 0{,}05$, `random_state = 42`, giá tính bằng INR.

: Bảng C.1. Danh sách mã nguồn

| Tệp | Người phụ trách | Nội dung | Kết quả trong báo cáo |
|---|---|---|---|
| `notebooks/01_cleaning.ipynb` | Khoa (TV1) | Tiền xử lý: xoá trùng lặp, tách đơn vị, xử lý giá trị khuyết, mức hiếm và giá trị vô lý; xuất `cleaned_cars.csv` v1.0 | Chương 2 (mục 2.7), Hình 2.1 – 2.4 |
| `notebooks/02_eda.ipynb` | Uyên (TV2) | Thống kê mô tả, biểu đồ phân phối và tương quan, khoảng tin cậy 95% | Mục 3.1 |
| `notebooks/03_hypothesis.ipynb` | Sang (TV3) | Kiểm tra giả định; Welch t-test, Welch ANOVA + Games-Howell, Kruskal-Wallis + Dunn (Holm), Spearman, Chi-bình phương; hệ số ảnh hưởng, hiệu chỉnh Holm | Mục 3.2, Hình 3.7 – 3.11, Bảng 3.5 – 3.12 |
| `notebooks/04_regression.ipynb` | Nguyên (TV4) | Hồi quy tuyến tính bội trên `log_price`, stepwise AIC/BIC, VIF, chẩn đoán phần dư, đánh giá trên tập test | Mục 3.3, Chương 4 |
| `kiem_thu_quy_trinh.py` | Khoa (TV1) | Kiểm thử độc lập toàn bộ quy trình làm sạch (PASS / WARN / FAIL) | Mục 2.7 |
| `report/build_report.py` | Khoa (TV1) | Dựng báo cáo Word từ các chương Markdown | Toàn bộ báo cáo |

*Nguồn: Nhóm nghiên cứu.*

**Cách chạy lại kết quả.**

```bash
pip install -r requirements.txt
python kiem_thu_quy_trinh.py                     # kiểm thử dữ liệu: không có dòng FAIL
jupyter nbconvert --to notebook --execute --inplace notebooks/03_hypothesis.ipynb   # tương tự cho 01, 02, 04
python report/build_report.py                    # dựng report/output/BaoCao_XSTK.docx
```

Trên Kaggle: thêm `cleaned_cars.csv` làm *Input*, *File → Import Notebook* rồi *Restart & Run All*; các notebook tự nhận
đường dẫn `/kaggle/input` và ghi hình vào `/kaggle/working/figures`.
