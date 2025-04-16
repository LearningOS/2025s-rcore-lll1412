# 实现功能总结

1.按要求实现sys_trace系统调用函数
2.统计每个app的每个系统调用的次数
3.通过测试用例

# 简答作业

## 1

使用：RustSBI version 0.4.0-alpha.1, adapting to RISC-V SBI v2.0.0

> [ch2b_bad_address.rs](../user/src/bin/ch2b_bad_address.rs): PageFault in application, bad addr = 0x0, bad
> instruction = 0x804003a4, kernel killed it.
> [ch2b_bad_instructions.rs](../user/src/bin/ch2b_bad_instructions.rs): IllegalInstruction in application, kernel killed
> it.
> [ch2b_bad_register.rs](../user/src/bin/ch2b_bad_register.rs): IllegalInstruction in application, kernel killed it.

## 2
### 2.1 
内核栈
### 2.2 
恢复了 sstatus，sepc，sscratch 寄存器的值
1. sstatus: 记录了之前坐在的特权级
2. sepc: 记录了返回用户态后的地址
3. sscratch: 记录了用户态的栈地址

### 2.3
`x2` 是 `sp`，后续修改后再进行保存，`x4` 用不到无需保存

### 2.4
sp中是内核栈，sscratch中是用户栈

### 2.5
发生在 `sret`

### 2.6
`sp` 中是用户栈，`sscratch` 中是内核栈

### 2.7
`ecall`

# 荣誉准则

1. 在完成本次实验的过程（含此前学习的过程）中，我曾分别与 以下各位 就（与本次实验相关的）以下方面做过交流，还在代码中对应的位置以注释形式记录了具体的交流对象及内容：

> 无

2. 此外，我也参考了 以下资料 ，还在代码中对应的位置以注释形式记录了具体的参考来源及内容：

> 无

3. 我独立完成了本次实验除以上方面之外的所有工作，包括代码与文档。 我清楚地知道，从以上方面获得的信息在一定程度上降低了实验难度，可能会影响起评分。

4. 我从未使用过他人的代码，不管是原封不动地复制，还是经过了某些等价转换。 我未曾也不会向他人（含此后各届同学）复制或公开我的实验代码，我有义务妥善保管好它们。
   我提交至本实验的评测系统的代码，均无意于破坏或妨碍任何计算机系统的正常运转。
   我清楚地知道，以上情况均为本课程纪律所禁止，若违反，对应的实验成绩将按“-100”分计。