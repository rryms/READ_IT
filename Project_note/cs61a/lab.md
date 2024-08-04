# 写题的算法

![interesting_Web](https://giancarlo-ma.github.io/categories/CS61A/)



python逻辑判断：
``or``\``and`` ``isnot``
``&  with | `` 成了位运算。



## Recusion
[code](./homework/hw02/hw02.py)
basic case 可以很“复杂”.计算机仅保证你这么思考，会得到这样的结果。

重要的：观察父子递归中间的关系，甚至可以创造参数通过记录关系通关

**Towers of Hanoi**
```python
def move_disk(disk_number, form_peg, to_peg):
    print("Move disk" + str(disk_number)+"from peg" + str(from_peg)+ "to peg" + str(to_peg)+".")


def solve_hanoi(n,start)
```

## lab04---Recursion, Tree Recursion, Python Lists
```py
def recursion():
    if small cases:
        return the result
    else :
        return recursion(for_a_partition)
```
also for string cases