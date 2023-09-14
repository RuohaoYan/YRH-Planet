docker run -i 17df19ea8201
docker exec -it ddc1eb732b02 /bin/bash
# dockerfile
docker build  -f celery.dockerfile -t celerytrans:0.0.1 .

 -f Dockerfile 文件的位置
 --tag, -t: 镜像的名字及标签，通常 name:tag 或者 name 格式；可以在一次构建中为一个镜像设置多个标签。
