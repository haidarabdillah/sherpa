Requirement :

1. Docker (installation flow : )
2. Docker Compose (Installation flow : )
3. Cloudflare pem and key  
4. Explorer v1 database backup (or use this <http://45.151.123.106:7979/blockscout1.sql>)
5. upload public logo and icon sample is here :
NEXT_PUBLIC_NETWORK_LOGO=<http://res.cloudinary.com/dwzzq7hyf/image/upload/v1701446927/tihx8dkhsb27krvvv18r.png>
NEXT_PUBLIC_NETWORK_ICON=<http://res.cloudinary.com/dwzzq7hyf/image/upload/v1701446234/je2pbkayzispor92dtzq.svg>

Installation step :

1. make new folder on proxy with your domain name
2. add certificate.crt and private.key
3. change domain on proxy/default.conf.template to your domain
4. run container with this command `docker-compose up -d`
5. stop container compose with this comman `docker-compose stop`
6. now run the DB container with command `docker-compose up -d db`
7. restore database with this command `cat /blockscout1.sql | docker exec -i -e PGPASSWORD=ceWb1MeLBEeOIfk65gU8EjF8 container_id psql -U blockscout -d blockscout`, remember to change container_id to your container_image_id of db , you can type `docker ps` you will see the container id
8. wait restore db completely, then restart container by command `docker-compose up -d`
