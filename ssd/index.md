# SSD


<!--more-->
# SSD Architecture
- SSD is a complete, small system where all componets are soldedred on a PCB and is indpendenty packaged
 ---------------------------------------------------------------------------------------
|                                                                                       |
|                                SSD                                                    |
|                    ------------------------------------------------------------       |
|                   |                                                            |      |
|  -------          |  ----- -----       -----------------         ----------    |      |
| |       |         | |     |     |     |                 |       |          |   |      |CH0  ----- 
| |       |         | |     |     |     |                 |       |          |   |-----------|Flash|
| |       |         | |     |     |-----|                 |       |          |   |      |     -----
| |       |         | |     |     |     |    ARM Cores    |       |          |   |      |
| | PCIE  |         | |PCIE |NVMe |     |                 |-------|  Flash   |   |      |
| | Host  |-------- | |Layer|Layer|     |                 |       |Controller|   |      |CH1  -----
| |       |         | |     |     |     |                 |       |          |   |---------- |FLASH|
| |       |         | |     |     |      -----------------        |          |   |      |     -----
| |       |         | |     |     |        |          |           |          |   |      |
| |       |         | |     |     |        |          |           |          |   |      |
| |       |         | |     |     |     --------   -------- -     |          |   |   .  |
| |       |         | |     |     |    |Internal| |DRAM      |    |          |   |   .  |
|  --------         | |     |     |    | Buffer | |Controller|    |          |   |   .  |
|                   |  ----- -----      --------   ----------      ----------    |   .  |
|                   |                                   |                        |      |
|                   |                                   |         ------------   |      |
|                   |                                   |        |            |  |      |
|                   |                                   |        |other logic |  |      |CHN -----
|                   |                                   |        |            |  |--------- |FLASH|
|                   |                                   |         ------------   |      |    -----
|                   |                                   |                        |      |
|                    -----------------------------------|------------------------       |
|                                                       |                               | 
|                                                       |                               |
|                                                       |                               |
|                                                 -----------                           |
|                                                |           |                          |
|                                                |   DRAM    |                          |
|                                                |           |                          |
|                                                 -----------                           |
|                                                                                       |
 ---------------------------------------------------------------------------------------

# Controller功能
- 提供一个接口在host和Flash之间
- 处理来自host的数据，提高数据传输效率以及数据的可靠性。
  Controler中包含wear leveling， Garbage colletcion， Bad Block magnagement，ECC，flash interface。
  

# DRAM
- DRAM主要用来作为L2P(Logic to Physical) table mapping，一般配置是1GB NAND FLASH空间对应1MB DRAM
- FW code本省也需要dram空间来运行
- 多余的DRAM空间可以作为host write buffer以及其他的table（比如：Bad Block table， RBTree for good/availbale blocks）
- 帮助实现奇偶校验

# 其他部分
- voltage supervisor
  防止2powerloss and brown outs。如果检测到有power loss，那么fw对打断一些特殊操作。

- Backup capacitance
  super caps 可以保证整个drive backup（比如dump entrie dram）
  tantalum caps 提供一段时间保证program comman完成。

- NOR FLASH
  1. BOOTLOAD(Enumerates the nand, initialized the DRAM)
  2. Manufacturing data
  3. Page Table pOINTER(nand lbock that contains the L2P table)
  4. Error/evnet logs

