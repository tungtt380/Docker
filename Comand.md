docker pull ubuntu

Run ubuntu from image
docker run -it ubuntu

attach container
docker attach CONTAINER_ID

Stop container
docker stop conatainerId

Show process
docker ps -a
Ctr+P+Q Exit ubuntu

docker images: Liệt kê các images hiện có

docker rmi {image_id/name}: Xóa một image

docker ps: Liệt kê các container đang chạy

docker ps -a: Liệt kê các container đã tắt

docker rm -f {container_id/name}: Xóa một container

docker start {new_container_name}: Khởi động một container

docker exec -it {new_container_name} /bin/bash: Truy cập vào container đang chạy

start docker service
$ sudo systemctl start docker 

auto start docker service when boot
$ sudo systemctl enable docker

## Firewall ##
https://www.cyberciti.biz/faq/how-to-set-up-a-firewall-using-firewalld-on-centos-8/

## Cockpit ##
https://www.cyberciti.biz/faq/install-activate-cockpit-the-web-console-on-rhel-8/
