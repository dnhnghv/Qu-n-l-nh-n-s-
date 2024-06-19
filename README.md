# Thông Tin về sinh viên.
- Họ tên: Đinh Nguyễn Hoàng Vũ
- Mã SV: K215480106133
- Lớp: K57KMT
- Bài tập lớn môn học: Hệ quản trị cơ sở dữ liệu.

# Thông tin về bài toán
- Project csdl cho bài toán:Quản lý nhân sự trong bệnh viện.
- mô tả về bài toán:
+ Tạo cơ sở dữ liệu và các bảng.
+ Thêm các ràng buộc kiểm tra (CHECK constraints).
+ Tạo các thủ tục lưu trữ (Stored Procedures).
+ Thêm, sửa, xóa và xem thông tin nhân viên,Lịch làm việc,Đào tạo,Nghỉ phép và phúc lợi.
+ Báo cáo: Tạo các báo cáo về lương, đào tạo, hiệu suất, nghỉ phép, vi phạm kỷ luật và sức khỏe của nhân viên.
+ Tạo các hàm (Functions):Tính tuổi của nhân viên dựa trên ngày sinh, tính tổng lương của nhân viên trong tháng, tính số ngày nghỉ của nhân viên trong tháng.

# Chức năng:
Bài toán quản lý nhân sự trong bệnh viện nhằm đảm bảo quản lý hiệu quả và tối ưu hóa nguồn nhân lực:
- Quản lý thông tin nhân viên: Thêm một nhân sự mới, sửa thông tin của nhân sự, xoá thông tin của một nhân viên,xem thông tin nhân viên bệnh viện bao gồm mã nhân viên, họ tên, ngày sinh, ngày vào làm, chức vụ, Khoa, và mức lương.
- Quản lý lịch làm việc: Lập lịch, chỉnh sửa, xóa và xem lịch làm việc của nhân viên, bao gồm ngày làm việc, giờ bắt đầu và giờ kết thúc ca làm.
- Quản lý thông tin về các khóa đào tạo mà nhân viên tham gia, bao gồm tên khóa, ngày đào tạo, và chứng chỉ đạt được.
- Quản lý các yêu cầu nghỉ phép, nghỉ bệnh, và phúc lợi của nhân viên.
# Báo cáo:
- Báo cáo lương của nhân viên trong tháng.
- Cung cấp báo cáo chi tiết về tình trạng đào tạo của từng nhân viên.
- Báo cáo chi tiết về hiệu suất làm việc của từng nhân viên để hỗ trợ quyết định thăng tiến, khen thưởng, hoặc đào tạo lại.
- báo cáo về số lượng ngày nghỉ của nhân viên trong tháng và trong năm.
- báo cáo về tình hình vi phạm và kỷ luật của nhân viên.
- báo cáo về tình trạng sức khoẻ của nhân viên.
# Các bảng của hệ thống: 
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
    + dữ liệu được nhập cho bảng:
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/30c1809c-9d22-4804-a631-9eedd276fcbf)

  - Bảng PhongBan(MaPhongBan,TenPhongBan,MoTa);
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/89a72789-3412-400e-989d-1a779d7612ba)
    + mã phòng ban đặt là khoá chính vì mỗi phòng ban sẽ chỉ có một mã duy nhất, để tăng tự động cho Mã Phòng.
    + dữ liệu được nhập cho bảng:
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/fc44480f-8b81-4c04-be7f-d6a713677cfd)

      
  - Bảng Khoa(MaKhoa,TenKhoa,MoTa);
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/9381d814-39fb-4d3b-85d4-0707f8e1ed57)
    + đặt Mã Khoa vì mỗi khoa chỉ có một mã làm khoá chính và được tăng tự động
    + dữ liệu được nhập cho bảng:
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/e3b50cc1-1f0a-4883-88ff-9a032b132f9c)

  - Bảng LichLamViec(MaLich,MaNhanVien,NgayLamViec,GioBatDau,GioKetThuc);
    + Đảm bảo rằng giá trị trong trường MaNhanVien của bảng hiện tại phải tồn tại trong trường MaNhanVien của bảng NhanVien.
Ví dụ, nếu bảng hiện tại là LichLamViec, mỗi bản ghi trong bảng LichLamViec phải có MaNhanVien hợp lệ, tức là phải tham chiếu đến một nhân viên tồn tại trong bảng NhanVien.
      + dữ liệu được nhập cho bảng:
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/5ecb4235-2e56-4262-94d5-10f526bc4bb9)

  - Bảng DaoTao(MaDaoTao,MaNhanVien,TenKhoa,NgayDaoTao,ChungChi);
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/7ba628bb-c3a9-48d1-9a62-c8480369b2a5)
    + Đặt là khoá chính Mã đào tạo vì mỗi lần đào tạo sẽ chỉ có một mã duy nhất, để tăng tự động cho mã đào tạo.
    + Đảm bảo rằng trường MaNhanVien trong bảng DaoTao tham chiếu đến trường MaNhanVien trong bảng NhanVien,Đảm bảo rằng mỗi khóa đào tạo được ghi nhận trong bảng DaoTao là của một nhân viên hợp lệ, tức là một nhân viên có tồn tại trong bảng NhanVien
    + dữ liệu được nhập cho bảng:
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/2d1704ee-8f50-46fb-8e02-fb5bb1f9079e)

  - Bảng DanhGiaHieuSuat(MaDanhGia,MaNhanVien,NgayDanhGia,DiemDanhGia,GhiChu);
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/40b042ce-146c-4423-b4ba-90b79fdd484b)
mã đánh giá Là khóa chính (Primary Key) của bảng HieuSuat, đảm bảo mỗi bản ghi trong bảng này là duy nhất.
Câu lệnh FOREIGN KEY (MaNhanVien) REFERENCES NhanVien(MaNhanVien) trong bảng HieuSuat đảm bảo rằng mỗi bản ghi hiệu suất liên kết với một nhân viên hợp lệ trong bảng NhanVien, duy trì tính toàn vẹn dữ liệu và hỗ trợ các truy vấn phức tạp liên quan đến đánh giá hiệu suất của nhân viên.
    + dữ liệu được nhập cho bảng:
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/71933be2-b10e-4142-9a6c-beac7d56e241)

  - Bảng Luong(MaLuong,MaNhanVien,ThangNam,SoTien);
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/75df9cf0-b86f-406e-b150-9b4d9c3186af)

    + Tạo mối quan hệ giữa bảng Luong và NhanVien:
Khóa ngoại đảm bảo rằng mỗi bản ghi lương phải liên kết với một nhân viên cụ thể trong bảng NhanVien.
Đảm bảo rằng không thể nhập một MaNhanVien vào bảng Luong nếu mã nhân viên đó không tồn tại trong bảng NhanVien.
giúp thực hiện các truy vấn kết hợp dữ liệu từ cả hai bảng để tạo báo cáo chi tiết về lương của nhân viên.
    + dữ liệu được nhập cho bảng:
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/393fb401-2e42-46a2-bced-fac105d6f7f2)

  - Bảng PhucLoi(MaPhucLoi,MaNhanVien,LoaiPhucLoi,NgayPhucLoi,GhiChu);
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/37589023-568d-482f-b77c-2df698f9a05e)
    + Khóa ngoại đảm bảo rằng giá trị của cột MaNhanVien trong bảng Phúc Lợi phải tồn tại trong cột MaNhanVien của bảng Nhân Viên. Điều này đảm bảo rằng mỗi phúc lợi phải được gán cho một nhân viên hợp lệ trong bảng Nhân Viên.
Khóa ngoại tạo mối quan hệ giữa bảng Phúc Lợi và bảng Nhân Viên. Nó giúp kết nối thông tin về phúc lợi với thông tin về nhân viên nhận phúc lợi đó.
Với ràng buộc khóa ngoại, khi bạn thực hiện các thao tác như JOIN giữa bảng Phúc Lợi và bảng Nhân Viên, bạn có thể dễ dàng lấy thông tin liên quan từ cả hai bảng dựa trên mối quan hệ giữa chúng.
Khi thêm hoặc cập nhật dữ liệu trong bảng Phúc Lợi, ràng buộc khóa ngoại sẽ kiểm tra xem MaNhanVien có tồn tại trong bảng Nhân Viên hay không. Nếu không, thao tác sẽ bị từ chối, ngăn chặn việc nhập dữ liệu không hợp lệ.
      + dữ liệu được nhập cho bảng:
        ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/66a8a0cc-76fe-4e0d-abcd-0bb3f938440a)

  - Bảng NghiPhep(MaNghiPhep,MaNhanVien,LoaiNghiPhep,NgayBatDau,NgayKetThuc,LyDo);
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/c2dc0003-48e3-4e05-b4f2-72a383bffa78)

    + khoá chính mã nghỉ phép nghĩa là mỗi giá trị trong cột này là duy nhất và không trùng lặp. Điều này giúp xác định duy nhất mỗi kỳ nghỉ phép trong bảng.
    + Khóa ngoại này đảm bảo rằng giá trị của cột MaNhanVien trong bảng Nghỉ Phép phải tồn tại trong cột MaNhanVien của bảng Nhân Viên. Điều này ngăn chặn việc nhập dữ liệu không hợp lệ, chẳng hạn như gán một kỳ nghỉ phép cho một nhân viên không tồn tại.
Khóa ngoại này tạo mối quan hệ giữa bảng Nghỉ Phép và bảng Nhân Viên. Điều này giúp liên kết thông tin về kỳ nghỉ phép với nhân viên cụ thể trong bảng Nhân Viên.
Khi thực hiện các thao tác truy vấn dữ liệu, chẳng hạn như JOIN, ràng buộc khóa ngoại này giúp dễ dàng lấy thông tin liên quan từ cả bảng Nghỉ Phép và bảng Nhân Viên dựa trên mối quan hệ giữa chúng.
Khi thêm hoặc cập nhật dữ liệu trong bảng Nghỉ Phép, ràng buộc khóa ngoại sẽ kiểm tra xem giá trị MaNhanVien có tồn tại trong bảng Nhân Viên hay không. Nếu không tồn tại, thao tác sẽ bị từ chối, ngăn chặn việc nhập dữ liệu không hợp lệ.
      + dữ liệu được nhập cho bảng:
        ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/ba3822fc-d205-4cee-a98f-ae4241cf6ac4)

  - Bảng ViPhamKyLuat(MaViPham,MaNhanVien,NgayViPham,MoTaViPham,HinhThucKyLuat);
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/a4047a52-1117-49dc-8489-46b87d8d84b2)

    + Khóa ngoại đảm bảo rằng giá trị của cột MaNhanVien trong bảng Vi Phạm Kỷ Luật phải tồn tại trong cột MaNhanVien của bảng Nhân Viên. Điều này ngăn chặn việc nhập dữ liệu vi phạm kỷ luật cho một nhân viên không tồn tại.
Khóa ngoại tạo mối quan hệ giữa bảng Vi Phạm Kỷ Luật và bảng Nhân Viên. Nó giúp kết nối thông tin về vi phạm kỷ luật với thông tin về nhân viên vi phạm đó.
Khi thực hiện các thao tác truy vấn dữ liệu, chẳng hạn như JOIN, ràng buộc khóa ngoại này giúp dễ dàng lấy thông tin liên quan từ cả bảng Vi Phạm Kỷ Luật và bảng Nhân Viên dựa trên mối quan hệ giữa chúng.
Khi thêm hoặc cập nhật dữ liệu trong bảng Vi Phạm Kỷ Luật, ràng buộc khóa ngoại sẽ kiểm tra xem giá trị MaNhanVien có tồn tại trong bảng Nhân Viên hay không. Nếu không tồn tại, thao tác sẽ bị từ chối, ngăn chặn việc nhập dữ liệu không hợp lệ.
      + dữ liệu được nhập cho bảng:
        ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/aa59fee3-a44a-47c5-a134-42bee99130f6)
        chú ý là ngày vi phạm không được xảy ra ở tương lai.
   + tạo bảng sức khoẻ
     ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/5fe7f93d-35c0-409d-9c2a-63e92ba61402)
    + dữ liệu được nhập cho bảng:
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/edf3b44a-1d1c-4b87-8bd6-2dfb2e57dc67)

  ##thêm các rằng buộc CK cho bài toán:
    - Điểm đánh giá hiệu suất sẽ nằm trong khoảng từ 1 đến 10.
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/ea28c32e-5775-400d-9906-e1cfec9ea625)

    - số tiền lương phải lớn hơn 0.
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/5c8410cf-3ea6-44bc-b331-e8e266295288)

    - NgayBatDau DATE: Ngày bắt đầu nghỉ phép phải trước ngày kết thúc. NgayKetThuc DATE: Ngày kết thúc nghỉ phép phải sau ngày bắt đầu.
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/8153fdd2-29c6-41d5-94bd-a59a72729555)

    -  Ngày vi phạm không thể trong tương lai.
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/5e86a118-516d-4f48-83f9-55e447456c2e)

    
     # Tạo SP cho bài.
- Thêm một nhân sự mới.
    ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/8a46d6e7-63c5-4359-baf6-6d2371f4fb5f)
+ cách sử dụng:
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/f2e9da11-9ebc-4c72-b7b0-1963e76865ef)
+ kết quả:
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/46fc8131-59a4-416a-aa09-da7f2824b458)

- Sửa thông tin của nhân sự.
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/3e3e8535-f7f4-4f78-830a-856f49f57f37)
+ cách sử dụng:
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/30b6d27d-3683-438d-8616-304c92cb3834)

- Xoá thông tin của một nhân viên
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/fcb6ebdc-0212-4029-baaf-133d6b3d2173)
   kết quả:
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/b1d0faf8-9225-40bb-ae95-6943b7f83070)

- Xem thông tin nhân viên bệnh viện.
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/1b34af3c-bb59-4e65-b396-024286edc32f)
   kết quả:
- Thêm một lịch làm việc mới cho nhân viên vào bảng.
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/93f22a5d-7943-48cd-bd56-33e1835d92f6)
   kết quả:
- chỉnh sửa lịch làm việc.
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/cdd44f3b-16d9-41f3-81a5-ae57cdf114b7)
   kết quả:
- Xoá lịch làm việc.
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/a7e690ee-7511-47f3-ae49-1a3dd6136297)
   kết quả:
- Xem lịch làm việc của nhân viên.
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/dccfc117-8747-4aa0-9e15-5b14fc5502e8)
   kết quả:
- Thêm thông tin khóa đào tạo.
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/b60b56b3-fe34-46b4-bede-2eb8d8822d66)
  kết quả:
- Sửa thông tin khóa đào tạo.
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/8be89964-f189-4ebb-bcd9-0cfd22e1df22)
  kết quả:
- Xoá thông tin khóa đào tạo.
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/70c4b04e-bf0e-4fe5-bcf8-1f91b9f84bb1)
  kết quả:
- Xem thông tin khóa đào tạo của nhân viên.
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/5b220dba-9c17-44a4-bc5d-bdb5d445e9aa)
  kết quả:
- Thêm yêu cầu nghỉ phép, nghỉ bệnh, phúc lợi.
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/2a3d0b06-53df-4032-9d0b-49c967eaaed7)
  kết quả:
- xoá yêu cầu nghỉ phép, nghỉ bệnh, phúc lợi.
      ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/eb990bf6-e71a-4b22-a07a-4a74b0bc2145)
  kết quả:
- xem yêu cầu nghỉ phép, nghỉ bệnh, phúc lợi.
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/1d53d19a-7aff-4806-8d6d-c3a7477b82ce)
  kết quả:
- Báo cáo lương của nhân viên trong tháng.
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/fc363835-c980-48c3-9e47-b47354db9db2)
+ kết quả:
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/6b6c89e4-05f2-4e67-90d4-556dec9b3339)

- Báo cáo chi tiết về tình trạng đào tạo của từng nhân viên
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/b5432098-200c-4d94-bd58-7006eeec9917)
  + kết quả:
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/e9466f96-fb34-4351-9dfc-65c7b4e3f4ba)

- báo cáo đánh giá hiệu suất của nhân viên
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/b810ac38-5639-4af7-9cfd-f788120654b4)
+ kết quả:
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/ff160f71-1e31-4ca2-bbe8-662cfe3747ae)

- Báo cáo về số lượng ngày nghỉ của nhân viên trong tháng và trong năm
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/18248638-8eaf-462c-8808-ed49c61924a5)
- kết quả: 
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/b859f501-3edc-4891-9c9c-91070e3c804e)
  
- Báo cáo về tình hình vi phạm và kỷ luật của nhân viên
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/2092a645-036d-4112-b0a3-7b7e47698d2f)
  kết quả:
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/b0395a98-813f-428d-b4c7-3c839fbfd8f6)

- Báo cáo về tình trạng sức khỏe của nhân viên
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/96dbf9f3-3be9-4f25-903f-21a18cf230f0)
kết quả:
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/163176d9-2fcf-4629-8464-e976f0c23498)
# tạo FN:
tạo FN tính tuổi: 
![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/255cbc88-0a25-4c9c-b3a6-fe2fb6bbee13)
+ kết quả:
![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/926f82ac-0ff7-498e-9486-45b10ccc653a)

- Tạo hàm để tính số ngày nghỉ của nhân viên trong một tháng cụ thể:
![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/477e6543-1c43-4cb7-809d-60e292abacb5)

- Tạo hàm FN_TinhLuong.hàm này tính lương dựa trên mức lương cơ bản, số ngày công, và hệ số lương.
![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/125bd085-6b08-49be-9fda-b429b1331771)
# tạo trigger với chức năng lưu lịch sử thay đổi thông tin nhân viên 
- đầu tiên tạo một bảng lịch sử thay đổi thông tin nhân viên.
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/88140534-6f8e-4098-8cd0-670ab655f8b1)
- sau đó tạo trigger
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/fd3d93f0-8a44-4ea6-9f46-4d5c831ef0b3)
- kết quả :
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/81df52a9-dd6a-4239-8f8e-9888128399e4)
  # Tạo corsor
- Tạo một cursor để duyệt qua từng nhân viên trong bảng NhanVien và cập nhật lương của họ dựa trên một điều kiện (tăng 10% lương cho những nhân viên có chức vụ là "Bác sĩ").
  ![image](https://github.com/dnhnghv/Qu-n-l-nh-n-s-/assets/168661356/60408348-4356-4428-a976-7fc8eb9293eb)






































