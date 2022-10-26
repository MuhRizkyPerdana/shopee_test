# shopee_test
for test requiment shopee

Docker Define the project
1. git clone file from github
2. Create a docker-compose.yml file that starts your WordPress blog and a separate MySQL instance with 
3. code this code example, below
services:
  db:
    # We use a mariadb image which supports both amd64 & arm64 architecture
    image: mariadb:10.6.4-focal
    # If you really want to use MySQL, uncomment the following line
    #image: mysql:8.0.27
    command: '--default-authentication-plugin=mysql_native_password'
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      - MYSQL_ROOT_PASSWORD=somewordpress
      - MYSQL_DATABASE=wordpress
      - MYSQL_USER=wordpress
      - MYSQL_PASSWORD=wordpress
    expose:
      - 3306
      - 33060
  wordpress:
    image: wordpress:latest
    volumes:
      - wp_data:/var/www/html
    ports:
      - 80:80
    restart: always
    environment:
      - WORDPRESS_DB_HOST=db
      - WORDPRESS_DB_USER=wordpress
      - WORDPRESS_DB_PASSWORD=wordpress
      - WORDPRESS_DB_NAME=wordpress
volumes:
  db_data:
  wp_data:

Notes:
* The docker volumes db_data and wordpress_data persists updates made by WordPress to the database, as well as the installed themes and plugins. Learn more about docker volumes
* WordPress Multisite works only on ports 80 and 443.
Build the project
Now, run docker compose up -d from your project directory.
This runs docker compose up in detached mode, pulls the needed Docker images, and starts the wordpress and database containers, as shown in the example below.

4. docker compose up -d

that will be create

+] Running 5/5
 ⠿ Network shopee_test_default        Created                                                                        0.1s
 ⠿ Volume "shopee_test_wp_data"       Created                                                                        0.0s
 ⠿ Volume "shopee_test_db_data"       Created                                                                        0.1s
 ⠿ Container shopee_test-wordpress-1  Started                                                                        1.8s
 ⠿ Container shopee_test-db-1         Started                                                                        1.7s


5.Running Using Localhost port 8080, if u using docker gui, you can click docker running


5. After that signup wordpress and install

6.you can using


￼
￼
