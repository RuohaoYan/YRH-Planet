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

## 异常处理
```python
try:
    # 可能引发异常的代码
    pass
except ExceptionType:
    # 处理异常
    pass
else:
    # 在没有异常时执行的代码
    pass
finally:
    # 无论异常是否发生都执行的代码
    pass
```
### 意料之内的异常，可能是用户操作顺序不当或者其他原因，用于提醒用户正常操作
```python
try:
    dividend = int(input("请输入被除数："))
    divisor = int(input("请输入除数："))
    result = dividend / divisor
    print("结果：", result)
except ZeroDivisionError:
    print("除数不能为零！")
except ValueError:
    print("请输入有效的整数！")
except FileNotFoundError:
    print("文件不存在！")
except IndexError:
    print("索引超出范围！")
except KeyError:
    print("键不存在！")
```
### 捕获意料之外的异常并抛出
```python
def divide(dividend, divisor):
    if divisor == 0:
        raise ValueError("除数不能为零！")
    result = dividend / divisor
    return result

try:
    dividend = int(input("请输入被除数："))
    divisor = int(input("请输入除数："))
    result = divide(dividend, divisor)
    print("结果：", result)
except ValueError as e:
    raise ValueError("发生了一个异常：" + str(e))
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
    // 使用 IntelliSense 了解相关属性。 
    // 悬停以查看现有属性的描述。
    // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Python: Current File",
            "type": "python",
            "request": "launch",
            "program": "${file}",
            "console": "integratedTerminal",
            "cwd": "${workspaceFolder}",
            "justMyCode": false,
            "purpose":["debug-in-terminal"],
            "env": {
                "RABBITMQ_DEFAULT_USER": "username",
                "RABBITMQ_DEFAULT_PASS": "password",
                "MODEL_LOAD_LIST": "[\"1\",\"1\",\"0\",\"1\",\"0\",\"0\",\"0\",\"0\"]",
                "NVIDIA_VISIBLE_DEVICES": "all",
                "port": "10001",
                "BROKER_CONN_URI": "amqp://username:password@10.1.10.2:5672",
                "BACKEND_CONN_URI": "redis://10.1.10.2:6379/10",
                "REDIS_STORE_CONN_URI": "redis://10.1.10.2:6379/0",
                "CELERY_QUEUE_LIMIT": "100000",
                "CUDA_VISIBLE_DEVICES": "1",
                "PORT": "20002"
            },
        }
    ]
}
```
    左上角是配置调试，会读取launch.json配置文件。
![image](https://github.com/YRH0/book/assets/74707759/4049235a-8c16-439b-b0c5-bdc226515bec)

# 环境配置
## 迁移

# 漂亮的代码
```python
d221 = dict([[value, key] for key, value in d221.items()])
```
