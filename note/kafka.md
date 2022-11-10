## Apache Kafka® là một nền tảng stream dữ liệu phân tán

- [link](https://topdev.vn/blog/kafka-la-gi/)

- Là hệ thống message pub/sub phân tán (distributed messaging system). Bên pulbic dữ liệu được gọi là producer, bên subscribe nhận dữ liệu theo topic được gọi là consumer. Kafka có khả năng truyền một lượng lớn message theo thời gian thực, trong trường hợp bên nhận chưa nhận message vẫn được lưu trữ sao lưu trên một hàng đợi và cả trên ổ đĩa bảo đảm an toàn. Đồng thời nó cũng được replicate trong cluster giúp phòng tránh mất dữ liệu.

- Kafka thường được sử dụng cho 2 mục đích chính sau:

  - Xây dựng các pipeline stream dữ liệu theo thời gian thực để nhận dữ liệu giữa các hệ thống hoặc ứng dụng một cách đáng tin cậy.
  - Xây dựng các ứng dụng stream theo thời gian thực để biến đổi hoặc ánh xạ đến các stream của dữ liệu.
    - stream data: dòng dữ liệu, hãy tưởng tượng dữ liệu là nước trong 1 con suối.
    - Data Pipeline: dùng để thiết lập kênh liên lạc giữa 2 hệ thống hoặc dịch vụ.

## kafka components

1.Producer
2.consumer
3.Broker
4.Cluster
5.Topic
6.Partitions
7.Offset
8.Consumer groups
