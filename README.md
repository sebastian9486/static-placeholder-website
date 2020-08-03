# static-placeholder-website
Simple static website for AWS and Docker experiments served using an Nginx container inside Docker. The code for the site is contained in `index.html`, and the Nginx config is in `default.conf`.

To build a Docker image from the Dockerfile:

```sh
$ docker build -t sebastian9486/static-placeholder-website:1.0 .
```

Run the image in a Docker container:
```sh
$ docker run -itd --name static-placeholder-website --publish 80:80 sebastian9486/static-placeholder-website:1.0
```

Stop container:
```sh
$ docker stop static-placeholder-website
```

Delete container:
```sh
$ docker rm static-placeholder-website
```
