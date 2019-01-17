# Wordpress Dockerized
Dockerized stack to run the wordpress projects in `LAMP` environment.

## Services
- [nginx-proxy](https://hub.docker.com/r/jwilder/nginx-proxy)
- [mysql](https://hub.docker.com/_/mysql)
- [wordpress](https://hub.docker.com/_/wordpress)
- [phpmyadmin](https://hub.docker.com/r/phpmyadmin/phpmyadmin)

## Installation
### Download  
```
git clone git@github.com:MagePsycho/wordpress-dockerized.git
```

### Configure  
Prepare the environment setting file 
```
cd wordpress-dockerized
cp .env.dist .env
```

Configure the environment variables only if you want to change the default host, port etc.:
- `WP_HTTP_HOST` Wordpress Domain, Default: wordpress.test
- `PMA_HTTP_HOST` PhpMyAdmin Domain, Default: phpmyadmin.test
- etc.

Add entries in `/etc/hosts`
```
echo "127.0.0.1 wordpress.test" | sudo tee -a /etc/hosts
echo "127.0.0.1 phpmyadmin.test" | sudo tee -a /etc/hosts
```

### Containerize  
Create a unique network for `nginx-proxy` and other Docker containers to communicate through.
```
docker network create nginx-proxy
```

Finally run the magic command
```
docker-compose up -d
```

All the services must be running. You can check via:
```
docker ps -a
```
Now you can open the Wordpress & PHPMyAdmin site(see `Connection` section for URLs).

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
