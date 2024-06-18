# Thông Tin về sinh viên.
- Họ tên: Đinh Nguyễn Hoàng Vũ
- Mã SV: K215480106133
- Lớp: K57KMT
- Bài tập lớn môn học: Hệ quản trị cơ sở dữ liệu.

# Thông tin về bài toán
- Project csdl cho bài toán:Quản lý nhân sự trong bệnh viện.
- mô tả về bài toán:
Để quản lý nhân sự trong bệnh viện cần thiết kế cơ sở dữ liệu bao gồm các thông tin về nhân viên, phòng ban, công việc. lịch làm việc, đào tạo, đánh giá hiệu suất, lương bổng và các phúc lợi khác.
# Chức năng:
Bài toán quản lý nhân sự trong bệnh viện nhằm đảm bảo quản lý hiệu quả và tối ưu hóa nguồn nhân lực:
- Quản lý thông tin nhân viên: Thêm một nhân sự mới, sửa thông tin của nhân sự, xoá thông tin của một nhân viên,xem thông tin nhân viên bệnh viện bao gồm mã nhân viên, họ tên, ngày sinh, ngày vào làm, chức vụ, Khoa, và mức lương.
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
- tạo database cho bài toán quản lý:
CREATE DATABASE QuanLyNhanSuBenhVien;
- với các mô tả chức năng và báo cáo như trên thì bài toán cần có các bảng sau:
  - Bảng NhanVien(MaNhanVien,HoTen,NgaySinh,NgayVaoLam,ChucVu,MaKhoa,MaPhongBan,Luong);
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/45f08868-ee4c-416c-968f-8b271d486d85)
    +  MaNhanVien, PK: Mã nhân viên duy nhất cho mỗi nhân viên, để tăng tự động cho Mã Nhân Viên;
    +  MaKhoa, FK: Khóa ngoại tham chiếu đến bảng Khoa, Đảm bảo rằng mỗi nhân viên được liên kết với một khoa hợp lệ.
    +  MaPhongBan, FK: Khóa ngoại tham chiếu đến bảng PhongBan, Đảm bảo rằng mỗi nhân viên được liên kết với một phòng ban hợp lệ.
    +  Các khóa ngoại trong bảng NhanVien đảm bảo rằng mỗi nhân viên được liên kết với một khoa và một phòng ban hợp lệ, duy trì tính toàn vẹn dữ liệu và hỗ trợ việc quản lý, truy vấn thông tin một cách hiệu quả.
    +   FOREIGN KEY (MaKhoa) REFERENCES Khoa(MaKhoa),Câu lệnh này xác định rằng trường MaKhoa trong bảng NhanVien là một khóa ngoại (Foreign Key).
Khóa ngoại MaKhoa tham chiếu đến trường MaKhoa của bảng Khoa.Điều này có nghĩa là giá trị của MaKhoa trong bảng NhanVien phải tồn tại trong trường MaKhoa của bảng Khoa.
Khóa ngoại đảm bảo tính toàn vẹn dữ liệu bằng cách không cho phép nhập giá trị vào MaKhoa trong bảng NhanVien nếu giá trị đó không tồn tại trong bảng Khoa.
    +   FOREIGN KEY (MaPhongBan) REFERENCES PhongBan(MaPhongBan), Câu lệnh này xác định rằng trường MaPhongBan trong bảng NhanVien là một khóa ngoại (Foreign Key).
Khóa ngoại MaPhongBan tham chiếu đến trường MaPhongBan của bảng PhongBan.Khóa ngoại đảm bảo tính toàn vẹn dữ liệu bằng cách không cho phép nhập giá trị vào MaPhongBan trong bảng NhanVien nếu giá trị đó không tồn tại trong bảng PhongBan.
    
  - Bảng PhongBan(MaPhongBan,TenPhongBan,MoTa);
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/89a72789-3412-400e-989d-1a779d7612ba)
    + mã phòng ban đặt là khoá chính vì mỗi phòng ban sẽ chỉ có một mã duy nhất, để tăng tự động cho Mã Phòng.
      
  - Bảng Khoa(MaKhoa,TenKhoa,MoTa);
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/9381d814-39fb-4d3b-85d4-0707f8e1ed57)
    + đặt Mã Khoa vì mỗi khoa chỉ có một mã làm khoá chính và được tăng tự động
      
  - Bảng LichLamViec(MaLich,MaNhanVien,NgayLamViec,GioBatDau,GioKetThuc);
    + Đảm bảo rằng giá trị trong trường MaNhanVien của bảng hiện tại phải tồn tại trong trường MaNhanVien của bảng NhanVien.
Ví dụ, nếu bảng hiện tại là LichLamViec, mỗi bản ghi trong bảng LichLamViec phải có MaNhanVien hợp lệ, tức là phải tham chiếu đến một nhân viên tồn tại trong bảng NhanVien.


  - Bảng DaoTao(MaDaoTao,MaNhanVien,TenKhoa,NgayDaoTao,ChungChi);
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/7ba628bb-c3a9-48d1-9a62-c8480369b2a5)
    + Đặt là khoá chính Mã đào tạo vì mỗi lần đào tạo sẽ chỉ có một mã duy nhất, để tăng tự động cho mã đào tạo.
    + Đảm bảo rằng trường MaNhanVien trong bảng DaoTao tham chiếu đến trường MaNhanVien trong bảng NhanVien,Đảm bảo rằng mỗi khóa đào tạo được ghi nhận trong bảng DaoTao là của một nhân viên hợp lệ, tức là một nhân viên có tồn tại trong bảng NhanVien
      
  - Bảng DanhGiaHieuSuat(MaDanhGia,MaNhanVien,NgayDanhGia,DiemDanhGia,GhiChu);
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/40b042ce-146c-4423-b4ba-90b79fdd484b)
mã đánh giá Là khóa chính (Primary Key) của bảng HieuSuat, đảm bảo mỗi bản ghi trong bảng này là duy nhất.
Câu lệnh FOREIGN KEY (MaNhanVien) REFERENCES NhanVien(MaNhanVien) trong bảng HieuSuat đảm bảo rằng mỗi bản ghi hiệu suất liên kết với một nhân viên hợp lệ trong bảng NhanVien, duy trì tính toàn vẹn dữ liệu và hỗ trợ các truy vấn phức tạp liên quan đến đánh giá hiệu suất của nhân viên.

  - Bảng Luong(MaLuong,MaNhanVien,ThangNam,SoTien);
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/75df9cf0-b86f-406e-b150-9b4d9c3186af)

    + Tạo mối quan hệ giữa bảng Luong và NhanVien:

Khóa ngoại đảm bảo rằng mỗi bản ghi lương phải liên kết với một nhân viên cụ thể trong bảng NhanVien.
Đảm bảo rằng không thể nhập một MaNhanVien vào bảng Luong nếu mã nhân viên đó không tồn tại trong bảng NhanVien.
giúp thực hiện các truy vấn kết hợp dữ liệu từ cả hai bảng để tạo báo cáo chi tiết về lương của nhân viên.
  - Bảng PhucLoi(MaPhucLoi,MaNhanVien,LoaiPhucLoi,NgayPhucLoi,GhiChu);
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/37589023-568d-482f-b77c-2df698f9a05e)
    + Khóa ngoại đảm bảo rằng giá trị của cột MaNhanVien trong bảng Phúc Lợi phải tồn tại trong cột MaNhanVien của bảng Nhân Viên. Điều này đảm bảo rằng mỗi phúc lợi phải được gán cho một nhân viên hợp lệ trong bảng Nhân Viên.
Khóa ngoại tạo mối quan hệ giữa bảng Phúc Lợi và bảng Nhân Viên. Nó giúp kết nối thông tin về phúc lợi với thông tin về nhân viên nhận phúc lợi đó.
Với ràng buộc khóa ngoại, khi bạn thực hiện các thao tác như JOIN giữa bảng Phúc Lợi và bảng Nhân Viên, bạn có thể dễ dàng lấy thông tin liên quan từ cả hai bảng dựa trên mối quan hệ giữa chúng.
Khi thêm hoặc cập nhật dữ liệu trong bảng Phúc Lợi, ràng buộc khóa ngoại sẽ kiểm tra xem MaNhanVien có tồn tại trong bảng Nhân Viên hay không. Nếu không, thao tác sẽ bị từ chối, ngăn chặn việc nhập dữ liệu không hợp lệ.

  - Bảng NghiPhep(MaNghiPhep,MaNhanVien,LoaiNghiPhep,NgayBatDau,NgayKetThuc,LyDo);

    
  - Bảng ViPhamKyLuat(MaViPham,MaNhanVien,NgayViPham,MoTaViPham,HinhThucKyLuat);
  ## sau đây là cụ thể về các bảng cũng như sự liên kết giữa các bảng với nhau:
  





















