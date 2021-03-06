## 思想：

1. 负数用正数的补码来表示, 使得任意数字的加减乘除都可以用加法来实现。
2. 通过控制位来指定某个简单操作是否执行，通过组合这些可能的简单操作，
使得ALU拥有执行许多复杂操作的能力
3. ALU 模块可以小模块组成，小模块的设计方法：先写出真值表，从真值表可以推倒出模块结构

## 具体：

1. 可以用 n 个二进制位表示 `2^(n-1)` 个正数(首位定为0)， 负数通过正数的补码来表示。
(补码： `2^(n) - 正数`, 可以证明， 补码可以通过取反再加1的方式得到)
2. 关于ALU的实现：如果有 DMux16() 模块，会更高效。只不过没有内置该模块，那么就凑活着用Mux16吧

## ALU
- IN
    - x[16], y[16],  // 16-bit inputs
    - zx, // zero the x input?
    - nx, // negate the x input?
    - zy, // zero the y input?
    - ny, // negate the y input?
    - f,  // compute out = x + y (if 1) or x & y (if 0)
    - no; // negate the out output?

- OUT
    - out[16], // 16-bit output
    - zr, // 1 if (out == 0), 0 otherwise
    - ng; // 1 if (out < 0),  0 otherwise
