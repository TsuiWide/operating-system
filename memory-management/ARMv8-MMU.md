
ARMv8中，Kernel Space的页表基地址存放在TTBR1_EL1寄存器中，User Space页表基地址存放在TTBR0_EL0寄存器中，其中内核地址空间的高位为全1，(0xFFFF0000_00000000 ~ 0xFFFFFFFF_FFFFFFFF)，用户地址空间的高位为全0，(0x00000000_00000000 ~ 0x0000FFFF_FFFFFFFF)

ARMv8中：

虚拟地址支持
64位虚拟地址中，并不是所有位都用上，除了高16位用于区分内核空间和用户空间外，有效位的配置可以是：36, 39, 42, 47。这可决定Linux内核中地址空间的大小。比如我使用的内核中有效位配置为CONFIG_ARM64_VA_BITS=39，用户空间地址范围：0x00000000_00000000 ~ 0x0000007f_ffffffff，大小为512G，内核空间地址范围：0xffffff80_00000000 ~ 0xffffffff_ffffffff，大小为512G。

页面大小支持
支持3种页面大小：4KB, 16KB, 64KB。

页表支持
支持至少两级页表，至多四级页表，Level 0 ~ Level 3

