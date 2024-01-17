# Quy tắc khi sử dụng máy chủ aiotlab3:
 - Tên máy chủ: aiotlab3
 - IP cố định: 202.191.58.201

## Thông tin phần cứng của server:
- Mainboard: X570 AORUS ULTRA 
- CPU: AMD Ryzen 9 3900X (24) @ 3.800GHz
- GPU: NVIDIA GeForce GTX TITAN X
- GPU: NVIDIA GeForce RTX 2080 Ti
- RAM: 64gb

## 1. Hướng dẫn kết nối
- Trước tiên, bạn phải liên hệ với anh Lê Công Thành để được tạo tài khoản. 
- Sau khi đã có tài khoản, tiến hành đăng nhập theo cú pháp: <code>ssh [Tên tài khoản]@[IP cố định]<code> 
- Tiến hành nhập mật khẩu khi được nhắc.

## 2. Tạo workspace:
- Sau khi hoàn thành bước 1, đi đến thư mục của lab: <code>cd /home/aiotlab3/RISE<code>.
- Tiến hành tạo thư mục cá nhân theo họ tên riêng: <code>mkdir [Họ tên riêng]<code>. Ví dụ: Tên là Nguyễn Văn An thì <code>mkdir [annv]<code>.
- Nếu muốn cấu hình các tùy chỉnh theo cá nhân thì phải được lưu trong thư mục cá nhân này.

## Một số lưu ý chung:
### Lưu trữ dữ liệu:
- Kiểm tra dung lượng cá nhân: <code>du -sh [Đường dẫn tới thư mục cá nhân của bạn]<code>. Nếu bạn đang ở thư mục cá nhân thì chỉ cần gõ <code>du -sh .<code>

- Dung lượng của mỗi thư mục cá nhân được cài đặt tối đa là 50gb. Không được phép lưu trữ lớn hơn dung lượng này ở thư mục home.
 
- Nếu muốn lưu trữ lớn hơn, bạn phải tạo thư mục cá nhân ở ổ cứng <code>/media/aiotlab3/27934be5-a11a-44ba-8b28-750d135bc3b3/RISE/[Họ tên riêng]<code>. Dung lượng tối đa cho phép ở dây cho mỗi cá nhân là 100gb.

### Sử dụng GPU:
- Kiểm tra hoạt động của GPU: <code>nvidia -smi<code>
- Có hai GPU: Con GTX TITAN X tên là <code>cuda:1<code> với ID là 1, con RTX 2080 Ti là <code>cuda:0<code> với ID là 0.
- Nếu không tùy chỉnh, sẽ chỉ luôn chạy <code>cuda:0<code>

- Chọn GPU để chạy: <code>export CUDA_VISIBLE_DEVICES="[ID của GPU]"<code>
- Nếu muốn chạy cả hai con đồng thời (Không khuyến khích): <code>export CUDA_VISIBLE_DEVICES="0,1"<code>

- Việc huấn luyện, tinh chỉnh và suy diễn:
  Định nghĩa:
   Mô hình nhỏ: Là các mô hình có dưới 1 tỷ tham số (VD: BERT, BART, roBERTa,...)
   Mô hình lớn: Là các mô hình có trên 1 tỷ tham số (VD: Llama-2, Mistral, TransformerXL,...)
   - Được phép sử dụng GPU cho mục đích huấn luyện, tinh chỉnh các mô hình nhỏ và suy diễn các mô hình lớn.
   - Không được phép sử dụng GPU cho việc huấn luyện và tinh chỉnh các mô hình lớn.
  Chi tiết về số lượng tham số của mô hình có thể xem ở HuggingFace hoặc chạy mã nguồn để kiểm tra.

### Hệ thống
- Thông tin về RAM theo thời gian thực: <code>top<code>.
- Khi sử dụng chú ý lượng RAM, vì dung lượng của nó rất hạn chế (64gb) so với số người dùng, rất dễ xảy ra vấn đề tràn RAM nếu không kiểm soát. 
- Không truy cập vào các tập tin và trình điều khiển hệ thống để tinh chỉnh tùy ý.

Rất mong anh em sử dụng đúng quy định!
