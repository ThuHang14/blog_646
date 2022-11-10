![Screenshot from 2022-10-17 13-50-03](https://user-images.githubusercontent.com/96046778/196108116-847469f3-6b2f-46bc-8e9d-c9bd969abc53.png)  

- một vài registry để upload image cá nhân lên    
![Screenshot from 2022-10-17 14-55-13](https://user-images.githubusercontent.com/96046778/196120640-3c329cba-9654-4147-a9bf-6562528a3ab8.png)

# [install docker](https://docs.docker.com/engine/install/ubuntu/) 
- `Got permission denied while trying to connect to the Docker daemon socket` - sửa lỗi này khi chạy docker version như sau : 
  1. groups : kiểm tra group đang có 
  2. sudo usermod -aG docker [name_group] : nhóm mới vào group gruop 
  3. su - [userName] : chạy lại user
  4. nhập tiếp groups sẽ thấy docker-> chạy lệnh docker bình thường mà không cần gọi tới sudo 
  - thao tác dùng khi tải xong docker hoặc thêm user mới vào docker 

## Docker Components
<b>1. image </b >
![Screenshot from 2022-10-17 20-50-01](https://user-images.githubusercontent.com/96046778/196194789-a2664909-1375-4e2d-9ccd-9644677ca7fa.png)

  - có 3 layer : 
    1. base (ubutu) 
    2. tool (python)
    3. source code 

  - dung lượng image : alpine (nhẹ nhất ) -> slim -> bust 
  - image không thể thay đổi mà chỉ có thể đọc (Read-only template) - File bất biến . Ta chỉ có thể tạo mới image và ghi thêm phía trên layer 3 (write on top) 
  - giống như 1 khuôn mẫu để tạo ra môi trường chạy ứng dụng vd như 1 ổ usb chứa tệp cài zorin nó sẽ chữa các thư viện , công cụ để khởi chạy zorin 
  - đại diện cho 1 ứng dụng tại 1 thời điểm 
  - chứa các source code , library , dependences , tool -> để tạo nên container và start ứng dụng của ta
  - có nhiều cách tạo thường là viết docker file rồi build -> push lên regisry (docker hub,gitlab ...) 
  
  ```docker
  docker image --help
  docker pull <image>:<tag>
  docker images 
  docker tag <image>:<tag> <iamge>:<new_tag>
  docker image rm <image>:<tag>
```

```docker
  docker save <image>:<tag> -o <namefile>.tar
``` 
  - -o : output mà ta đưa ra 
  - lưu image thành 1 file system 
  - ll | grep <image>  -> xem file đã nén ở trên 
  - có hiểu nôm na là nén file

  ```
  docker image load -i <thử file .tar đã nén ở trên >
   -> pull image từ file .tar (thường dùng khi không có mạng ) 
   - hiểu nôm na là giải nén file 
  ``` 
  - save và load là 2 quá trình ngược nhau nén và giải nén 

<b>2. container </b>
  - run time environment : là môi trường chạy ứng dụng 
  - cho phép ứng dụng chạy độc lập 
  - chỉ ảo hóa ở lớp ứng dụng , chia sẻ tài nguyên trên host 
  - là 1 instance của 1 docker image (1:35 day10)   
  - hoạt động độc lập , hỏng sẽ không ảnh hưởng đến sever đó 
  - image khởi tạo bằng container khởi chạy ứng dụng độc lập tài nguyên trên local 

  ```
  docker run <image>:<tag>
  ctrl + c 
  docker ps -a == doker container ls -a 
  -> lấy ra các container ở các trạng thái 
  docker ps -> lấy ra container đang chạy 
  ```

  ``` 
  chạy ngầm : 
  docker run -itd <image>:<tag>
    -d (detached ) : option chạy ngầm 
    -itd : đi cùng -d , cho phép chạy ngầm , cho phép container mở nhiều shell như ssh , -t cho nhiều ng cùng truy cập chia ra nhiều session mỗi ng 1 cái k ai chạm ai 
    - day10_2h18
    --name <name> : đặt tên cho container nếu không có thì sẽ là tên mặc định 
    ===>  docker run -itd --name <name> <image>:<tag>
  ```

  ```
  docker container rm -f <id_container> : -f xóa cả khi containẻ đó đang chạy trong phần chạy ~ stop

  docker container rm <id_container> : khi đã stop rồi thì lệnh này sẽ xóa hẳn container đi , xóa container chứ k xóa image 
  ```

  ```
  -web : -p 8080:80 -> port import từ mạng bên ngoài vào mạng bên trong (docker) và chạy ở cổng 80 đc public ra mạng của ta là 8080 
  ```
  tổng kết : 
 ` docker run -itd -p <port>:<port> --name <name> <image>:<tag>`


  - day10_2h49 

  ```
  curl localhost:8080 : truy vấn vào trang html đang chạy ở cổng 8080 

  sudo netstat -ntlp ????
  sudo netstat -plant ???? 
  ```

  - truy cập vào sever 
  ```
  docker exec --help  
  docker exec <id_contaier> curl localhost  

  - đi vào container (xem dữ liệu , đại loại như push code tham khảo code dưới : thao tác copy 1 file vào container )
  ```

![Screenshot from 2022-10-17 22-53-49](https://user-images.githubusercontent.com/96046778/196224897-5f35aa19-8dbf-4fa3-a87b-cf3a2e241dd6.png)

```
  docker exec -it <id_container> bash 
  bash hoặc sh tùy máy  
   ==> exit 
```

- Status container (thao tác từng trạng thái container , lệnh trên là thao tác chung )
![Screenshot from 2022-10-18 09-30-37](https://user-images.githubusercontent.com/96046778/196321638-39e8d254-c7d2-436f-9a3a-95c95628bb26.png)
  1. create   
  `docker create -it --name <name> <image>:<tag>`
  2. running   
  `docker start -i <id_container>`  k có lệnh chạy ngầm -d nên sẽ mở thêm 1 terminal để ssh khi chạy lệnh đó, còn không thì bỏ -i đi thì sẽ chạy ngầm 
  3. stopped   
  `docker stop <id_container>`
  - stop ~ tắt , paused ~ ngủ đông 

  4. delete    
  `docker rm <id_container>`

  5. all
  muốn xóa docker từ trạng thái run sang delete ta có lệnh đi tắt : 
  `docker rm -f <id_container>` 
  - thên -f vào 


<b>3. network </b>
  - docker sẽ khởi tạo mạng ảo riêng để sd cho container , giúp các container giao tiếp vs nhau và từ inernet truy cập vào trong ứng dụng chạy trong container trong docker 

<b>4. volume </b>
  - lưu trữ dữ liệu bởi docker demon và thường đc sd bởi docker container cho phép các container lưu trữ dữ liệu bền vững ngay cả khi ứng dụng start stop hay thậm chí xóa đi thì vẫn còn dữ liệu   




