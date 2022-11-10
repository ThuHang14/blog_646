# Docker storage - data
![Screenshot from 2022-10-18 10-14-13](https://user-images.githubusercontent.com/96046778/196327214-089e0b37-b9c8-4453-bc95-5a5b2d678daa.png)  

- mục đích : lưu trữ dữ liệu sang docker host  

![Screenshot from 2022-10-18 10-18-56](https://user-images.githubusercontent.com/96046778/196327780-c9f0b061-119f-4110-a81d-97cdbbccb7bc.png)  
 - Chi tiết 3 kiểu lưu trữ dữ liệu này:

    - Dữ liệu trên volume được lưu trên filesystem của Docker host (/var/lib/docker/volumes/) và được quản lý bởi Docker deamon. Các process không liên quan đến Docker sẽ không đụng đến phần dữ liệu này. Volumes là cách lưu trữ dữ liệu tốt nhất trên Docker.
    - Bind mount có thể được lưu ở bất cứ đâu trên máy host. Các process không liên quan đến Docker hoặc một container khác có thể chỉnh sửa các file này bất kỳ lúc nào.
    - Tmpfs mound được lưu trên bộ nhớ (RAM) của máy host và không ghi lên trên host filesystem (không ghi lên disk).

- 2 kiểu mount thường dùng 

![Screenshot from 2022-10-18 10-22-56](https://user-images.githubusercontent.com/96046778/196328263-15297a74-28bf-4b4c-8c57-4a5eb2c39add.png)  

- bindmount ra đời trước nên sẽ ít tính năng hơn , bindmount cho hiệu năng tốt nhưng bị phụ thuộc vào file system của docker , yêu cầu đg dẫn tuyệt đối (từ root đi xuống) , sẽ mount đg dẫn vào container 
- mount : hiểu nôm na là ta có 1 usb để sd đc trên linux ta sẽ mout vào đg dẫn trên file system để truy cập vào usb đó 
- ## [volume](https://viblo.asia/p/mount-trong-docker-4dbZNnBkZYM)  


![Screenshot from 2022-10-18 14-13-20](https://user-images.githubusercontent.com/96046778/196361593-4d8ce4ed-a6a0-45b8-9950-dc5db1701521.png)

- Storage trong docker là một tính năng quản lý data của docker. Data ở đây có thể hiển là các file trong quá trình chạy ứng dụng như file log, file data …
- Khi chạy một container, data trong quá trình vận hành được chưa ở writeable layer và sẽ bị mất đi khi container bị xóa. Để giải quyết được vấn đề này, Docker đã đưa ra một cơ chế để quản lý data của các container đó là Docker Storage.
- Về bản chất, Docker storage là một cơ chế cho phép lưu trữ các data của container và docker host bằng cách mount mot folder từ Docker Container vào Docker Host.
- Bằng việc mount này, data trong Container giờ đây sẽ được an toàn hơn, dễ dàng chia sẻ giữa các container với nhau hơn. Một số chứa setting hay log có thể được đọc dễ dàng hơn trong quá trình troubleshoot các Container.

- thực hành Volume : 
    - docker volume create <name_volume>    : Tạo một volume
    - docker volume ls                  : List danh sách volume
    - docker volume inspect <name_volume>   : Hiển thị thông tin của Volume
    - sudo ls < Mountpoint xem trong inspect >        : Kiểm tra volume được tạo ra
         - `docker run -idt -v <name volume >:<container>  ` <=> docker run -idt -v my-v:/otp/mount_point centos
        - -v : mount volume vào đg dẫn trong container , chưa có thì sẽ đc tự tạo 
        - sau dấu `:` thì điền đg dẫn nào cx đc , do mình lựa
        - `docker exec <id_container> sh -c "echo 'This is file test' > /otp/mount_point/test.txt"` <=> docker exec 9cc6 sh -c "echo 'This is file test' > /otp/mount_point/test.txt"
        - Docker exec là câu lệnh sử dụng để chạy một command bên trong một container đang hoạt động. (command : câu lệnh )
        - -c : phần truyền câu lệnh vào ( 9cc6 là id của container )
        - kiểm tra file vừa ghi : docker exec 9cc6 sh -c "cat /otp/mount_point/test.txt"  

- thực hành bind mounts : (sẽ phải chỉ ra đường dẫn tuyệt đối của file system )
    - 46.40
    - `docker run -itd -v /opt/docker_host_folder:/opt/mount_point centos`
    - /opt/docker_host_folder : đường dẫn tuyệt đối của file system trên docker host 
    - sudo mkdir -p /otp/docker_host_mount  : tạo thư mục mới
    - docker run -itd --mount type=bind,src=/otp/docker_host_mount,dst=/otp/mount_point centos  : chạy 
    - -v tượng tự như khai báo type , .. rút ngắn câu lệnh bằng -v 

    - docker exec 442d8 sh -c 'echo "Hello" > /otp/mount_point/test.txt' :viết mới file test
    - docker exec 442d8 sh -c 'cat /otp/mount_point/test.txt' : kiểm tra file test
    - cat /otp/docker_host_mount/test.txt  : kiểm tra thư mục vừa tạo ở trên có tồn tại trên docker system không 
 
 - tóm tắt : 
    - [link](https://cloudcraft.info/nhap-mon-docker-phan-2-gioi-thieu-cac-kieu-luu-tru-du-lieu-tren-docker/)
    - sau `-v` nếu là tên thì sẽ là volume còn là đường dẫn thì sẽ là bind-mount 
    - volume là do docker quản lí với đg dẫn mặc định là /var/lib/docker
    - binds-mount thì mk có thể mount với đg daanc bất kì trên docker host 
    - giúp đưa file từ localhost ra file system để lưu trữ data 
    - docker inspect my-v => lấy ra Mountpoint 
    - Mountpoint : vào thư mục root 
    - cd /var/lib/docker/volumes/my-v/_data
    - ll -> sẽ thấy file test.txt " This is file test "
    - ==> exit 





