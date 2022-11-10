## Monolithic so với microservice

- [link](https://comdy.vn/microservice/kien-truc-microservice/)
-  (monolithic) là cách truyền thống để xây dựng và triển khai các ứng dụng.
- Cấu trúc này dựa trên khái niệm về một đơn vị duy nhất, không thể chia tách, bao gồm phía máy chủ, phía máy khách và cơ sở dữ liệu. Tất cả các khía cạnh được thống nhất và quản lý như một đơn vị và cơ sở mã.
- Điều này có nghĩa là mọi cập nhật phải được thực hiện cho cùng một cơ sở mã, vì vậy toàn bộ ngăn xếp phải được thay đổi. Khi các ứng dụng nguyên khối có quy mô, chúng có thể trở nên khá phức tạp, do đó sự phát triển tổng thể thường dài hơn.Ngược lại,  chia nhỏ khối đó thành các đơn vị độc lập có chức năng như các dịch vụ riêng biệt. Điều này có nghĩa là mọi dịch vụ đều có logic và cơ sở mã riêng. Chúng giao tiếp với nhau thông qua các API (giao diện lập trình ứng dụng).
![Screenshot from 2022-10-25 11-03-23](https://user-images.githubusercontent.com/96046778/197679649-a1c68762-2e1a-49c8-9e2e-9bdaa34a1402.png)

- Chọn kiến ​​trúc nguyên khối : 
  - Nếu công ty của bạn là một nhóm nhỏ : Sử dụng kiến trúc này, bạn không phải đối phó với sự phức tạp của việc triển khai kiến ​​trúc microservice.
  - Nếu bạn muốn khởi động nhanh hơn : Kiến trúc nguyên khối nhỏ đòi hỏi ít thời gian hơn để khởi động. Hệ thống này sẽ cần nhiều thời gian hơn để cập nhật hệ thống của bạn, nhưng việc khởi chạy ban đầu nhanh hơn.

- Chọn kiến ​​trúc microservice : 
  - Nếu bạn muốn phát triển một ứng dụng có khả năng mở rộng hơn : Mở rộng một kiến ​​trúc microservice dễ dàng hơn nhiều. Các chức năng và mô-đun mới có thể được thêm vào rất dễ dàng và nhanh chóng.
  - Nếu công ty của bạn lớn hơn hoặc có kế hoạch phát triển : Sử dụng microservice rất tốt cho một công ty có kế hoạch phát triển, vì kiến ​​trúc microservice có khả năng mở rộng và dễ dàng tùy chỉnh hơn theo thời gian.

  ![Screenshot from 2022-10-25 11-02-44](https://user-images.githubusercontent.com/96046778/197679602-e9c52731-3580-4a88-b7fb-154cabf6c435.png)

- Nói nôm na về nguyên tắc hoạt động của một API Gateway thì nó sẽ cho phép chúng ta có thể cấu hình để khi một request tới nó thì đối với request này, nó sẽ forward request tới service này, còn request kia nó sẽ forward cho service kia. Spring Cloud Gateway cũng có chức năng như vậy. Spring Cloud Gateway hỗ trợ chúng ta các filter, giúp chúng ta có thể thay đổi một request bất kỳ tới các service bên trong như thêm request parameter, thay đổi request URL, thêm header này nọ, … Chúng ta có thể thêm mới các custom filter, nghĩa là các bạn có thể viết code Java, để thêm bất kỳ các logic xử lý khác trước khi một request thực sự được forward đến target service

- [link](https://cloud.cmctelecom.vn/use-cases/Microservice)