# 思考题
* 段寄存器3-15位是选择子，存放的是段描述符的索引，该描述符用于描述存储器段的位置、长度和访问权限。而段描述符可以分为两种，全局描述符(GDT)和局部描述符(LDT)，对应着第2位，而0,1两位是表示CPU的权限级别（0-4级）。

* CPL是当前进程的权限级别(Current Privilege Level)，是当前正在执行的代码所在的段的特权级，存在于cs寄存器的低两位。  
RPL说明的是进程对段访问的请求权限(Request Privilege Level)，是对于段选择子而言的，每个段选择子有自己的RPL，它说明的是进程对段访问的请求权限。  
DPL存储在段描述符中，规定访问该段的权限级别(Descriptor Privilege Level)，每个段的DPL固定。

* 中断处理中硬件压栈内容是一些寄存器的值。用户态中断和内核态中断的硬件压栈不同之处在于用户态需要进行堆栈切换。

* 在用户态的中断响应要使用内核堆栈是为了保护中断服务例程代码的安全。

* trap类型的中断明确是从用户态跳到内核态，需要在IDT表中设定优先级的转变，从而实现堆栈切换等操作。还需要注意，控制权通过trap门进入处理程序时不关中断。

* ebp可以直接获得，不使用内联函数将获得错误的值。而eip不存在直接获得的指令，需要利用函数将eip压栈的特性间接获得。

* 不是。CPU启动后，中断向量表尚未建立。
 