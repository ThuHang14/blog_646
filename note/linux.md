- `q` enter esc : thoát
- ctrl + c :
----------- linux -------------
- cd /usr/local -> ll hoặc ls hoặc ls -a : vào thư mục và xem chi tiết
docker version
- `-a` : all
- `pwd`: tìm đường dẫn của thư mục hiện tại (folder) mà bạn đang ở trong đó
- `cd` : chuyển hướng trong hệ thống tập tin Linux, bạn có thể sử dụng command cd. Nó sẽ cần nhập đường dẫn đầy đủ hoặc tên thư mục bạn muốn chuyển tới.
- `ls` được dùng để xem nội dung thư mục - ls -R : liệt kê các file bao gồm cả các thư mục phụ bên trong - ls -a : liệt kê những file ẩn - ls -al : liệt kê tất cả file và thư mục với thông tin chi tiết như phân quyền, kích thước, chủ sở hữu, vân vân.
- `cat` : xem nội dung file trên output tiêu chuẩn (sdout).
- `cp` : để sao chép files từ thư mục hiện tại .
- `mv` là di chuyển files, dù nó cũng có thể được dùng để đổi tên files. ( mv oldname.ext newname.ext )
- `mkdir` : tạo thư mục mới
- `rmdir` : rmdir chỉ cho phép bạn xóa các thư mục trống.
- `rm` được sử dụng để xóa thư mục và nội dung bên trong thư mục đó.
- `touch` cho phép bạn tạo files mới trống thông qua dòng lệnh
- `locate` : (định vị) file, giống như lệnh tìm kiếm trong Windows.
- `-i` với lệnh này làm cho nó không còn phân biệt chữ hoa chữ thường, nên bạn có thể tìm file ngay cả khi không nhớ tên chính xác.
(*) Để tìm file chứa hai hoặc nhiều từ, hãy sử dụng dấu hoa thị . Ví dụ: command locate -i school*note sẽ tìm tất cả file nào chứa từ “school” và “note”, không phân biệt chữ hoa hay chữ thường.
- `find` cũng tìm files. Sự khác biệt là bạn sử dụng command find để xác định vị trí files trong thư mục nhất định.
- `grep` cho phép bạn tìm kiếm tất cả text thông qua tập tin nhất định.
- `sudo` là viết tắt của “SuperUser Do”, cho phép bạn thực hiện các tác vụ yêu cầu quyền quản trị hoặc quyền root.
- `df` dùng để nhận báo cáo về dung lượng lưu trữ được sử dụng trên hệ thống, hiển thị theo tỷ lệ phần trăm và KBs. Nếu bạn muốn xem báo cáo tính bằng megabyte, hãy nhập df -m.
- `du` : kiểm tra dung lượng của file hoặc của thư mục theo định dạng kích thước thông thường . Nếu bạn muốn xem theo byte, kilobyte và megabyte, hãy thêm argument -h vào dòng lệnh.
- `head` được sử dụng để xem dòng đầu tiên của bất kỳ file văn bản nào. Theo mặc định, nó sẽ hiển thị 10 dòng đầu tiên, nhưng bạn có thể thay đổi số này theo ý mình. chỉ muốn hiển thị 5 dòng đầu tiên, hãy nhập head -n 5 filename.ext.
- `diff` sẽ so sánh nội dung của 2 files từng dòng một. Sau khi phân tích files này, nó sẽ xuất ra các dòng không khớp nhau. ( diff file1.ext file2.ext )
- `tar` là command được sử dụng rộng rãi nhất để lưu trữ nhiều file vào tarball – một định dạng file Linux phổ biến tương tự định dạng zip, nhưng nén file thì tùy.
- `kill` : Nếu có chương trình nào đó không phản hồi, bạn có thể chấm dứt chương trình thủ công
- `ping` để kiểm tra trạng thái kết nối của bạn với server. ping google.com, lệnh sẽ kiểm tra xem bạn có thể kết nối với Google hay không và đo thời gian phản hồi.
- `wget` : tải file từ internet xuống ( gõ wget, đằng sau là link tải xuống. )
- `uname`, viết tắt của Unix Name, sẽ in thông tin chi tiết về hệ thống Linux của bạn như tên máy, hệ điều hành, kernel, v.v.
- `top` sẽ hiển thị danh sách tiến trình đang chạy và lượng CPU mà tiến trình đó sử dụng
history đặc biệt hữu ích nếu bạn muốn xem lại những command bạn nhập trước đó.
- `echo` : Lệnh này được dùng để chuyển dữ liệu vào một file.
- `zip` để nén file thành zip archive và lệnh unzip để giải nén file zipped trong zip archive.
- `hostname` : cho biết tên của một máy / mạng máy tính
Vì Linux là một hệ máy đa người dùng, có nghĩa là nhiều hơn 1 người tương tác với máy cùng lúc. useradd được dùng để tạo user mới, còn passwd đặt mật khẩu cho một tài khoản user. Để thêm user có tên John, useradd John rồi thiết lập password bằng lệnh passwd 123456789. Để xóa một user cũng tương tự như thêm user. Để xóa user account, nhập lệnh userdel UserName
