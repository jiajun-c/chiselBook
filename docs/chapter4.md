
# 基础运算

chisel中支持基础的运算比如加减乘除位运算等

> 无法对一个chisel中的类型和非chisel中的类型进行算术运算，比如1.U + 1

```scala
package operator
import chisel3._
class op extends Module {
	val io = IO(new Bundle {
		val in1 = Input(UInt(3.W))
		val in2 = Input(UInt(3.W))
		val out = Output(UInt(3.W))
	})

	io.out := io.in1 + io.in2
}
```

下面是chisel的cheatSheet

![image.png](https://s2.loli.net/2023/01/12/exSumPBhtw49LXn.png)

> 其中有一个非常好用的特性比如进行两个数相加的时候，位数可能会加1，那么我们可以使用 +& 来生成满足要求的位数



