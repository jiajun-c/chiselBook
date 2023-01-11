
# 测试

chisel中使用test库进行测试，使用poke进行输入，使用expect来判断是否满足我们预期的输出

```scala
test(new <YouModule>) { m => 
	m.io.in.poke(<value>)
	m.io.out.
}
```

具体的使用如下所示

|        | iotesters             | ChiselTest            |
| :----  | :---                  | :---                |
| poke   | poke(c.io.in1, 6)     | c.io.in1.poke(6.U)    |
| peek   | peek(c.io.out1)       | c.io.out1.peek()      |
| expect | expect(c.io.out1, 6)  | c.io.out1.expect(6.U) |
| step   | step(1)               | c.io.clock.step(1)  |
| initiate | Driver.execute(...) { c => | test(...) { c => |

## 1. 使用chiselTest

```scala
package operator

import chisel3._
import chiseltest._
import org.scalatest.freespec.AnyFreeSpec
import chisel3.experimental.BundleLiterals._
class opSpec extends AnyFreeSpec with ChiselScalatestTester {
	"dut" in {
		test(new op) {
			o => {
				o.io.in1.poke(2.U)
				o.io.in2.poke(3.U)
				o.io.out.expect(5.U)
			}
		}
	}
}
```

## 2. 使用iotesters
```scala
test(new PassthroughGenerator(16)) { c =>
    c.io.in.poke(0.U)     // Set our input to value 0
    c.clock.step(1)    // advance the clock
    c.io.out.expect(0.U)  // Assert that the output correctly has 0
    c.io.in.poke(1.U)     // Set our input to value 1
    c.clock.step(1)    // advance the clock
    c.io.out.expect(1.U)  // Assert that the output correctly has 1
    c.io.in.poke(2.U)     // Set our input to value 2
    c.clock.step(1)    // advance the clock
    c.io.out.expect(2.U)  // Assert that the output correctly has 2
}
```


## 3. 队列接口测试


## 4. 使用fork和join进行测试




