### 前言

这是我的毕业设计（2020年），主要包含了对电脑的各类资源进行显示，此外还包含了游戏挂机和音乐频谱等功能。考虑到后期维护性，还具有IAP在线升级功能。整个设计包含了3D模型设计、下位机硬件电路设计、下位机软件程序编写、上位机软件程序编写。下位机主控芯片采用的是STM32F103C8T6(CBT6)，为了节省成本和缩小体积，PCB没有采用4层板而是采用的两张2层板进行叠加的方式。其中上位机和下位机的通信规则是自定义的，具体可以参见文档。

------

### 效果演示视频 [B站指路](https://www.bilibili.com/video/BV1Yv411B7Ur/)
------
### 项目文件说明
> * dashboard-iap-windows[链接](https://github.com/POTN-dashboard/dashboard-iap-windows)：IAP升级时，PC端需要用到的。主体为C++，使用的是VS code，如果仅仅需要使用直接下载release即可。
> * dashboard-app-windows[链接](https://github.com/POTN-dashboard/dashboard-app-windows)：平时使用时，PC端需要用到的。主体为C++，使用的是 VS,如果仅仅需要使用直接下载release即可。
> * dashboard-iap-stm32[链接](https://github.com/POTN-dashboard/dashboard-iap-stm32)：IAP升级时，STM32用到的，使用的是keil5
> * dashboard-app-stm32[链接](https://github.com/POTN-dashboard/dashboard-app-stm32)：平时使用时，STM32用到的，使用的是keil5
> * Dashboard-Others[链接](https://github.com/POTN-dashboard/Dashboard-Others)：其中3D_model包含了3D模型及装配，使用的是solidworks，采用的是光固化打印（对精度要求较高)。  
PCB是PCB文件，使用的是AD19,PCB1是底板，PCB2是上层板。打样采用的是嘉立创8mm板厚的黑色。PCB3和PCB4是为了节约成本的不合规拼版，其中PCB4不会被嘉立创发现，可以五元包邮。  
doc包含了各类文档，上位机和下位机的通信规则、开发过程中使用到的工具和参考了的网页.
 

------

### 关于设计思想
 首先希望价格低廉，希望尽可能多的人可以自己DIY，本次设计做到了无3D打印外壳时，自己DIY成本可以做到30元内。如果需要3D打印外壳也可以找淘宝白嫖首单优惠，只需要付运费即可。（本人打印的店铺是未来工厂）。  
 
 本人考虑过无线，但是由于想要实现游戏挂机功能，所以做成有线是最优解，还可以节约电池的成本。当然都21世纪了，接口肯定采用最先进的type-c，在开发过程中发现双层板布线做不到特别小的体积，但是四层板又太贵，所以采用了两张双层板叠加在一起的方式。实现了双层板布线，并且可以嘉立创拼版五元包邮（别打邮票孔，自己用钳子剪一下就好）。  
 
 这里采用OLED屏幕的原因是，看起来有一种像素风格，感觉比较“高级”。而且OLED的低功耗后期也有利于改无线，减少工作量。
 芯片选型STM32F103C8T6的原因主要是便宜好用，而且也有个USB控制器，可以直接硬件USB。
 
 为了缩小体积，使用的元器件都是贴片。因为本人是穷逼没有热风枪也没钱开钢网，所以只能电烙铁。因此使用的封装最小的只是0603.
 3D建模后光固化打印，其余连接采用的是符合国标的M2螺钉螺母和六角柱，我使用的是尼龙材质。

------

### 关于上位机
 上位机本来想用Qt写个界面的，奈何本人懒狗，一直没有开工。如果哪位大佬有闲情逸致帮忙写个，在下也是感激不尽的（黑框框确实也太没牌面了）。

------
### 关于BUG
 本次设计还存在一个严重影响用户体验的BUG，就是每次IAP升级后，从app程序软件复位跳转到iap程序后，USB不能被正确的识别。但是从iap跳转到app却能够正常运行。本人想要通过纯软件解决这个问题，但是感觉这个问题目前超出了我的能力范围。目前的解决方案是，每次升级从app跳转到iap后重新插拔设备，重新硬件上电即可识别。

------
### 关于教程
 如果有人觉得这个项目有意思，想要自己做一个或者再次基础上进行改进。本人后期可以考虑出一个开发教程（开发文档），有什么问题都可以私聊我，工程相关的问题可以Issues里发，其余问题可以B站私信我（对，没错，我就是2020届的双非本科）~~~
