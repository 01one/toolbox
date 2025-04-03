## Project Tree

```bash
.
├── docker-compose.yml
└── php.ini
```

### PHP Configuration (`php.ini`)

```ini
upload_max_filesize = 100M
post_max_size = 100M
memory_limit = 256M
max_execution_time = 300
```

### Docker Compose Configuration (`docker-compose.yml`)

```yaml
version: '3.8'

services:
  db:
    image: mysql:latest
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: your_root_password
      MYSQL_DATABASE: wordpress
      MYSQL_USER: your_username
      MYSQL_PASSWORD: your_password
    volumes:
      - dbdata:/var/lib/mysql
    networks:
      - backend

  wordpress:
    image: wordpress:latest
    depends_on:
      - db
    restart: always
    ports:
      - '9000:80'
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: your_username
      WORDPRESS_DB_PASSWORD: your_password
    volumes:
      - ./wordpress:/var/www/html
      - ./php.ini:/usr/local/etc/php/conf.d/custom.ini
    networks:
      - backend

volumes:
  dbdata:

networks:
  backend:
    driver: bridge
```

it will run on 127.0.0.1:9000 and available address


**Note:** Before setting your wordpress username and password, ensure that you do not make the server worldwide available without restriction. For testing, you can add Nginx htpassword and other security measures.
for local testing its okay.


