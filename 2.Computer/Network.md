# SSH协议
secure shell 22/tcp 替换传统的telnet协议
具体软件实现
OpenSSH:ssh协议的开源实现
SSH协议版本
●v1:基于CRC-32做MAC，不安全; man-in-middle
●v2:双方主机协议选择安全的MAC方式，基于DH算法做密钥交换，基于RSA或DSA实现身份认证
