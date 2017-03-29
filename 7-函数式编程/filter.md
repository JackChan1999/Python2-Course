Python内建的`filter()`函数用于过滤序列。

和`map()`类似，`filter()`也接收一个函数和一个序列。和`map()`不同的时，`filter()`把传入的函数依次作用于每个元素，然后根据返回值是`True`还是`False`决定保留还是丢弃该元素。

例如，在一个list中，删掉偶数，只保留奇数，可以这么写：

```
def is_odd(n):
    return n % 2 == 1

filter(is_odd, [1, 2, 4, 5, 6, 9, 10, 15])
# 结果: [1, 5, 9, 15]

```

把一个序列中的空字符串删掉，可以这么写：

```
def not_empty(s):
    return s and s.strip()

filter(not_empty, ['A', '', 'B', None, 'C', '  '])
# 结果: ['A', 'B', 'C']

```

可见用`filter()`这个高阶函数，关键在于正确实现一个“筛选”函数。

### 练习

请尝试用`filter()`删除1~100的素数。