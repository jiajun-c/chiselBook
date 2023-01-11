
# 变量/条件语句/函数

对于变量的声明可以使用val和var，我们应该尽量使用val去防止对变量的重复使用

```scala
val x = 1.U
```


## 1. 数据的类型

- bits 比特 后缀.B
- UInt 无符号整数 后缀.U
- SInt 有符号整数 后缀.S

>  SInt中当首位为1时表示负数，其数值等于对所有位取反然后+1


## 2. 条件语句

- if 语句

```scala
val likelyCharactersSet = if (alphabet.length == 26)
    "english"
else 
    "not english"

println(likelyCharactersSet)
```

- for 语句

```scala
for (i <- start to end) {
	
}
```

## 3. 函数

使用def进行声明

```scala
def func(param: <type>) :<return type> = {
	
}
```

