#### 兵种文件的XML位置：

> X:\Steam\steamapps\common\Mount & Blade II Bannerlord\Modules\SandBoxCore\ModuleData\spnpccharacters



#### 兵种翻译文件位置：

> X:\Steam\steamapps\common\Mount & Blade II Bannerlord\Modules\SandBoxCore\ModuleData\Languages\CNs\std_spnpccharacters_xml-zho-CN.xml



#### 操作方法：

> Ctrl+F输入中文查询兵种，“    ”内是兵种代码，查询到后复制。
>
> 到兵种文件中Ctrl+F，输入查询对应的数据。



#### 参考资料：

###### 兵种熟练度：

兵种熟练度在 <skills>和 </skills>之间。

> 各项熟练度代码如下：
> 单手OneHanded 双手TwoHanded 长杆武器Polearm
> 弓Bow 十字弩Crossbow 投掷Throwing
> 骑术Riding 跑动Athletics 锻造Crafting
> 侦查Scouting 战术Tactics 流氓习气Roguery
> 魅力Charm 统御Leadership 交易Trade
> 管理学Steward 医术Medicine 工程学Engineering
> 没有写的出代码，表示该兵种无此项熟练度。 



###### 兵种装备数据：

<equipmentSet>和 </equipmentSet>之间，注意这段有三段重复，必须全部修改，不然无法完成修改。



###### 物品文件位置：

> X:\steam\steamapps\common\Mount & Blade II Bannerlord\Modules\SandBoxCore\ModuleData\spitems



###### 物品翻译位置：

> X:\steam\steamapps\common\Mount & Blade II Bannerlord\Modules\SandBoxCore\ModuleData\Languages\CNs\std_spitems_xml-zho-CN



###### 武器位置：

武器修改在<equipment slot="ItemX"
                 id="Item.          " />中，最多有四个武器位：X=0、1、2、3。



###### 装备位置：

在<equipment slot="    "
                 id="Item.          " />中，一共有Head（头部）、Body（身体）、Gloves（手部）、Leg（腿部）、Cape（披风）五个部位。



###### 注意：

如果武器或装备栏位代码缺失，则兵种在对应栏位也不会使用武器或装备。



[参考：骑砍中文站-抛砖引玉，浅谈兵种武器装备TXT修改方法](http://bbs.mountblade.com.cn/thread-2059238-1-1.html)

