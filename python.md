# 基础语法
## 参数
```python
def test(*arg,**args):
    print(arg)
    print("------------------------")
    print(args)
    
test(1,2,a=5,b=6)
# (1, 2)
# ------------------------
# {'a': 5, 'b': 6}
```
## 输出
```python
name = "Alice"
age = 25
print("My name is %s and I am %d years old." % (name, age))  # 使用 % 进行格式化
# My name is Alice and I am 25 years old.
data_i = "a"
name1 = "11"
text = "{%s}:{%s}" %(data_i,name1)
print(text)
# {a}:{11}
print("My name is {} and I am {} years old.".format(name, age))  # 使用 format() 方法进行格式化
# My name is Alice and I am 25 years old.
print(f"My name is {name} and I am {age} years old.")  # 使用 f-string 
# My name is Alice and I am 25 years old.
# \n \t \\ \' \" \r \b \v 
print("Hello,\nWorld!")
# Hello,
# World!
print("Name:\tAlice")
# Name:   Alice
print("This is a backslash: \\")
# This is a backslash: \
print("He said, \"Hello!\"")
# He said, "Hello!"
print('She\'s happy.')
# She's happy.
print("Hello\rWorld!")  # 输出后将光标移至行首
# World!
print("Hello\bWorld!")  # 输出后删除前一个字符
# HellWorld!
print("Hello\vWorld!")  # 输出后垂直制表符
# Hello
#      World!
```
## 路径
### sys
#### sys.path
python在模块导入过程中，解释器会使用sys.path变量来确定模块的搜索路径，包括当前工作目录、python安装目录
![image](https://github.com/YRH0/book/assets/74707759/b7c9b8db-8734-4ebd-a24c-dbd56d90d90d)
### os
#### os.environ
##### os.environ['PATH']
指定了可执行文件的搜索路径
#### os.getcwd()
获取的是工作目录的路径，调试时运行
```python
(/data1/conda_env/yrh_mtwxb) root@bit:/data1/yrh/trans/wxb_mechine_translation_nj# python machine_translation/test.py
/data1/yrh/trans/wxb_mechine_translation_nj
(/data1/conda_env/yrh_mtwxb) root@bit:/data1/yrh/trans/wxb_mechine_translation_nj/machine_translation# python test.py 
/data1/yrh/trans/wxb_mechine_translation_nj/machine_translation

```

# IDE使用
## vscode
### debug
    debug的原理是什么？
    程序员想要知道程序运行的某个状态，使用解释器/编译器运行程序，并在指定的步骤暂停，获取想要的信息。python解释器有CPython、IPython、PyPy、Jython，vscode的python插件使用环境默认解释器，python --version, Python 3.8.16, python官方默认使用cpython解释器。c++编译器有gcc、mingw、clang等
#### "purpose":["debug-in-terminal"]
    界面右上角的debug按钮是简单调试，不读launch.json文件，所以在launch.json中的任何配置都不生效，如果想要其读取launch.json配置，需要增加"purpose":["debug-in-terminal"]。
```python
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Python: 当前文件",
            "type": "python",
            "request": "launch",
            "program": "${file}",
            "console": "integratedTerminal",
            "justMyCode": false,
            "purpose":["debug-in-terminal"]
        }
    ]
}
```
    左上角是配置调试，会读取launch.json配置文件。
![image](https://github.com/YRH0/book/assets/74707759/4049235a-8c16-439b-b0c5-bdc226515bec)

