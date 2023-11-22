# vscode
## debug
```json
{
    "version": "0.2.0",
    "configurations": [
      {
        "name": "Fairseq Training",
        "type": "python",
        "request": "launch",
        // "program": "fairseq-train",
        "program": "${file}",
        "console": "integratedTerminal",
        "justMyCode": false,
        "args": [
          "/data1/2023/yrh/fairseq/data/bin",
          "--arch",
          "transformer",
          "-s",
          "ti",
          "-t",
          "zh",
          "--encoder-learned-pos",
          "--decoder-learned-pos",
          "--reset-optimizer",
          "--optimizer",
          "adam",
          "--adam-betas",
          "(0.9, 0.98)",
          "--clip-norm",
          "0.0",
          "--save-dir",
          "/data1/2023/yrh/fairseq/checkpoints",
          "--save-interval-updates",
          "2000",
          "--keep-interval-updates",
          "5",
          "--max-epoch",
          "2600",
          "--no-epoch-checkpoints",
          "--max-tokens",
          "10240",
          "--update-freq",
          "1",
          "--skip-invalid-size-inputs-valid-test",
          "--lr",
          "2e-5",
          "--lr-scheduler",
          "inverse_sqrt",
          "--dropout",
          "0.3",
          "--weight-decay",
          "0.0000",
          "--eval-bleu",
          "--eval-bleu-args",
          "{\"beam\": 5, \"max_len_a\": 1.2, \"max_len_b\": 10}",
          "--seed",
          "888",
          "--empty-cache-freq",
          "10",
          "--criterion",
          "label_smoothed_cross_entropy",
          "--label-smoothing",
          "0.1"
        ],
        "env": {
          "CUDA_VISIBLE_DEVICES": "4,5,6,7"
        },
        // "cwd": "${workspaceFolder}",
      }
    ]
}
```

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
## Xftp
![image](https://github.com/YRH0/YRH-Planet/assets/74707759/5cc42497-9e6e-417c-9e2b-dd629db3cb43)
![image](https://github.com/YRH0/YRH-Planet/assets/74707759/3c041066-a09a-4bbf-9f27-384dfab5c811)



# tar
```shell
tar zcvf - file_name |split -b 4096m - file_name.tar.gz
```
 

# xshell
## 多级跳转
![image](https://github.com/YRH0/YRH-Planet/assets/74707759/110a4af6-d18e-41ea-bce8-c7df37308e06)
