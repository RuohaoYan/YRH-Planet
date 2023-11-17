# ftp
## 连接ftp服务器
1、默认端口
```shell
ftp 192.168.1.1
```
2、指定端口
```shell
ftp -P 8036 192.168.1.1
```
## 下载文件(进入指定目录，或在命令中指定目录)
```shell
下载一个
get /usr/your/1.htm 1.htm (回车)
批量下载
mget *.* (回车)
```
## 上传文件(进入指定目录，或在命令中指定目录)
```shell
上传一个
put 1.htm
批量上传
mput *.htm　（回车）
```
# tar
```shell
tar zcvf - file_name |split -b 4096m - file_name.tar.gz
```
