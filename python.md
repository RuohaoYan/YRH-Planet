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
