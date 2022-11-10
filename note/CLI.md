- command line interface : ~ giao diện
- GUI : a graphic user interface
  - là loại giao diện phổ biến nhất , tương tác chủ yếu qua bàn phím và chuột
- CLI & Terminal : nơi người dùng nhập các dòng lệnh và nhận kết quả trên màn hình ( trong OS của linux chỉ có CLI không có GUI ) (terminal có hỗ trợ tương tác chuột giúp ta có thể lăn lên xuống )
  ![image](https://user-images.githubusercontent.com/96046778/195558602-d2e4cd42-37e9-4ea9-9c5a-1d9286544ddf.png)
- vim chuyen sang che do insert mode -> an phim i , nha esc chuyen ve che do command ---- day2 1:20
- sudo apt install vim
- [xóa process ](https://vinasupport.com/sua-loi-unable-to-lock-the-administration-directory-var-lib-dpkg-ubuntu/)

- linux : giống 1 mạng xã hội , mỗi ng sẽ có 1 tài khoản , tên , pass khác nhau hiểu nôm na như fb , chỉ là user bình thường và phair login khi vào mỗi tài khoản như 1 uid
- win thì kkhi khởi tạo sẽ là 1 ng dùng và có toàn quyênf admin vs hệ thống may tính của mk

![image](https://user-images.githubusercontent.com/96046778/195571128-05128576-b6bc-40ff-8d85-a176b18df88f.png)

- 3 người dùng trong ảnh dưới
  - userroot : cài sẵn trong máy ,chỉ có 1 tk , có toàn quyền , uid = 0 , k thể xóa
  - user accont - nomal : mn dùng để đăng nhập vào, có thể có nhiều tk, kưu trữ thông tin ng dùng
  - user sẻvice accout - system account : k pass , có thể có nhiều tk, dùng để cho service , vd ta có chtrinh mysql thì sẽ tạo 1 user quản lí mysql đó thôi
    ![image](https://user-images.githubusercontent.com/96046778/195571857-3b6ca320-9396-4e9d-a11c-f14c8092bcc2.png)

![image](https://user-images.githubusercontent.com/96046778/195572925-d02a383c-1254-41d9-b623-489093b05114.png)
![image](https://user-images.githubusercontent.com/96046778/195573514-029523a9-131c-407c-b861-9cebec4e14af.png)

- cat etc/passwd
  - tên : pass ~ x : userid : description : thư mục home của ngươi dùng đó : shell (chtrinh giao tiếp bin bat sh )
- cat etc group

## câu lệnh thao tác trên user group

![image](https://user-images.githubusercontent.com/96046778/195574858-9b5eaf55-a93a-4cb4-ae0f-80b879c06588.png)
