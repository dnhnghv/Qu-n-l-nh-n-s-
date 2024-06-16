# Thông Tin về sinh viên.
- Họ tên :Đinh Nguyễn Hoàng Vũ
- Mã SV : K215480106133
- Lớp K57KMT
- Bài tập lớn môn học : Hệ quản trị cơ sở dữ liệu.

# Thông tin về bài toán
- Project csdl cho bài toán:Quản lý nhân sự trong bệnh viện.
- mô tả về bài toán:
Để quản lý nhân sự trong bệnh viện cần thiết kế cơ sở dữ liệu bao gồm các thông tin về nhân viên, phòng ban, công việc, bệnh nhân. lịch làm việc, đào tạo, đánh giá hiệu suất, lương bổng và các phúc lợi khác.
# Chức năng:
Bài toán quản lý nhân sự trong bệnh viện nhằm đảm bảo quản lý hiệu quả và tối ưu hóa nguồn nhân lực:
- Quản lý yhoong tin nhân viên: Thêm một nhân sự mới, sửa thông tin của nhân sự, xoá thông tin của một nhân viên,xem thông tin nhân viên bệnh viện bao gồm mã nhân viên, họ tên, ngày sinh, ngày vào làm, chức vụ, Khoa, và mức lương.
- Quản lý lịch làm việc: Lập lịch, chỉnh sửa, xóa và xem lịch làm việc của nhân viên, bao gồm ngày làm việc, giờ bắt đầu và giờ kết thúc ca làm.
- Quản lý thông tin về các khóa đào tạo mà nhân viên tham gia, bao gồm tên khóa, ngày đào tạo, và chứng chỉ đạt được.
- Quản lý các yêu cầu nghỉ phép, nghỉ bệnh, và phúc lợi của nhân viên.
# báo cáo:
- Báo cáo lương của nhân viên trong tháng.
- Cung cấp báo cáo chi tiết về tình trạng đào tạo của từng nhân viên.
- Báo cáo chi tiết về hiệu suất làm việc của từng nhân viên để hỗ trợ quyết định thăng tiến, khen thưởng, hoặc đào tạo lại.
- báo cáo về số lượng ngày nghỉ của nhân viên trong tháng và trong năm.
- báo cáo về tình hình vi phạm và kỷ luật của nhân viên.
- báo cáo về tình trạng sức khoẻ của nhân viên.
# các bảng của hệ thống: 
- với các mô tả chức năng và báo cáo như trên thì bài toán cần có các bảng sau:
  - Bảng NhanVien(MaNhanVien,HoTen,NgaySinh,NgayVaoLam,ChucVu,MaKhoa,MaPhongBan,Luong);
  - Bảng PhongBan(MaPhongBan,TenPhongBan,MoTa);
  - Bảng Khoa(MaKhoa,TenKhoa,MoTa);
  - Bảng LichLamViec(MaLich,MaNhanVien,NgayLamViec,GioBatDau,GioKetThuc);
  - Bảng DaoTao(MaDaoTao,MaNhanVien,TenKhoa,NgayDaoTao,ChungChi);
  - Bảng DanhGiaHieuSuat(MaDanhGia,MaNhanVien,NgayDanhGia,DiemDanhGia,GhiChu);
  - Bảng Luong(MaLuong,MaNhanVien,ThangNam,SoTien);
  - Bảng PhucLoi(MaPhucLoi,MaNhanVien,LoaiPhucLoi,NgayPhucLoi,GhiChu);
  - Bảng NghiPhep(MaNghiPhep,MaNhanVien,LoaiNghiPhep,NgayBatDau,NgayKetThuc,LyDo);
  - Bảng ViPhamKyLuat(MaViPham,MaNhanVien,NgayViPham,MoTaViPham,HinhThucKyLuat);





















