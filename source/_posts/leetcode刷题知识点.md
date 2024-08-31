# leetcode刷题知识点

## 列表如何整体进行加减运算？

### 方法一：使用列表推导式

```python
original_list = [10, 20, 30, 40, 50]
value_to_subtract = 5

new_list = [x - value_to_subtract for x in original_list]
print(new_list)
```



### 方法二：使用`map`函数

```python
original_list = [10, 20, 30, 40, 50]
value_to_subtract = 5

new_list = list(map(lambda x: x - value_to_subtract, original_list))
print(new_list)
```

## 往复运动=边界条件+step变量


```python
def convert(self, s: str, numRows: int) -> str:
    if numRows == 1 or numRows >= len(s):
        return s

    ans = [''] * numRows
    index, step = 0, 1

    for char in s:
        ans[index] += char
        if index == 0:
            step = 1
        elif index == numRows - 1:
            step = -1
        index += step

    return ''.join(ans)
```

## zip函数的使用
```python
list1 = [1, 2, 3, 4]
list2 = ['a', 'b', 'c']
zipped = zip(list1, list2)

print(list(zipped))  # 输出: [(1, 'a'), (2, 'b'), (3, 'c')]
```

## 列表逆序

```python
# 示例列表
words = ["apple", "banana", "cherry"]

# 方法一：使用 reversed 函数
reversed_words = reversed(words)
result = ' '.join(reversed_words)
print(result)  # 输出: cherry banana apple

# 方法二：使用切片操作
reversed_words = words[::-1]
result = ' '.join(reversed_words)
print(result)  # 输出: cherry banana apple
```

## KMP算法

