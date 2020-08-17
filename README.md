# Docker Template

This repository contains a Docker template for local webdevelopment using Apache, PHP 7.4 and MySQL.

## MySQL port

Make sure to map MySQL port 3306 to a unique port number for each project to be able to access the database using your preferred GUI. In the example file, port 3306 is mapped to port 3307.

## NGINX proxy

The template makes use of a network named nginx-proxy to map `{PROJECT_NAME}.test` to 127.0.0.1.

```bash
docker network create nginx-proxy

docker run -d -p 80:80 --net nginx-proxy -v /var/run/docker.sock:/tmp/docker.sock jwilder/nginx-proxy --name nginx_proxy --restart always
```

More information about running the nginx-proxy container is described on https://medium.com/@juan_cortes/local-domains-through-nginx-proxy-and-docker-13d97ee8c010.

You can add `{PROJECT_NAME}.test` to your hosts file or use dnsmasq to map all \*.test domains to 127.0.0.1

## Usage

Add these files to the root of your project, replace `{PROJECT_NAME}` with your project name and run `docker-compose up -d` to start the containers. Opening `{PROJECT_NAME}.test` in your preferred browser should now show a `phpinfo()` screen.

## Volumes

All MySQL data will be stored in the `./docker/data/mysql` directory relative to the project root.
