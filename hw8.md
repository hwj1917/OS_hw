# 思考题
* “均衡繁忙”是指各种存储介质都处理繁忙状态，但又不构成系统瓶颈。

* 覆盖指的是划分程序功能模块、不会同时执行的模块共享同一块内存。
程序员的任务是进行模块划分、确定模块的共享关系。

* 交换指的是作为一个整体的进程地址空间的换入和换出。覆盖与交换的不同在于，覆盖通过切块，解决进程空间大于物理内存的问题；交换通过进程整体交换，解决高优先级进程运行需要的内存空间不够问题。

* 可以通过静态代码分析、动态函数调用跟踪分析内核模块间的依赖关系，获取内核模块间的函数调用列表。

* 有意识地规范程序跳转和数据访问可以提高程序执行时的局部性特征。

* 虚拟存储指的是只把当前指令执行所需要的部分进程地址空间内容放在物理内存中。特征包括不连续性、大用户空间、部分交换。

* 虚拟存储需要硬件支持地址转换，操作系统支持置换算法。

* 为了支持虚拟页式存储的实现，页表项需要增加：
驻留位：表示是否在内存；
修改位：表示是否被修改过；
访问位：表示是否被访问过；
保护位：表示允许页面访问方式。

* 缺页异常的处理包括：
指令执行中的页表项引用；
由于页面不在内存，导致缺页异常；
在外存中查找需要访问的页面备份；
页面换入；
页表项修改；
重新执行导致缺页异常的指令；

* 虚拟页式存储管理中有效存储访问时间EAT = 访存时间 * (1-p) + 缺页异常处理时间 * 缺页率p。
 