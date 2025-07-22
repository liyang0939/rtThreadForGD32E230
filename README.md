# rtThreadForGD32E230
基于兆易创新的官方固件库GD32E23x_Firmware_Library_V2.3.0，为GD32E230移植rt-thread实时操作系统rtThread nano，包括finsh交互界面

1、以keil为集成开发环境；

2、在keil上使用GD32E230芯片，需要安装对应的add-on，可以去GD的官方网站下载这个软件包：https://www.gd32mcu.com/download/agree/box_id/13/document_id/215/path_type/1

3、因GD32E230基于Cortex-M23内核，其ram最大只有8K字节，所以移植rt-Thread nano 3.1.5版本。

4、为了方便和外界进行交互，同时移植了finsh。finsh使用usart1，芯片的PA2和PA3引脚，波特率为115200，8位数据为，1位停止位，没有校验位；

5、除了默认的main线程之外，额外创建了一个CaiJi线程，这两个线程会周期性的打印一行字符串到shell窗口；这两个线程栈均为256字节，如果你需要编写业务代码，请根据实际情况设定对应的栈空间；

6、因ram很小，所以没有启用动态内存功能，所有功能只使用栈、全局变量、局部静态变量；

7、移植结束后，其占用的内存ram空间约为3.7kB，flash大小约为12kB：
Program Size: Code=11000 RO-data=996 RW-data=68 ZI-data=3644
