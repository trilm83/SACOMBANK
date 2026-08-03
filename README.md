# 🏦 Đồ án Phân tích và Cải tiến Quy trình Quản lý Yêu cầu Dịch vụ (PYC) tại Sacombank

[![BPMN 2.0](https://img.shields.io/badge/BPMN-2.0-blue.svg)](#)
[![Camunda](https://img.shields.io/badge/Tool-Camunda-orange.svg)](#)
[![Lean Management](https://img.shields.io/badge/Methodology-Lean_Management-green.svg)](#)

## 📖 Giới thiệu Dự án
Khối Công nghệ thông tin (IT Division) của Sacombank hoạt động như một tổ chức cung cấp dịch vụ độc lập, phục vụ khách hàng nội bộ là các cán bộ nhân viên và phòng ban. 
Dự án này tập trung phân tích và tối ưu hóa **Quy trình Quản lý Yêu cầu Dịch vụ (Service Request - PYC)** nhằm giảm thiểu thời gian chờ (Lead time), nâng cao chất lượng dịch vụ nội bộ và đẩy mạnh quá trình chuyển đổi số.

## 🏗 Kiến trúc Quy trình CNTT
Các quy trình của Khối IT được chia thành 3 nhóm chính:
1. **Nhóm Quản lý (Management Processes):** Quản lý mức dịch vụ (SLA), Rủi ro & An toàn thông tin, Lập kế hoạch ngân sách.
2. **Nhóm Cốt lõi (Core Processes):** **Quản lý Yêu cầu Dịch vụ (PYC)**, Quản lý sự cố, Quản lý phát hành.
3. **Nhóm Hỗ trợ (Support Processes):** Quản lý vấn đề, Quản lý thay đổi, Quản lý tài sản CNTT, Quản lý tri thức.

## 🔍 Phương pháp Nghiên cứu
Dự án sử dụng phương pháp phỏng vấn chuyên sâu với 20 câu hỏi chia làm 2 khía cạnh:
- **Định tính:** Khai thác trải nghiệm người dùng, cảm nhận, cách phối hợp và điểm nghẽn trong phân luồng PYC.
- **Định lượng:** Đo lường các chỉ số thời gian (Lead time), tỷ lệ trễ hạn SLA, số bước luân chuyển (ping-pong) và số giờ làm việc thực tế bị lãng phí.

## ⚠️ Phân tích Hiện trạng (AS-IS) & Các Loại Lãng Phí
Dựa trên mô hình hóa BPMN 2.0 (sử dụng Camunda) và phân tích luồng giá trị (VA/NVA/VBA), 3 loại lãng phí (Waste) chính đã được nhận diện theo tư duy Lean:
- **Move (Di chuyển/Chuyển giao):** Lãng phí thời gian luân chuyển phiếu qua nhiều "làn", đặc biệt là hiện tượng "ping-pong" khi phải trả về để người dùng bổ sung thông tin.
- **Hold (Chờ đợi):** Nút thắt cổ chai (bottleneck) tại bước phê duyệt của Quản lý trực tiếp và sự chậm trễ tại cổng gom luồng do tác vụ Ghi log bảo mật thực hiện thủ công.
- **Overdo (Xử lý quá mức):** Bắt buộc đi qua cổng phê duyệt cho mọi loại PYC, kể cả những quyền cơ bản (rủi ro thấp), gây dư thừa thủ tục hành chính.

## 🚀 Đề xuất Cải tiến (Mô hình TO-BE)
Để khắc phục các điểm nghẽn và tối ưu hóa nguồn lực, dự án đề xuất 3 giải pháp trọng tâm:
1. **Chuẩn hóa Biểu mẫu (Smart-Form):** Thiết lập các trường thông tin bắt buộc dưới dạng Dropdown list. Đảm bảo nguyên tắc "Right First Time" (Đúng ngay lần đầu) để triệt tiêu hoàn toàn vòng lặp bổ sung thông tin (NVA).
2. **Ma trận Phê duyệt Tự động (Auto Approval):** Phân loại danh mục dịch vụ theo mức độ rủi ro. Tự động bypass bước phê duyệt của Trưởng/Phó đơn vị đối với các yêu cầu rủi ro thấp (VD: Wifi, Folder chung, Reset Password) đẩy thẳng tới Làn IT xử lý.
3. **Tự động hóa Ghi log bằng API:** Tích hợp API giữa hệ thống cấp quyền và hệ thống quản lý log tập trung (SIEM). Tự động kích hoạt (trigger) việc ghi log bảo mật ngay khi cấp quyền xong, loại bỏ thời gian chờ đồng bộ giữa 2 tác vụ song song.

## 🎯 Kết luận
Mô hình TO-BE hứa hẹn rút ngắn đáng kể thời gian chờ đợi, loại bỏ các tác vụ dư thừa không mang lại giá trị gia tăng (NVA), và giải phóng thời gian cho cấp quản lý (VBA). Cải tiến này không chỉ nâng cao tỷ lệ hài lòng (CSAT) của người dùng nội bộ mà còn đóng góp trực tiếp vào chiến lược Chuyển đổi số toàn diện của Khối CNTT Sacombank.

---
**Tác giả:** Lê Minh Trí 
*Khối Công nghệ thông tin - Vận hành Kỹ thuật, Sacombank*
