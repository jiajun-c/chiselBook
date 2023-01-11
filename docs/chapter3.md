# Module

## 1. demo

和verilog一样，如果要生成一个组件，那么需要使用Module进行包装

```scala
class MyModule extends Module {
	
}
```

## 2. IO

使用IO创建我们的输入和输出,使用Input/Output分别表示输入输出

```scala
  val io = IO(new Bundle{
    val in = Input(UInt(2.W))
    val out = Output(UInt(2.W))
  })
```

## 3. 参数传递

在创建类的时候可以为类添加参数
```scala

```


