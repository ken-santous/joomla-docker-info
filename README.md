```sh
# joomla-docker-info
joomla-docker-info
apt-get update
apt-get install docker.io
docker network create joomla-network
docker pull mysql
docker pull joomla
docker images
docker volume create mysql-data
docker volume inspect mysql-data
sudo ln -s /var/lib/docker/volumes/mysql-data/_data /mysql

sudo docker run -d --name joomladb  -v mysql-data:/var/lib/mysql --network joomla-network -e "MYSQL_ROOT_PASSWORD=cairo1234" -e MYSQL_USER=joomla -e "MYSQL_PASSWORD=cairo1234" -e "MYSQL_DATABASE=joomla" mysql

docker volume create joomla-data
docker volume inspect joomla-data

sudo ln -s /var/lib/docker/volumes/joomla-data/_data /joomla

sudo docker run -d --name joomla -p 8081:80 -v joomla-data:/var/www/html --network joomla-network -e JOOMLA_DB_HOST=joomladb -e JOOMLA_DB_USER=joomla -e JOOMLA_DB_PASSWORD=kamisama123 joomla

http://localhost:8081

• Database type - MySQLi
• Hostname - joomladb
• Username - joomla
• Password - cairo1234
• Database - joomla

docker ps -a
docker ps -a -f name=joomla
docker ps -a -f name=joomladb
docker container stop joomla
docker container stop joomladb
docker container start joomla
docker container start joomladb
docker logs joomla
docker logs joomladb

```
