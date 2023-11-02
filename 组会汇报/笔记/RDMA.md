# RDMA

## 1. DMA和RDMA概念

### 1.1 DMA

DMA(直接内存访问)是一种能力，允许在计算机主板上的设备直接把数据发送到内存中去，数据搬运不需要CPU的参与。

传统内存访问需要通过CPU进行数据copy来移动数据，通过CPU将内存中的Buffer1移动到Buffer2中。DMA模式：可以同DMA Engine之间通过硬件将数据从Buffer1移动到Buffer2,而不需要操作系统CPU的参与，大大降低了CPU Copy的开销。

![传统和DMA模式](C:\Users\Administrator\Desktop\组会汇报\笔记\图片\传统和DMA模式.jpg)

### 1.2 RDMA

RDMA是一种概念，在两个或多个计算机进行通讯的时候使用DMA，从一个主机的内存直接访问另一个主机的内存。

![](C:\Users\Administrator\Desktop\组会汇报\笔记\图片\RDMA.jpg)

RDMA是一种host-offload, host-bypass技术，允许应用程序(包括存储)在它们的内存空间之间直接做数据传输。具有RDMA引擎的==以太网卡(RNIC)==--而不是host--负责管理源和目标之间的可靠连接。使用RNIC的应用程序之间使用专注的==QP==和==CQ==进行通讯：

1. 每一个应用程序可以有很多QP和CQ
2. 每一个QP包括一个SQ和RQ
3. 每一个CQ可以跟多个SQ或者RQ相关联

![](C:\Users\Administrator\Desktop\组会汇报\笔记\图片\RDMA传输模式.jpg)