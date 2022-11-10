> sudo systemctl status docker  : ktra trạng thái docker xem có chạy không => ctrl + C 

```
 docker run -it -p 8080:80 nginx

-it: là interactive terminal nghĩa là nó sẽ chạy trong terminal của chúng ta. Tiếp theo sẽ lấy ra một cái port để truy cập vào, ban đầu sẽ là 8080 và port bên trong container nginx là 80. cuối cùng là tên image là nginx.
```
[click để tham khảo các lệnh cơ bản ](https://viblo.asia/p/docker-va-nhung-nhung-lenh-co-ban-cho-nguoi-moi-tim-hieu-OeVKB6xyKkW)

- nếu image chưa tồn tại thì docker sẽ tự động tải về image đó , chỉ cần nhập đúng tên là oki 

- docker run -p <public-port>:<target-port/protocol> <image>

- docker run -itd -p 9090:80 nginx

- curl localhost:9090

- docker run -idt --network host nginx

- sudo systemctl stop nginx
- docker run -itd -e MY_VAR=VALUE nginx

- docker exec c8f17a003 bash -c "env | grep MY_VAR"

- docker network create --driver bridge devops-network

- docker network ls

- docker network create -d bridge --subnet=10.11.0.0/16 --gateway=10.11.0.1 dev
  ops-net

- docker network inspect devops-network

- docker network connect devops-network game_2048

- docker run -itd --network=devops-network nginx

- docker exec 0f7a0f4 bash -c 'curl 172.18.0.2'

- docker exec 0f7a0f4 bash -c 'curl game_2048'
- docker run -itd -v /opt/docker_host_folder:/opt/mount_point centos

- docker exec 6c1cb32b8c98f11 bash -c 'echo "Hello" > /opt/mount_point/test.txt'

- docker exec 6c1cb32b8c98f11 bash -c 'cat /opt/mount_point/test.txt'

- cat /opt/docker_host_mount/test.txt

- docker run -itd --mount type=bind,src=/opt/docker_host_mount,dst=/opt/mount_point centos
- docker volume create my-volume

- docker volume ls

- docker volume inspect my-volume

- docker run -idt -v my-volume:/opt/mount_point centos

- docker container inspect 17f1000ba716

- docker run -itd --mount type=volume,src=my-volume,dst=/opt/mount_point centos

- docker exec 56cf8 bash -c "echo 'This is file test' > /opt/mount_point/test.t
  xt"

- docker exec 56cf8 bash -c "cat /opt/mount_point/test.txt"

- sudo cat /var/lib/docker/volumes/my-volume/\_data/test.txt
- sudo systemctl enable docker

- docker create -it --name nginx_status nginx:latest

- docker start 34173d729d07

- docker stop 34173d729d07

- docker rm -f <container_id>
- sudo systemctl status docker

- sudo service docker status

- sudo systemctl enable docker
- Production -
- UAT -
- Staging / QA -
- Development / Testing -

- Scale -
- Fault Tolerant -
- High Availability -
- Load balancer -

- Podman
- Trực tiếp server + Tools automation

- Kubernetes + cri-o - containerd
- artifact - tạo tác/ chế tác

- Containerization

  - CGroup: Giới hạn tài nguyên sử dụng: RAM, CPU, Storage
  - Namespace: Cô lập cô lập trình

- Docker Engine/Container Engine

- Public ----------- Private

- Container Registry

  - Docker registry (no GUI) (free)
  - Jfrog jcr (free)
  - Harbor (free)
  - Docker Hub Enterprise
  - AWS, GCP, Azure
  - Redhat, quay.io,....

- alpine
- slim
- bust

- docker pull <image_name>:<tag>
- docker images
- docker image ls 
- docker tag nginx:latest nginx:v10.0.0
- docker image rm nginx:v10.0.0
- docker image save nginx:latest -o nginx.tar
- docker image load -i nginx.tar

- docker run nginx:latest

- docker ps -a
- docker container ls -a
- docker run -d nginx:latest

- docker run -itd --name my_web nginx:latest

- docker container stop <container_id/name>
- docker container rm <container_id/name>
- docker container rm -f <container_id/name>
- docker exec <container_id> curl localhost
- docker exec -it <container_id> /bin/bash
- docker exec 9d5100a4a8e3 curl localhost
- docker exec -it 9d5100a4a8e3 /bin/bash
- docker run -idt -p 8080:80 --name game_2048 thuongnn1997/react-app:latest
- docker run nginx:latest
- docker ps -a

- docker container ls -a

- docker run -d nginx:latest

- docker run -itd --name my_web nginx:latest

- docker container stop 3f87137fcc28

- docker container rm -f 3f87137fcc28
- docker image load -i nginx.tar

- docker image save nginx:latest -o nginx.tar
  ----- docker basic ------

Production -
UAT -  
Staging / QA -
Development / Testing -

Scale -
High Availability -
Fault Tolerant -
Load balancer -

Podman
Trực tiếp server + Tools automation

Kubernetes + cri-o - containerd
artifact - tạo tác/ chế tác

Containerization

- CGroup: Giới hạn tài nguyên sử dụng: RAM, CPU, Storage
- Namespace: Cô lập cô lập trình

Docker Engine/Container Engine

Public ----------- Private

Container Registry

- Docker registry (no GUI) (free)
- Jfrog jcr (free)
- Harbor (free)
- Docker Hub Enterprise
- AWS, GCP, Azure
- Redhat, quay.io,....

alpine
slim
bust

docker pull <image_name>:<tag>
docker images
docker image ls
docker tag nginx:latest nginx:v10.0.0
docker image rm nginx:v10.0.0
docker image save nginx:latest -o nginx.tar
docker image load -i nginx.tar

docker run nginx:latest

docker ps -a
docker container ls -a
docker run -d nginx:latest

docker run -itd --name my_web nginx:latest

docker container stop <container_id/name>
docker container rm <container_id/name>
docker container rm -f <container_id/name>
docker exec <container_id> curl localhost
docker exec -it <container_id> /bin/bash
