- linux : kpp hệ điều hành mà là 1 hệ điều hành nhân linux , linux là hệ điều hành free k mất phí như win và có opensource code
- OS (Operating System) Hệ điều hành 
- ![image](https://user-images.githubusercontent.com/96046778/195279721-3eb54e85-c004-4776-b6dc-2bdeeb692ef0.png)
- Hardware : phần cứng
- kernel : nhân ( start máy tính -> kernel điều khiển các ứng dụng , vd mở chorme nó sẽ quyết định chorme sẽ đc dùng bao nhiêu ram , cpu ) , khi ta tắt các tap thì kernel sẽ đi dọn dẹp để điều phối tài nguyên , là nơi giao tiếp p cứng p mềm
- shell : lớp biên dịch , khi ta lấy dữ liệu , thông tin từ hardware thì sẽ đc chuyển hóa thành các câu lệnh ( các câu lẹnh sẽ gọi đến kernel nhưng k thể hiểu ngôn ngữ tập lệnh bậc cao vd ls ... mà chỉ hiểu đc ngôn ngữ nhị phân vd: 01010 nên shell sẽ dùng để biên dịch )
- application layer : gồm system libraries (thư viện hệ thống chương trình ng dùng vd ổ C có thư mục này) , system tool , development tool (công cụ phát triển ứng dụng) , end user tool . Tạo ra các bản phân phối vd hdh Win qua rất nhiều version

### Phân loại os

- ![image](https://user-images.githubusercontent.com/96046778/195282857-7263e51a-1c45-4472-a369-5933f71a1ed0.png)

- ![image](https://user-images.githubusercontent.com/96046778/195285655-92d74031-af4e-4a23-9d08-c81403b426fe.png)
- [5 cấp độ dùng linux](https://maximilianocontieri.com/explain-in-5-levels-of-difficulty-linux)

- Thực hành : tải virtuaBox , dùng ubutu server
- run virtuabox :
- có thể bỏ qua updatte vesion
- ngôn ngữ : English
- keyboard : English
- cấu hình network connection : để mặc định cx đc , máy ảo đã cài sẵn 1 drive ,đã có 1 cap mạng ( địa chỉ ip của máy vd : 10.0.2.15/24 : ip nội bộ của mình)
- proxy : next
- configure ubutu archive mirror : là 1 cái link chữa các phần mêm package của ubutu khi ta cập nhật thì sẽ kiểm tra version phần mềm cx như ubutu trên link này
- guided storage configuation : chọn ổ đĩa , máy ảo thì chỉ đc chọn 1 , phần dưới là để mã hóa ổ đĩa
- storage configuation :
- profile setup : đặt tên cho máy đó thuhang - ubutu - thuhang - 123
- ssh setup : tải 1 số tiện ích cho ubutu -> tích zô open ssh server để dùng ssh ( truy cập tới server qua giao thức ssh )
- featured server snaps : tải thêm 1 vài package khác của ubutu -> bỏ qua
  -> chờ tải

## Linux file

- ![image](https://user-images.githubusercontent.com/96046778/195316137-9faf42b9-dcb7-4d0e-823e-c2e2d80743e0.png)
- ![image](https://user-images.githubusercontent.com/96046778/195316513-abecd612-965c-492a-b6ff-8a65510a5481.png)
- mọi thứ trong linux là file
  ![image](https://user-images.githubusercontent.com/96046778/195319057-81c4a046-af4f-4de5-92da-7b5311ab2716.png)
- phần mềm mất phí , bản quyền sẽ đc cài trong `/otp`
  ![image](https://user-images.githubusercontent.com/96046778/195319260-ea44bf5f-5729-46bd-aeec-ab340c700fb9.png)  
  ![image](https://user-images.githubusercontent.com/96046778/195319541-6910af26-a96c-407f-b4dd-97b4ea63b7d9.png)
  ![image](https://user-images.githubusercontent.com/96046778/195319950-ac181d4b-166f-4f96-99a7-0320c35dfeb5.png)
- `/var`
  ![image](https://user-images.githubusercontent.com/96046778/195320494-b173dfe2-fc4f-474c-a205-1e630e648d28.png)
  ![image](https://user-images.githubusercontent.com/96046778/195321313-e50b4ff9-1087-41ac-91e3-49c36b7c2e16.png)
  ![image](https://user-images.githubusercontent.com/96046778/195321574-b0bb4ac8-075a-49c9-8d20-e70ba5b918b5.png)

# [installing Nginx](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04)

- nếu dùng destop thì mở terminal ra conf server thì mặc định là dòng lệnh rồi
- sudo apt update : kiểm tra các version package
- sudo apt upgrade -y : update các package
- -y : thì mk sẽ không cần ấn chữ y
- sudo apt install nginx : tải nginx , trên win tải file còn linux , ubutu dùng lệnh
- sudo systemctl status nginx : kiểm tra xem nginx có hđ không
- ctrl + c : để thoát
- nginx sẽ đc cài trong chương trình cấp 2 có dạng thư mục : /usr/sbin/nginx (kiểm tra : stat /usr/sbin/nginx )

# [installing shh in ubutu 22.0.2](https://linuxhint.com/enable-use-ssh-ubuntu/)
