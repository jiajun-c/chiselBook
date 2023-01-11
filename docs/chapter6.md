
# 时序逻辑

在数字电路中，我们经常需要编写时序逻辑去处理一些问题，比如两位饱和分支预测器或者更简单的，一个计数器(下面我们就用一个计数器作为栗子)

```scala
class seq extends Module {
	val io = IO(new Bundle {
		val out = Output(UInt(3.W))
	})
	val count = RegInit(0.U(3.W))
	count := count + 1.U
	io.out := count
}
```

下面补充介绍一下寄存器

## 寄存器相关

- RegInit 使用一个数值初始化一个寄存器
- RegNext 将传入的数值作为寄存器的下一个状态

下面是一个使用寄存器进行移位运算

```scala
class shift(val init:Int = 1) extends Module {
	val io = new Bundle {
		val in = Input(Bool())
		val out = Output(UInt(4.W))
	}
	val state = RegInit(0.U(4.W))
	val nextState = (state << 1)|io.in
	state := nextState
	io.out := state
}
```





