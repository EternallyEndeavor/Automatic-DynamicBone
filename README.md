写在开头:  
* 如果您是第一次接触该项目,您可以选择在[此处下载示例](https://wws.lanzous.com/iotvcf8d3mb) 并访问[项目的wiki](https://github.com/OneYoungMean/Automatic-DynamicBone/wiki)  
* [English version manual](https://github.com/OneYoungMean/Automatic-DynamicBone/wiki/English-version-manual)  sorry Im too busy to make the localization XD

- **当前版本:0.9preview 最后更新日期:20/7/31**  
- **除了修bug以外应该不会大改了..大概**   

# AutomaticDynamicBone
**unity骨骼布料仿真插件**.  
* 基于https://github.com/SPARK-inc/SPCRJointDynamics 
* 基于unity jobs 多线程系统
* 一个可以根据骨骼布料,自动生成具有物理效果头发和裙子,用于代替dynamicBone插件功能
* 此外,缅怀作者被dynamic bone坑走了**15美刀**  


## 快速开始

1. 在脚本中找到**ADBRuntimeController**,添加到你想要添加的目标/目标父物体上.  
2. 检查目标需要添加物理效果的骨骼,通常这类骨骼名字都会包含一个**固定的关键词**,比如hair,skirt,你需要把关键词写入到 _识别关键词_ 中.  
3. 按下`生成节点数据`,并在底下找到绘制并辅助线勾选,如果一切顺利的话,你可以看到几条彩色的线和点,这些就是识别到的数据.  
4. 运行游戏,一切已经就绪,晃动你的目标以查看效果,就是这么快XD!  

![](https://s1.ax1x.com/2020/08/02/atCRNd.gif) 


## 特性

- **针对高性能进行优化**尽可能脱离对于monobehavior的操作,尽可能减少GC以及针对物理效果的优化,采用 unity Job System + Burst compiler作为基础,采用指针写的物理底层,使用多线程进行计算与修改transfrom,拥有着**极其强悍的优化程度!**[详情](https://github.com/OneYoungMean/AutomaticDynamicBone/wiki/Q&A#q%E6%80%A7%E8%83%BD%E6%96%B9%E9%9D%A2%E5%85%B7%E4%BD%93%E6%80%8E%E4%B9%88%E6%A0%B7)  

- **无需(但兼容)ECS与Dots!** 我们并**没有**采用ECS系统!除了unity的多线程jobs系统,你不用担心额外的jobs系统其对你的项目造成影响!并支持除了WebGL以外**所有平台**  

- **极其低的学习曲线!** 作者已经帮你们把门槛踏平了!无需任何复杂的添加与操作,通过关键词识别与humanoid识别,只需要三分钟学习就可以**一键生成**你想要的bone与collider!

- **良好的报错系统!** 任何不正确的操作都会给出相关的提示,作者已经帮你们把能犯的错误犯过了!  

- **适应runtime的脚本!** 无需复杂的操作,只要简单设置参数,就能允许你在runtime过程中生成整套的物理特性,是的,你甚至不需要任何操作就可以完整套物理的生成!  

- **高度自由的物理与运行时保存系统!** 提供各种参数,可以自由的组合出你想要的的物理特性!你无需反复调试这些物理参数,因为你可以随时在runtime过程中修改并保存他们!  

- **独特的迭代与除颤机制!** 我们通过细分物体的运行轨迹,在一帧内同时计算多个细分位置的受力情况并加以综合,通常只需要四次你就能获得预期的效果,只要你迭代的足够多,你就能获得无限接近稳定的物理!  

- **完整且高效的Collider系统!** 支持球体,胶囊体,立方体的碰撞;支持杆件/点与collider的碰撞;无需创建transfrom,你可以在交互界面实现偏移,旋转等效果!;同时,该脚本提供了一套完整的collider过滤机制与距离近似估计的算法,大大提高了碰撞的运行效率,一切都是为了让你尽可能的快!  

- **独特的黑科技!** **一键生成人物一整套Collider,可定制的Collider对撞规则,动态实时的性能调节**以及,你甚至可以**在编译好的程序中给AssetBundle包当中的角色**[添加该脚本](https://github.com/OneYoungMean/AutomaticDynamicBone/wiki/ADBRuntimeController%E4%BB%8B%E7%BB%8D#%E5%A6%82%E4%BD%95%E5%9C%A8runtime%E7%9A%84%E6%97%B6%E5%80%99%E6%B7%BB%E5%8A%A0%E8%AF%A5%E8%84%9A%E6%9C%AC)**及时生成物理!**

- **简洁的操作界面!** 是的,我们已经将大部分能够优化的操作界面已经优化掉了,现在不会再有多余的选项出现,并且你可以直接在inspector看到统计的数据.  

- **完整的内部源码!** 不打包dll,提供所有的运行细节以及大量的注释!你可以任意定修改某一部分,已获得想要的物理效果与特殊性质,并且大可不必担心随之而来的耦合问题!  

- **免费!** 以及作者被dynaimc bone坑走了15美刀.** 并且<s>作者是MMD模型白嫖怪</s>MMD友好程度**极高!**

- **作者长期在线!** 有issue必回!包君满意!

![Github只支持5mb的动图,导致好好的一张图硬生生压成一坨shit](https://s1.ax1x.com/2020/08/01/aGEHyV.gif)
![我承认magic cloth很好用,但是这不是你们试图让我盗用别人代码的理由,我是开源插件,爱用不用](https://s1.ax1x.com/2020/09/17/wfmGUe.gif)

## 要求

- Unity2018.4及以上,除webGL外所有支持unity jobs的平台.  


### 说明书

[更多详情请参见wiki](https://github.com/OneYoungMean/Automatic-DynamicBone/wiki) 

### 最后,如果你喜欢本项目记得给本项目star!
```C#
[省略掉的吐槽很辛苦的话]
[省略掉的吐槽自己真的很穷的话]
[省略掉的小声BB的话]
有没有愿意收留实习生的,弱小,无助,可怜,还没钱QAQ
```
***
### 已知存在问题
节点的点碰撞目前只支持碰撞体-向外排斥.   
