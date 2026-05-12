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














ĐÁNH GIÁ VÀ NHẬN XÉT HỆ THỐNG TRIỂN KHAI MÃ NGUỒN MỞ
1. Về hệ quản trị nội dung WordPress
Tính tiện dụng và trực quan: WordPress không chỉ là một CMS mã nguồn mở mạnh mẽ mà còn là một môi trường quản trị nội dung cực kỳ thân thiện. Sau khi hoàn tất thiết lập hạ tầng kỹ thuật, việc sản xuất nội dung — như bài viết giới thiệu ngành học tại TNUT — trở nên đơn giản hóa qua trình soạn thảo khối (Gutenberg). Điều này cho phép người dùng tập trung tối đa vào tư duy sáng tạo nội dung mà không bị rào cản bởi kỹ năng lập trình chuyên sâu.

Khả năng tùy biến đa phương tiện: Khả năng tích hợp linh hoạt các định dạng từ hình ảnh, âm thanh đến video nhúng (YouTube) giúp bài viết có chiều sâu, tính tương tác cao và chuyên nghiệp hơn hẳn so với các phương thức xây dựng web truyền thống.

2. Ưu thế khi triển khai trên nền tảng Docker
Quản trị tập trung: Thông qua công nghệ Docker Compose, việc điều phối và quản lý các dịch vụ tách biệt (MariaDB, phpMyAdmin, WordPress) được quy về một mối duy nhất. Điều này giúp hệ thống đạt được sự đồng bộ tuyệt đối.

Tính đóng gói và ổn định (Isolation): Docker giúp cô lập môi trường chạy ứng dụng, đảm bảo website hoạt động ổn định và không phát sinh xung đột với các tiến trình khác trên hệ điều hành Ubuntu. Đây là yếu tố then chốt giúp việc bảo trì và sao lưu (Backup) dữ liệu trở nên an toàn, nhanh chóng.

3. Phân tích hiệu năng và tài nguyên máy chủ
Hiệu suất thực tế: Qua quan sát, hệ thống duy trì mức tiêu thụ ổn định khoảng 500MB - 800MB RAM ở trạng thái nhàn rỗi. Mức chiếm dụng tài nguyên này hoàn toàn tối ưu đối với các dòng máy chủ ảo (VPS) hoặc máy ảo VMware phổ thông hiện nay.

Khả năng mở rộng: Cấu trúc này cho phép dễ dàng nâng cấp tài nguyên theo nhu cầu thực tế mà không cần cài đặt lại từ đầu, đảm bảo tính bền vững cho hệ thống lâu dài.

TỔNG KẾT & ĐÁNH GIÁ
Việc kết hợp giữa Docker, WordPress và Cloudflare Tunnel không chỉ là bài tập thực hành, mà còn là một giải pháp triển khai thực tế chuẩn quy trình DevOps hiện đại.

Mặc dù quá trình cài đặt ban đầu phát sinh nhiều thách thức về cấu hình tên miền, xác thực Token và phân quyền tệp tin, nhưng chính những "rào cản" đó đã giúp sinh viên củng cố kiến thức sâu sắc về:

          Cơ chế vận hành của Web Server và Database.

          Kỹ năng quản trị hệ thống Linux chuyên sâu.

          Tư duy xử lý mạng (Networking) và bảo mật trong môi trường Internet thực tế.






