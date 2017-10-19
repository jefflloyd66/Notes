Setup docker-compose entry for latest MySql

version: '2'
services:

database:
  image: mysql:latest
  volumes:
    - dbdata:/var/lib/mysql
  environment:
    - "MYSQL_DATABASE=homestead"
    - "MYSQL_USER=homestead"
    - "MYSQL_PASSWORD=secret"
    - "MYSQL_ROOT_PASSWORD=root"
  ports:
      - "33061:3306"

volumes:
  dbdata:
