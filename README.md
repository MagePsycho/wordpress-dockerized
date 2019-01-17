# Wordpress Dockerized
Dockerized stack to run the wordpress projects in `LAMP` enviroment.

## Services
- [nginx-proxy](https://hub.docker.com/r/jwilder/nginx-proxy)
- [mysql](https://hub.docker.com/_/mysql)
- [wordpress](https://hub.docker.com/_/wordpress)
- [phpmyadmin](https://hub.docker.com/r/phpmyadmin/phpmyadmin)

## Installation
```
# Download the tool
git clone git@github.com:MagePsycho/wordpress-dockerized.git
cd wordpress-dockerized

# Configure .env file
# Change WP_HTTP_HOST & PMA_HTTP_HOST enviroment variables
cp .env.dist .env

# Configure nginx virtual host
echo "127.0.0.1 wordpress.test" | sudo tee -a /etc/hosts
echo "127.0.0.1 phpmyadmin.test" | sudo tee -a /etc/hosts

# Finally run the magic command
docker-compose up -d
```

## Connection:

| Server     | Default Port | Access URL|
|------------|------| -------------- |
| PHPMyAdmin | 8080 | http://wordpress.test |
| Nginx      | 8000 | http://phpmyadmin.test |


## Project Structure
```bash
.
├── app
├── data
│   ├── backups
│   └── mysql
├── docker
│   ├── bin
│   ├── build
│   └── etc
├── docker-compose.yml
├── logs
│   ├── mysql
│   ├── nginx
│   └── php-fpm

```

- `app` Folder for application, wordpress in this case.
- `data` MySQL data folder mapped with container
- `docker` docker-compose related custom builds & commands (Don't touch unless you know what you are doing)
- `logs` Web & App logs

## ToDos
- HTTPS support
- Custom LEMP + Wordpress
