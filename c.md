### 1. pack与align区别
1. #pragma pack(n)告诉编译器结构体或类内部的成员变量相对于第一个变量的地址的偏移量的对齐方式，缺省情况下，编译器按照自然边界对齐，当变量所需的自然对齐边界比n大 时，按照n对齐，否则按照自然边界对齐；#pragma pack () /*取消指定对齐，恢复缺省对齐*/

2. __attribute__((aligned(m)))告诉编译器一个结构体或者类或者联合或者一个类型的变量(对象)分配地址空间时的地址对齐方式。也就是所，如 果将__attribute__((aligned(m)))作用于一个类型，那么该类型的变量在分配地址空间时，其存放的地址一定按照m字节对齐(m必 须是2的幂次方)。并且其占用的空间，即大小,也是m的整数倍，以保证在申请连续存储空间的时候，每一个元素的地址也是按照m字节对齐。
3. 
4.
5.
