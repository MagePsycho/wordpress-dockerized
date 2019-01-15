# Wordpress Dockerized [WIP]
Dockerized stack to run the wordpress projects in `LEMP` enviroment.

## Installation
```
# Download the tool
git clone git@github.com:MagePsycho/wordpress-dockerized.git
cd wordpress-dockerized

# Configure .env file
cp .env.dist .env

# Configure nginx virtual host
cp docker/etc/nginx/wordpress.conf.dist docker/etc/nginx/wordpress.conf
echo "127.0.0.1 wordpress.test" | sudo tee -a /etc/hosts

# Finally run the magic command
docker-compose up -d
```

This project use the following ports :

| Server     | Port |
|------------|------|
| MySQL      | 3036 |
| PHPMyAdmin | 8080 |
| Nginx      | 8000 |
