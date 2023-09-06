# 基础语法
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

# IDE使用
## vscode
1. JustMyCode设置无用，launch增加"purpose":["debug-in-terminal"]
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
