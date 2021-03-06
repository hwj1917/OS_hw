# 思考题
* 操作系统中存储管理的目标是抽象（进程拥有区别物理地址空间的逻辑地址空间）、保护（进程拥有独立的地址空间）、共享（进程能访问相同内存地址）、虚拟化（更大的地址空间）。

* 编译过程，负载将预处理生成的文件，经过词法分析，语法分析，语义分析及优化后生成汇编文件。编译过程，负载将预处理生成的文件，经过词法分析，语法分析，语义分析及优化后生成汇编文件。汇编，是将汇编代码转换为机器可执行指令的过程。通过使用gcc –C或者as命令完成。链接，负载根据目标文件及所需的库文件产生最终的可执行文件。加载，是操作系统将可执行文件装入内存，并对于动态链接的程序完成链接，建立符号表。

* 内碎片是指分配给任务的内存大小比任务所要求的大小所多出来的内存。外碎片只分配给任务的内存之间无法利用的内存。

* 最先匹配总是先找低地址空间的内存，到后期低地址空间都是大量小的不连续的内存空间，每次都要扫描低地址空间后到达高地址空间才能得到可用的内存。

* 最差匹配总是都找到最大的内存块进行分割，因此分割剩下的内存块也很大，往往能进行下一次分配。

* 紧凑是在内存中搬动进程占用的内存位置，以合并出大块的空闲块；对换是把内存中的进程搬到外存中，以空出更多的内存空闲块。早期的计算机内存小，多采用对换。而且对换处理也较简单。

* 一个处于等待状态的进程被对换到外存（对换等待状态）后，等待事件出现了。操作系统需要将进程从硬盘中读取到内存中，并将该进程标为等待状态并且调度其他进程。
 
* 伙伴系统的空闲块按照内存的大小有一系列链表组织,类似于哈希表，将相同大小的内存区域首地址连接起来。

* 当向内核请求分配(2^(i-1)，2^i]数目的页块时，按照2^i页块请求处理。如果对应的块链表中没有空闲页块，则在更大的页块链表中找。当分配的页块中有多余的页时，伙伴系统根据多余的页框大小插入到对应的空闲页块链表中。 释放多页的块时，内核首先计算出该内存块的伙伴的地址。内核将满足以下条件的三个块称为伙伴：(1)两个块具有相同的大小，记作b。(2)它们的物理地址是连续的。(3)第一块的第一个页的物理地址是2*(2^b)的倍数。如果找到了该内存块的伙伴，确保该伙伴的所有页都是空闲的，以便进行合并。内存继续检查合并后页块的“伙伴”并检查是否可以合并，依次类推。 