# 控制流

## 1. 赋值

在chisel中可以对一个数据进行多次的赋值，但是对于赋值而言，使用最后一次赋值的作为结果

## 2. 逻辑语句

虽然在scala中有if else 循环语句，但是如果需要通过chisel中的变量类型进行判断，那么则需要使用下面这种

```scala
when(condition) {
	
}.elsewhen(someOtherBooleanCondition) {
	
}.otherwise {
	
}
```

## 3. 线网类型

线网类型我们可以看作是用于连接输入输出信号的变量，它可以被赋值，也可以用于向其他变量进行赋值的操作

如果要初始化一个线网的类型，可以使用wire(val)的形式

```scala
package flow  
  
import chisel3._  
import chisel3.experimental.IO  
class poly {  
   val io = IO(new Bundle {  
      val select = Input(UInt(2.W))  
      val x = Input(SInt(32.W))  
      val fofX = Output(SInt(32.W))  
   })  
   val res = Wire(SInt(32.W))  
   val square = Wire(SInt(32.W))  
  
   square := io.x*io.x;  
   when(io.select === 0.U) {  
      res := 3.S*square + 2.S*io.x  
   }.elsewhen(io.select === 1.U) {  
      res := 2.S*io.x  
   }.otherwise {  
      res := 0.S  
   }  
}
```


