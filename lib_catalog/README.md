Sequence of commands for task 2:

docker network create --driver bridge --subnet 192.168.100.0/24 --ip-range 192.168.100.0/24 my-bridge-network

docker run -d --name database --net my-bridge-network --ip=192.168.100.10 -e POSTGRES_USER=django -e POSTGRES_PASSWORD=django -e POSTGRES_NAME=django postgres:13

docker build -t backend .

docker run -d -p 8000:8000 --name api --net my-bridge-network --ip=192.168.100.11 backend