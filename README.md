# Uniace Website Traffic & User Behavior Analysis

Phân tích dữ liệu truy cập và hành vi người dùng trên website [uniace.vn](https://uniace.vn) trong giai đoạn **01/08/2021 – 24/08/2021**, nhằm đánh giá hiệu quả SEO/traffic, hiểu hành vi người dùng và đề xuất chiến lược nội dung, quảng cáo phù hợp.

Đây là project cá nhân trong khoá học Data Analyst.

## 1. Mục tiêu

- Cung cấp cái nhìn tổng quan về hiện trạng SEO của Uniace.
- Phân tích các yếu tố ảnh hưởng đến lượng truy cập và thứ hạng tìm kiếm.
- Tìm hiểu hành vi người dùng theo thời gian, theo loại nội dung.
- Đề xuất chiến lược cụ thể để cải thiện traffic và tỷ lệ chuyển đổi.

## 2. Dữ liệu

Dữ liệu là log tương tác thực tế của người dùng với website Uniace trong tháng 8/2021, được export thành 3 file Excel (`Uniace_1/2/3.xlsx`).

| Cột | Ý nghĩa |
|---|---|
| Email | Email (tài khoản) của user |
| Type | Loại tương tác (click vào nội dung nào) |
| Name / Title | Tên bài viết, tên chủ đề |
| MA URL | URL trang được truy cập |
| MA Referrer | Nguồn dẫn đến truy cập (quảng cáo, SEO, trực tiếp...) |
| ma_path | Path của website |
| IP Address | Địa chỉ IP người truy cập |
| cuid | Mã định danh người dùng duy nhất |
| Date | Thời gian diễn ra hành động |
| URL / Link / Tag | Thông tin liên kết, phân loại nội dung |

Data dictionary đầy đủ (kèm giải thích các case dữ liệu lỗi) nằm trong [Document.xlsx](Document.xlsx).

### Các vấn đề gặp phải với dữ liệu

- **Email null**: khách hàng không đăng nhập tài khoản.
- **MA URL null**: khách hàng đang thực thi tác vụ khác, có thể suy ra từ Tag.
- **MA Referrer blank**: user vào trực tiếp, không qua nguồn thứ ba.
- **Lệch cột**: một số dòng bị lệch vị trí, cột `IP Address` nằm ở cột `Date`, cột `Date` nằm ở cột `Template ID`, cột `cuid` bị nhầm với `Date`... cần fix lại đúng vị trí.

### Xử lý dữ liệu

1. Fix lại vị trí các cột bị lệch (`IP Address`, `cuid`, `Date`).
2. Chuẩn hoá cột `Date` (loại dữ liệu dạng text lẫn trong cột ngày giờ).
3. Dùng Python (pandas) gộp 3 file Excel gốc thành một dataset duy nhất — xem [Clean data/UniaceData.ipynb](Clean%20data/UniaceData.ipynb).
4. Trực quan hoá và phân tích trên Power BI.

## 3. Công cụ sử dụng

- **Python (pandas)**: gộp và làm sạch dữ liệu.
- **Excel**: kiểm tra, xử lý dữ liệu lỗi.
- **Power BI**: xây dựng dashboard phân tích traffic, thời gian, user, nội dung.

## 4. Kết quả phân tích chính

**Tổng quan**
- Tiếp cận **12,727 người dùng**, tổng **74,137 lượt truy cập** trong 24 ngày (1–24/8).
- Chỉ **2,217 người** đăng ký email (~1/6 số người tiếp cận) → cần tối ưu website để tăng độ tin tưởng, thúc đẩy đăng ký.
- Hơn **23,000 lượt Organic traffic** từ Google, Bing, Cốc Cốc,... cho thấy SEO khá tốt.
- Trong Top 10 bài viết được xem nhiều nhất, có **4 bài liên quan đến Excel** → khách hàng thường gặp khó khăn khi dùng Excel.
- Chương trình **Young Talent** đem lại hơn **13,000 lượt truy cập**, tiếp cận **3,108 khách hàng** trong tháng.

**Thời gian**
- Trung bình **~3,200 lượt truy cập/ngày**, tương đối ổn định.
- Đột biến traffic từ **11/8 – 14/8** (từ 1,467 lên 9,556 pageviews) nhờ chương trình **Young Talent Program**, đem lại **124 đơn hoàn thành**.
- Khung giờ truy cập nhiều nhất: **12h–13h** và **21h–23h** (giờ ăn trưa, ban đêm).
- Khung giờ ra đơn nhiều nhất: **9h–11h** và **21h–23h** → nên tập trung chạy quảng cáo vào 2 khung giờ này.

**User**
- Top user xem nhiều nhất **không trùng** với top user mua nhiều nhất; đa số người xem chỉ đọc bài viết free.
- Young Talent thu hút nhiều sinh viên từ các trường như UEF, UEH, UEL,... phần lớn thuộc khối kinh tế và ở TP.HCM → nên tổ chức thêm event offline tại TP.HCM để tăng tỷ lệ chuyển đổi.

**Content**
- Nội dung chia 2 nhóm **Dữ liệu** và **Kỹ năng**; nhóm Dữ liệu chiếm ~50% lượt truy cập (từ khóa nổi bật: "phân tích", "dữ liệu", "excel", "power bi", "database").
- Khóa học free về Phân tích dữ liệu và series TECH đóng góp nhiều nhất (~1,000 lượt truy cập).
- **Excel** là kỹ năng được truy cập nhiều nhất → nên phát triển thêm nội dung về Python, Cloud,...

## 5. Kết luận & đề xuất

- Traffic và organic search tương đối tốt, nhưng tỷ lệ đăng ký/chuyển đổi còn khiêm tốn → cần tối ưu UX/website để tăng độ tin tưởng.
- Đa dạng hoá nội dung ngoài Excel/Power BI, bổ sung Python, Cloud, Big Data.
- Tập trung chạy quảng cáo và đăng nội dung vào khung giờ trưa (9–11h) và tối (21–23h).
- Duy trì và mở rộng các chương trình như Young Talent Program, kết hợp tổ chức offline tại TP.HCM để tăng tỷ lệ chuyển đổi từ sinh viên.

## 6. Cấu trúc thư mục

```
├── Clean data/
│   └── UniaceData.ipynb      # Notebook gộp & làm sạch dữ liệu (Python/pandas)
├── Document.xlsx              # Data dictionary & giải thích các case dữ liệu lỗi
├── Uniace_Campaign.xlsx        # Dữ liệu/hình ảnh liên quan chiến dịch
├── UniaceAnalysis.docx         # Báo cáo phân tích đầy đủ
└── README.md
```

> **Lưu ý về dữ liệu:** Các file dữ liệu thô/đã làm sạch (`Raw data/`, `Clean data/*.xlsx`, `Clean data/finaldata.csv`) và file dashboard `Uniace.pbix` chứa email và địa chỉ IP thật của người dùng website nên **không được đưa lên repo public** (đã thêm vào `.gitignore`). Báo cáo chi tiết và kết quả phân tích xem tại [UniaceAnalysis.docx](UniaceAnalysis.docx).
