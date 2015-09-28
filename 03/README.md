# 记忆，具有时间依赖性--现在，记住一些之前的记忆。

计算机通过一个标准的时钟表示时间的进程。一个周期只能做一次计算。Any better idea?

## DFF (Data Flip-Flop) 边沿触发

- 输入： in， t
- 输出: out(t) = in(t-1)

计算机中所有DFF都被提供统一的时钟信号

## Bit： 一比特寄存器

- IN in, load;
- OUT out;

在DFF前加一个Mux，由load位来决定下一时刻是输入新值还是输入前一时刻的值

## Register： 16比特寄存器

- IN in[16], load;
- OUT out[16];

16 个Bit， load都一样

## RAMn: 由n个16位寄存器组成，通过address来决定对那个寄存器进行load 或者read

- IN in[16], load, address[log_2^n];
- OUT out[16];

### RAM8:

- IN in[16], load, address[3];
- OUT out[16];

使用DMux8Way 来决定load哪个 Register， 使用 Mux 来决定读取哪个 Register

### RAM64:

- IN in[16], load, address[6];
- OUT out[16];

address[3..5]： 使用 DMux8Way 来决定load那个 RAM8， 使用 Mux8Way16 来决定读取那个 RAM8
address[0..2]: 作为每一个RAM8的address
