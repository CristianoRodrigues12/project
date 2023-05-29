version: '3.9'
services:
  nginx:
    image: nginx:latest
    container_name: my-nginx-app
    ports:
      - '8080:80'
    volumes:
      - ./website:/usr/share/nginx/html
    networks:
      - my-network

  mysql:
    image: mysql:latest
    container_name: my-mysql-db
    ports:
      - '3306:3306'
    environment:
      - MYSQL_ROOT_PASSWORD=mysecretpassword
      - MYSQL_DATABASE=mydatabase
      - MYSQL_USER=myuser
      - MYSQL_PASSWORD=mypassword
    volumes:
      - ./db_data:/var/lib/mysql
    networks:
      - my-network

networks:
  my-network:
