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
![image](https://github.com/YRH0/YRH-Planet/assets/74707759/5aa7ba83-25fb-4c52-a65c-ffa9ab16a4c0)
![image](https://github.com/YRH0/YRH-Planet/assets/74707759/6965ad72-3678-4a24-b379-d039f336c31a)



# tar
```shell
tar zcvf - file_name |split -b 4096m - file_name.tar.gz
```
 

# xshell
## 多级跳转
![image](https://github.com/YRH0/YRH-Planet/assets/74707759/110a4af6-d18e-41ea-bce8-c7df37308e06)


# git
当年Linus创建了开源的Linux，从此，Linux系统不断发展，现在已经成为最大的服务器系统软件了。(请不要傻傻分不清Linus和Linux但是随着Linux的不断壮大，就需要各种版本控制了，起初Linus带着他的小弟们使用的是BitKeeper(商业版本控制系统),之后呢由于某种原因BitKeeper的公司不让他们使用了，于是Linus自己花了两周时间写出了Git并且开源了。Linus Torvalds说 "a rotten person", he said. "I'm an egotistical bastard, so I name all my projects after myself. First Linux, now git" 没错，git英语俚语意思是蠢货，自以为是且好辩的人。


## Github
Git和Github：很多人说git是版本控制器，github是仓库，其实现在的github具有版本控制功能，我觉得GitHub是一个基于Git的代码托管平台，它使用Git作为底层的版本控制系统，已经包含了git。
**本地仓库区**：指存储在本地计算机上的Git版本库，包含了完整的项目历史记录和元数据信息，可以在本地仓库中进行提交、分支操作和版本控制。
{**工作区（Working Directory）**：包含实际的项目文件，在电脑上进行编辑和修改。
**暂存区（Staging Area/Index）**：暂存区相当于一个缓冲区，用于暂时存放将要提交的更改，在工作区中修改文件后，可以使用git add命令将更改添加到暂存区。
**版本库（Repository）**：包含了项目的完整历史记录和元数据，通常位于项目目录中的.git文件夹中，包括了暂存区、分支、提交记录、标签等信息，通过版本库，您可以查看历史记录、回滚更改、创建分支等操作。}
电脑上的工作目录
**远程仓库**：云端


### 配置ssh 打通机器与Github
1、检查密钥是否连通，否进入2、，
```shell
Host YRH0  # 域名的代称
    HostName github.com
    User git
    PreferredAuthentications publickey   # 指定首选的身份验证方法。在这种情况下，设置为 "publickey"，表示将使用SSH公钥身份验证。
    IdentityFile ~/.ssh/yrhGit
    ServerAliveInterval 30
```
配置~/.ssh/config 文件，目的是使计算机在运行ssh服务连接指定域名时知道应该使用哪个密钥

```python
ssh -T Host # Host = user@HostName
```

2、生成密钥
```shell
ssh-keygen -f ~/.ssh/id_rsa_xj_3090_2 -t rsa -C 邮箱
```
-f 参数表示指定密钥对生成位置与名称
密钥对通常放在 ~/.ssh 目录下
回车即可创建密钥对，需要输入密码如果不需要为密钥对进行加密，那么可以一路回车。
**邮箱与git邮箱要一致，github会验证邮箱**

3、在github中加入公钥（.pub文件）
点击图像，选择setting，选择SSH and GPG keys，增加new ssh keys
```shell
cat .pub # 剪切公钥的内容并复制粘贴到new ssh keys中
```

4、
```python
cd ~/.ssh # 进入ssh目录
vi config
```

5、重复1、，判断是否连接成功

6、下载项目
```shell
git clone YRH0:YRH0/k-translation.git
```

7、git push YRH0:YRH0/tools_yrh.git


### 初始化git操作
```powershell
git clone https://github.com/xxxxx
git clone 项目地址 # 克隆git项目
git clone -b thresCal git@github.com:xxxxx
git clone -b 分支名 分支仓库地址 # clone指定分支
git init
```

### 提交代码
```powershell
git add.  # 将目录下的文件全部添加到缓存区
git commit -m 提交信息  # 提交信息指修改表示，便于后期分辨
git push
git pull origin master --allow-unrelated-histories # 允许不相关历史提交，--allow-unrelated-histories强制合并
git push --force origin master # 强制提交
```

### 操作远程仓库
```powershell
git remote # 查看有哪些远程仓库
git remote -v / git remote show origin # 查看仓库地址
git remote remove origin # 删除远程仓库
git remote add origin xxx # 增加远程仓库xxx(链接)命名为origin
git push --set-upstream origin master # 关联本地分支与远程分支 origin指向远程仓库标签 master 远程仓库分支
git push -u origin master # 把本地仓库push到github上master分支
git remote remove orign # 删除orign仓库
```

### 子仓库
```powershell
git submodule add ...(仓库B的地址，即git clone时后面那串东西)
```

### 获取远程仓库最新代码
```powershell
方法①
git pull origin master:brantest
# 将远程主机 origin 的 master 分支拉取过来，与本地的 brantest 分支合并。
方法②
git fetch
# 更新代码
git merge
# 合并
```
git pull 与 git fetch + get merge 的区别 :
		git分为本地仓库和远程仓库，流程 写完代码 -> commit本地仓库（生成本地仓的commit ID，代表当前提交代码的版本号）-> push到远程仓库（记录这个版本号）。本地的git文件夹中对应存储了 git本地仓库master分支的commit ID、跟踪的远程分支orign/master的commit ID（.git/refs/head/[本地分支]、.git/refs/head/[本地分支]）。假设我们本地仓库的 master 分支上 commit ID =1 ，orign/mastter中的commit ID =1 ，这时候远程仓库有人更新了github ogirn库中master分支上的代码，新的代码版本号commit ID =2 ,那么在github上 orign/master的commitID=2，然后我们要更新代码。
		git fetch更新代码，本地的库中master的commitID不变，还是等于1。但是与git上面关联的那个orign/master的commit ID变成了2。这时候我们本地相当于存储了两个代码的版本号，我们还要通过merge去合并这两个不同的代码版本，如果这两个版本都修改了同一处的代码，这时候merge就会出现冲突，然后我们解决冲突之后就生成了一个新的代码版本。这时候本地的代码版本可能就变成了commit ID=3，即生成了一个新的代码版本。相当于fetch的时候本地的master没有变化，但是与远程仓关联的那个版本号被更新了，我们接下来就是在本地合并这两个版本号的代码。
		使用git pull的会将本地的代码更新至远程仓库里面最新的代码版本。
		**不要用git pull，用git fetch和git merge代替它。**
git pull的问题是它把过程的细节都隐藏了起来，以至于你不用去了解git中各种类型分支的区别和使用方法。当然，多数时候这是没问题的，但一旦代码有问题，你很难找到出错的地方。看起来git pull的用法会使你吃惊，简单看一下git的使用文档应该就能说服你。
		将下载（fetch）和合并（merge）放到一个命令里的另外一个弊端是，你的本地工作目录在未经确认的情况下就会被远程分支更新。当然，除非你关闭所有的安全选项，否则git pull在你本地工作目录还不至于造成不可挽回的损失，但很多时候我们宁愿做的慢一些，也不愿意返工重来。
### 分支操作
```powershell
git branch -r
# 查看远程分支
git push origin :[branch name]
# 删除github远程分支
git branch -a
# 查看所有分支
git branch
# 查看本地分支
git branch [branch name]
# 新建本地分支
git branch -d [branch name]
# 删除本地分支
git checkout [branch name]
# 切换新的分支
git push origin [branch name]
# 推送新分支到github
```
### 缓冲区文件操作
```powershell
git ls-files 
# 该命令输出在缓冲区中缓存的所有文件
git ls-files | grep test.data 
#找我保存的文件
git rm --cached your-file-name  
# 删除缓冲区中文件
git clean -f 
# 删除untracked文件
git clean -fd 
# 删除untracked目录
git clean -xfd 
# 连 gitignore 的untrack 文件/目录也一起删掉 （慎用，一般这个是用来删掉编译出来的 .o之类的文件用的）
```
### 忽略提交数据
```powershell
# 创建.gitingore文件
vi .gitingore
```
.gitingore未生效？
把某些目录或文件加入忽略规则，发现并未生效，原因是.gitignore只能忽略那些原来没有被track的文件，如果某些文件已经被纳入了版本管理中，则修改.gitignore是无效的。那么解决方法就是先把本地缓存删除（改变成未track状态），然后再提交
```bash
git rm -r --cached .
```
.gitingore中语法规则
空格不匹配任意文件，可作为分隔符，可用反斜杠转义
开头的文件标识注释，可以使用反斜杠进行转义
! 开头的模式标识否定，该文件将会再次被包含，如果排除了该文件的父级目录，则使用 ! 也不会再次被包含。可以使用反斜杠进行转义
/ 结束的模式只匹配文件夹以及在该文件夹路径下的内容，但是不匹配该文件
/ 开始的模式匹配项目跟目录
如果一个模式不包含斜杠，则它匹配相对于当前 .gitignore 文件路径的内容，如果该模式不在 .gitignore 文件中，则相对于项目根目录
** 匹配多级目录，可在开始，中间，结束
? 通用匹配单个字符
* 通用匹配零个或多个字符
[] 通用匹配单个字符列表
实例
```powershell
bert-base-chinese-pytorch_model ：忽略文件夹
twoThresCal.log ：忽略文件
__pycache__/SegmentBERT.cpython-38.pyc ：忽略文件夹下的文件
bin/: 忽略当前路径下的bin文件夹，该文件夹下的所有内容都会被忽略，不忽略 bin 文件
/bin: 忽略根目录下的bin文件
/*.c: 忽略 cat.c，不忽略 build/cat.c
debug/*.obj: 忽略 debug/io.obj，不忽略 debug/common/io.obj 和 tools/debug/io.obj
**/foo: 忽略/foo, a/foo, a/b/foo等
a/**/b: 忽略a/b, a/x/b, a/x/y/b等
!/bin/run.sh: 不忽略 bin 目录下的 run.sh 文件
*.log: 忽略所有 .log 文件
config.php: 忽略当前路径的 config.php 文件
```
### 遇到的问题
 1. push时修改暂存区没用？
copy时将.git文件也copy过来了，删除就好
 2. fatal: Not a git repository?
是找不到.git目录的原因
```powershell
 git init 
```
 3. ERROR: Repository not found. fatal: Could not read from remote repository.?
将SSH key 添加到 ssh-agent
```powershell
ssh-add ~/.ssh/id_rsa
# 如果出现Could not open a connection to your authentication agent
ssh-agent bash
```
配置Github账户，通过vi将id_ras.pub的内容复制到github中
验证key
```powershell
ssh -T git@github.com 
```
不行就重新生成ssh key，https://blog.csdn.net/qq_36372569?type=blog

