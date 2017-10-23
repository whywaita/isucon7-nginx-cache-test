# Nginx cache Test

Reproduction of [ISUCON7](http://isucon.net/archives/50949022.html) environment (Nginx deliver many images).

## Prepare

Get many images by Instagram, use [knok/instagram-food-images](https://github.com/knok/instagram-food-images).

```
$ cd icons
$ wget -i urllist_gyoza.txt --wait 60
```

modify index.html

```
$ ls icons/ | awk '{print "<br><img src=\"/icons/"$1"\">"}' > index.html
```

## Usage

```
$ docker run -it --rm --name nginx -v $(pwd):/usr/share/nginx/html -v $(pwd)/conf.d/:/etc/nginx/conf.d/ -v$(pwd)/nginx.conf:/etc/nginx/nginx.conf -p 8080:80 nginx:alpine
```
