# Linux

查看GPU使用情况
watch -n 10 nvidia-smi
查看服务器GPU内存使用情况 - 知乎 (zhihu.com)

Permission denied
chmod +x ./Tools/conlleval
压缩解压命令
# 仅打包，并非压缩
tar -xvf FileName.tar         # 解包
tar -cvf FileName.tar DirName # 将DirName和其下所有文件（夹）打包
python命令
-u
查看版本
cat /proc/version
Linux version 4.15.0-112-generic (buildd@lcy01-amd64-027) (gcc version 7.5.0 (Ubuntu 7.5.0-3ubuntu1~18.04)) #113-Ubuntu SMP Thu Jul 9 23:41:39 UTC 2020

发送接受文件

接收：sz

删除文件
rm -r -f * 
删除所有文件

运行命令
nohup sh run_train_p.sh &
tail -f nohup.out

查看大文本
less +G -n nohup.out 直达底部

(2条消息) Linux中查看进程状态信息_IT之旅 的博客-CSDN博客_linux 查看进程信息

拷贝命令
1.cp命令
命令：cp dir1/a.doc dir2 表示将dir1下的a.doc文件复制到dir2目录下
cp -r dir1 dir2 表示将dir1及其dir1下所包含的文件复制到dir2下
cp -r dir1/. dir2 表示将dir1下的文件复制到dir2,不包括dir1目录
说明：cp参数 -i：询问，如果目标文件已经存在，则会询问是否覆盖；
2.scp命令
例如：scp id_rsa.pub router_17@IP:/home/router_17/.ssh/authorized_keys可以实现将A电脑上的pub文件拷贝到B电脑上某个位置。同cp一样，如果复制的是整个文件夹的内容，则应使用scp -r 命令。

