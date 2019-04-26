# CodeSurvivor
Agent_55open

代码运行思路
============

和PUBG一样，使用的`杀人+跑路`
-----------------------
### 每次调用take_action（）时：<br>
#### if 所有玩家中有和自己距离小于6的玩家，优先射击：<br>
&nbsp;&nbsp;&nbsp;&nbsp;因为子弹的命中率和距离线性相关：所以选择距离小于6时进行射击，此时的命中概率理论上是大于40%的。

#### 如果没有人和自己的距离小于6，就开始跑路，也就是吃鸡中的占点
下面是`跑路部分`思路<br>
&nbsp;&nbsp;&nbsp;&nbsp;根据self.hunger或者self.thirst的状态判断要跑路的目的地<br>
&nbsp;&nbsp;&nbsp;&nbsp;确认跑路目的地的方法就是利用广度优先搜索`BreadFirstPathsB`搜距离self.next_safe_center最近的点<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;例如要补充口渴值，就搜距下个安全中心最近的水边点<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;例如要补充饥饿值，就搜距下个安全中心最近的森林点<br>
#### 需要注意的是跑路目的地不能是wall或者water<br>
#### 目的地也就是代码中的target_place<br>
if 当前位置 `不等于` 跑路目的地：<br>
&nbsp;&nbsp;&nbsp;&nbsp;`BreadFirstPathsA`搜自身距离至目的地的最短路径<br>
&nbsp;&nbsp;&nbsp;&nbsp;if 路径非空<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;每次调用过程访问路径中第一个点<br>
&nbsp;&nbsp;&nbsp;&nbsp;else 路径为空 `因为我的路径搜索不走水，所以可能出现路径为空的情况`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;射击最近玩家<br>
else:<br>
&nbsp;&nbsp;&nbsp;&nbsp;射击最近玩家




    
    


    
   
