# Nginx File Server

## Env

- Ubuntu 22.04.4 LTS aarch64

## Install nginx

```shell
sudo apt install nginx
```

## How to use

```shell
# create directory
sudo mkdir /nginx_files
sudo chmod 777 /nginx_files
sudo touch /nginx_files/{0..5}.txt

# download config
sudo wget -O /etc/nginx/sites-enabled/file_server.conf https://github.com/mingganglee/nginx_file_server/releases/download/v0.0.1-alpha/file_server.conf

# reload nginx config
sudo systemctl reload nginx
```

## Nginx operation

```shell
# check nginx settings
sudo nginx -t

# reload config
sudo systemctl reload nginx

# basic operation
sudo systemctl restart nginx
sudo systemctl start nginx
sudo systemctl stop nginx
```

## Upload file

```shell
# create test.txt file
echo "test" > test.txt

# upload file
curl -T test.txt http://localhost:8081/api/test.txt

# delete file
curl -X DELETE http://localhost:8081/api/test.txt

# download file ('-#' is a progress)
curl -O -# http://localhost:8081/api/test.txt
```
