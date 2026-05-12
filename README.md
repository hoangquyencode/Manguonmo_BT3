# Manguonmo_BT3

# SỬ DỤNG WORDPRESS ĐỂ TẠO WEB SITE
deadline : 23h59 ngày 12 tháng 5 năm 2026.



SSH và máy ảo
Tạo file: mkdir wordpress_project
          cd wordpress_project







<img width="1374" height="741" alt="image" src="https://github.com/user-attachments/assets/b96788af-b2fd-40d4-8777-848a8e2f1507" />







<img width="1137" height="836" alt="image" src="https://github.com/user-attachments/assets/d3dd904b-cabd-4242-95db-223952ea76e3" />



# tạo file docker-compose.yml


services:
  db:
    image: mariadb:10.11
    container_name: wp_db_new
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: root_password_day_ne
      MYSQL_DATABASE: wordpress_db
      MYSQL_USER: wp_user
      MYSQL_PASSWORD: wp_password
    volumes:
      - db_data_new:/var/lib/mysql
    networks:
      - wp_net_new

  wordpress:
    image: wordpress:latest
    container_name: wp_app_new
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wp_user
      WORDPRESS_DB_PASSWORD: wp_password
      WORDPRESS_DB_NAME: wordpress_db
      WORDPRESS_CONFIG_EXTRA: |
        define('WP_HOME','https://wordpress.quyenmebechip.io.vn');
        define('WP_SITEURL','https://wordpress.quyenmebechip.io.vn');
        define('FORCE_SSL_ADMIN', true);
    depends_on:
      - db
    volumes:
      - wp_data_new:/var/www/html
    networks:
      - wp_net_new

  cloudflared:
    image: cloudflare/cloudflared:latest
    container_name: wp_tunnel_new
    restart: always
    command: tunnel --no-autoupdate run
    environment:
      TUNNEL_TOKEN: eyJhIjoiN2VkNjdjMDFhZjE2NDgxMTY0MzIwY2I3ODIyZjgzYzgiLCJ0IjoiNjIwOWU1YzctZTNiYy00OTAxLTg1OWUtNmVjNDg3NTUzMzRiIiwicyI6IllXUXhPR0psT0RVdFpqUXdOQzAwWWpZeUxUaGlPVGN0TUdaaU4yTmlaRGxoT1dGbSJ9
    networks:
      - wp_net_new

volumes:
  db_data_new:
  wp_data_new:

networks:
  wp_net_new:




  Lấy ip và vào wordPress





  

<img width="1900" height="966" alt="image" src="https://github.com/user-attachments/assets/0bd93e40-f8d2-40a2-bbc7-c52ba86d748f" />











<img width="1851" height="896" alt="image" src="https://github.com/user-attachments/assets/f2b961dd-49ec-4e62-b911-79ec9bfd0f86" />








<img width="1100" height="674" alt="image" src="https://github.com/user-attachments/assets/6df61426-d2e6-4d5a-a85a-35e843ee4e0f" />









<img width="1527" height="694" alt="image" src="https://github.com/user-attachments/assets/4acffcc6-14a9-4218-8aff-73e4324e91b8" />











<img width="1153" height="380" alt="image" src="https://github.com/user-attachments/assets/adfcd9a3-9f04-459e-8667-46ccd899d3a0" />




<img width="1242" height="660" alt="image" src="https://github.com/user-attachments/assets/ae82d5b3-cb30-44b6-9ed4-7253f2ccc538" />






<img width="917" height="825" alt="image" src="https://github.com/user-attachments/assets/2a9e877d-b23a-4433-aee7-bf02601ddfdb" />








<img width="1869" height="1080" alt="image" src="https://github.com/user-attachments/assets/c3c52037-aa16-4ba3-beac-76c2c51f3e4b" />
