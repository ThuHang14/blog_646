## Dockerize ứng dụng SpringBoot

1. Tạo file jar

```shell
mvn clean package -DskipTests 
```

Sau bước này sẽ tạo ra 1 file có đuôi **.jar** trong thư mục **target**

Có thể kiểm tra chạy ứng dụng bằng câu lệnh sau

```shell
java -jar target/todolist-backend-0.0.1-SNAPSHOT.jar
```

2. Viết Dockerfile

Trong thư mục gốc chứa project, tạo file `Dockerfile`

```dockerfile
FROM openjdk:11.0.16-oraclelinux8

COPY target/todolist-backend-0.0.1-SNAPSHOT.jar todolist-backend-0.0.1-SNAPSHOT.jar

ENTRYPOINT ["java","-jar","/todolist-backend-0.0.1-SNAPSHOT.jar"]
```

3. Build docker image

```shell
docker build -t 14thuhang/test-app:latest .

docker image rm <image>:<tag>
```

4. Đẩy lên docker hub (nếu có tài khoản)

```shell
docker push 14thuhang/test-app:latest
```

5. Run container chạy thử

```shell
docker run <image>:<tag> => not detach 
docker run -d --name test-app -p 8888:8080 14thuhang/test-app:latest => new
 docker run -d -p 8888:8080 14thuhang/test-app:latest  => that container 
```
check 8888 : 

6. [docker compose](https://jsramblings.com/dockerizing-a-react-app/)
docker network create backend-network `front`

docker compose down
docker compose up -d `--build`


