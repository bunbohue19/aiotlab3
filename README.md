# Quy tắc khi sử dụng máy chủ aiotlab3:
 - IP public: `202.191.58.201`

## Thông tin phần cứng của server:
- Mainboard: X570 AORUS ULTRA 
- CPU: AMD Ryzen 9 3900X (24) @ 3.800GHz
- GPU: NVIDIA GeForce GTX TITAN X
- GPU: NVIDIA GeForce RTX 2080 Ti
- RAM: 64gb

## 1. Tạo tài khoản
- Trước tiên, bạn phải liên hệ với anh [Lê Công Thành](https://www.facebook.com/thanh.toanlamson) để được tạo tài khoản.
- Sau khi nhận tài khoản, bạn vui lòng khởi tạo lại mật khẩu mặc định.

## 2. Kết nối
- Sau khi đã có tài khoản, tiến hành đăng nhập theo cú pháp: `ssh [Tên tài khoản]@[IP cố định]`
- Tiến hành nhập mật khẩu khi được nhắc.

## 3. Workspace:
- Sau khi hoàn thành bước 1, bạn sẽ được tạo thư mục home tại `/users/${username}` ở đó username là tên user của bạn.
- Đối với bộ lưu trữ lâu dài, bạn vui lòng truy cập tại đường dẫn `/media/aiotlab3/27934be5-a11a-44ba-8b28-750d135bc3b3/RISE/username` ở đó username là tên user của bạn.

## Một số lưu ý chung:
### Lưu trữ dữ liệu:
- Kiểm tra dung lượng cá nhân: `du -sh [Đường dẫn tới thư mục cá nhân của bạn]`. \
  Nếu bạn đang ở thư mục cá nhân thì chỉ cần gõ `du -sh .`
- Dung lượng của mỗi thư mục cá nhân được cài đặt tối đa là 50gb. Không được phép lưu trữ lớn hơn dung lượng này ở thư mục home.
- Nếu muốn lưu trữ lớn hơn, bạn phải tạo thư mục cá nhân ở ổ cứng HDD `/media/aiotlab3/27934be5-a11a-44ba-8b28-750d135bc3b3/RISE/[Họ tên riêng]`. Dung lượng tối đa cho phép ở đây cho mỗi cá nhân là 100gb.

### Sử dụng GPU:
- Kiểm tra hoạt động của GPU: `nvidia-smi`
- Có hai GPU: Con GTX TITAN X tên là `cuda:1` với ID là 0, con RTX 2080 Ti là `cuda:0` với ID là 1.
- Nếu không tùy chỉnh, sẽ chỉ luôn chạy `cuda:0`

- Chọn GPU để chạy: `export CUDA_VISIBLE_DEVICES="[ID của GPU]"`
- Nếu muốn chạy cả hai con đồng thời (Không khuyến khích): `export CUDA_VISIBLE_DEVICES="0,1"`

- Việc huấn luyện, tinh chỉnh và suy diễn:\
  Định nghĩa:\
   Mô hình nhỏ: Là các mô hình có dưới 1 tỷ tham số (VD: BERT, BART, roBERTa,...)\
   Mô hình lớn: Là các mô hình có trên 1 tỷ tham số (VD: Llama-2, Mistral, TransformerXL,...)
   - Được phép sử dụng GPU cho mục đích huấn luyện, tinh chỉnh các mô hình nhỏ và suy diễn các mô hình lớn.
   - Không được phép sử dụng GPU cho việc huấn luyện và tinh chỉnh các mô hình lớn.\
Chi tiết về số lượng tham số của mô hình có thể xem ở HuggingFace hoặc chạy mã nguồn để kiểm tra.

### Hệ thống
- Thông tin về RAM theo thời gian thực: `top`.
- Khi sử dụng chú ý lượng RAM, vì dung lượng của nó rất hạn chế (64gb) so với số người dùng, rất dễ xảy ra vấn đề tràn RAM nếu không kiểm soát. 
- Không truy cập vào các tập tin và trình điều khiển hệ thống để tinh chỉnh tùy ý.

Rất mong anh em sử dụng đúng quy định 🙂. 
