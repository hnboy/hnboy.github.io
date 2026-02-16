# NAND FLASH ONFI SPEC 4.0 ( 一 )


## Interface(SDR NVDDR NVDDR2/NVDDR3)

- IO bus 改名成DQ bus.
- 多了个DQS 信号，DQS为双向管脚。 DQS不能用于cmd和address cycle。在SDR mode下DQS应该被host 拉高，device ignore ， DQS沿对应data valid window。

- NV-DDR interface

  - WE_n (clk)代替clock signal.
  - RE_n(W/R#)变成write/read 双向管脚信号. 

- NV-DDR2/3

  - RE_N变成RE_t , RE_c
  - DQS信号来做DQ data bus strobe.

  ![](/images/ONFI/interface.png)

## ONFI VS Tole

- Tole同步模式下不用clock，写数据用DQS差分信号跳变沿触发，读数据用Host发的REN差分信号跳变沿发读request，DQS跳变沿输出数据。
- ONFI2.0 增加NV-DDR，支持DDR操作，但是使用同步时钟来控制，所以边沿容易受干扰。ONFI3.0增加DDR2,ONFI4.0增加NV-DDR3,均支持DQS差分信号而不同同步时钟.

## Sync(同步) VS Async(异步)

 简单来说，需要时钟信号的就是同步NAND Flash，不需要时钟的就是异步NAND。

- 引脚的功能区别

  - 同步模式下PIN8为W/R#pin, 异步模式下为RE#引脚

  - 同步模式下PIN18为CLK引脚，异步模式下为WE#引脚

  - 同步模式下PIN35不使用，异步模式下DQS信号.

    

  ![](/images/ONFI/pin_define.png)

  

- 异步模式下cmd address and data in/*out* 

   

  ![](/images/ONFI/async_cmd_sequence.png)

  ![](/images/ONFI/async_address_sequence.png)

  ![](/images/ONFI/async_data_in.png)

  ![](/images/ONFI/async_data_out.png)

## Data input/output Pausing 

- host暂停data tinput/output
  - SDR模式下将WE#和RE#置高即可暂停数据输入输出
  - NV-DDR模式通过将ALE/CLE置低可暂停数据输入输出
  - NV-DDR2/3模式可以通过保持RE#高或者低电平（即RE#不发生信号翻转即可）。也可以通过暂停DQS信号。在数据暂停阶段ODT是保持开的状态了（如果device enable 了ODT 模式）

## Data Interface/Timing Mode转换
  根据ONFI 4.0 SPEC描述为只有以下几种情况的mode可以切换
  - SDR to NV-DDR
  - SDR to NV-DDR2
  - NV-DDR to SDR
  - NV-DDR2 to SDR
  NV-DDR3无法转换到其他mode(这里只是说用户模式下，正常command无法切换，实际
  上vendor是可以通过自己的测试模式进行切换，可以从NVDDR3-> SDR模式)，1.2V情况默认上电即NV-DDR3 mode（有些device 1.2V情况下上电默认是DDR3 mode 0)
  所有的mode切换都是通过set feature来设定。

未完待续！！！

