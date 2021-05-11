# CE Reduction

### 简介
  在大容量NAND Package设计中，一个设计中可能存在很多个NAND Package，每个package中一般有2~8根CE# PIN。使用CE# Reduction机制可以让host的单个CE#被多个NAND pacakge复用,这样使得Host所需要的CE#引脚大大减少。
  
  CE Reduction机制在初始化过程中，为每一个NAND指定一个Volume地址。初始化后，host可以通过volume选择命令(E1h)在选择指定的Volume。
  
  **Tips**:这里要区分NAND中Package,Target,LUN的概念划分。可以参考下图

  ![NAND Package][1]

  在物理连接上,通过ENo和ENI依次串联起所有的NAND Package。第一个Package的ENI不会连接，后面的Package依次连接到前一个Package的ENo信号。
  
  在Power on的时候，ENo会被driver low。之后如果CE#被置成High状态，ENo对应为High-Z状态。如果CE#置成Low并set成对应的volume地址后，此时的ENo会被置高。

  ENi状态决定了NAND package是否接受cmd。 如果CE# LOW and ENi Pin is High,那么就可以接受cmd；反之如果CE# high或者ENi low，则不能接受cmd。

### initial sequence
1. host power on the NAND.
2. host pulls CE# LOW.
3. 如果resetting all NAND Parallel，host 发送Reset(FFh) command.此时Reset CMD会被所有的NAND Device接受到。
4. 如果reseeting all NAND sequence
    1). 只有ENi pin high的NAND device能接受到命令。
5. host发送set feature cmd 来设定Volume Configure(58h)。每个NAND target的Volume address应该都是独立的。发送set features 命令后，ENo被设置成High同时Volume is deselected，直到host发送Volume select(E1h)来选中指定的Volume。

### Volumn configure&&select

![vol_configure][4]

![vol_select][5]

### 常见的CE Reduction 拓扑结构

![CE_Reduction_Single_Channel][2]

![CE_Reduction_two_Channel][3]

  [1]: /images/ONFI-CE-Reduction/package.png "package.png"
  [2]: /images/ONFI-CE-Reduction/single.png "single.png"
  [3]: /images/ONFI-CE-Reduction/two_channel.png "two_channel.png"
  [4]: /images/ONFI-CE-Reduction/vol_configure.png "vol_configure.png"
  [5]: /images/ONFI-CE-Reduction/vol_select.png "vol_select.png"
  



