# Manguonmo_BT3

# SỬ DỤNG WORDPRESS ĐỂ TẠO WEB SITE
deadline : 23h59 ngày 12 tháng 5 năm 2026.



SSH và máy ảo
Tạo file: mkdir wordpress_project
          cd wordpress_project







<img width="1374" height="741" alt="image" src="https://github.com/user-attachments/assets/b96788af-b2fd-40d4-8777-848a8e2f1507" />










# tạo file docker-compose.yml


services:
  db:
    image: mariadb:latest
    container_name: mariadb_db
    restart: always

    environment:
      MYSQL_ROOT_PASSWORD: root_password_day_ne
      MYSQL_DATABASE: wordpress_db
      MYSQL_USER: wp_user
      MYSQL_PASSWORD: wp_password

    volumes:
      - db_data:/var/lib/mysql

  phpmyadmin:
    image: phpmyadmin:latest
    container_name: phpmyadmin_ui
    restart: always

    ports:
      - "8081:80"

    environment:
      PMA_HOST: db

    depends_on:
      - db

  wordpress:
    image: wordpress:latest
    container_name: wordpress_site
    restart: always

    ports:
      - "8001:80"

    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wp_user
      WORDPRESS_DB_PASSWORD: wp_password
      WORDPRESS_DB_NAME: wordpress_db

    depends_on:
      - db

    volumes:
      - wp_data:/var/www/html

volumes:
  db_data:
  wp_data:





  Lấy ip và vào wordPress





  

<img width="1900" height="966" alt="image" src="https://github.com/user-attachments/assets/0bd93e40-f8d2-40a2-bbc7-c52ba86d748f" />











<img width="1851" height="896" alt="image" src="https://github.com/user-attachments/assets/f2b961dd-49ec-4e62-b911-79ec9bfd0f86" />








<img width="1100" height="674" alt="image" src="https://github.com/user-attachments/assets/6df61426-d2e6-4d5a-a85a-35e843ee4e0f" />









<img width="1527" height="694" alt="image" src="https://github.com/user-attachments/assets/4acffcc6-14a9-4218-8aff-73e4324e91b8" />











<img width="1153" height="380" alt="image" src="https://github.com/user-attachments/assets/adfcd9a3-9f04-459e-8667-46ccd899d3a0" />




<img width="917" height="825" alt="image" src="https://github.com/user-attachments/assets/2a9e877d-b23a-4433-aee7-bf02601ddfdb" />






<img width="1242" height="660" alt="image" src="https://github.com/user-attachments/assets/bf304372-5a84-4dff-912a-30da79a78dd1" />






<img width="1082" height="223" alt="image" src="https://github.com/user-attachments/assets/6322eef1-59a3-4632-833b-ac20a7e6f87b" />

