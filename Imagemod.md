# 制作角色立绘修改Mod

这个页面将会手把手教你制作『[雀魂 Plus](https://github.com/MajsoulPlus/majsoul-plus)』中适用的修改角色立绘的模组。

## 材料准备

- 你想使用的角色立绘 **越大越好**
- 一款你用起来上手的图片编辑器
- 你想修改的角色的现有mod或者是模板 （非必需）
>Windows自带的画图这种不能处理透明的请回避
- 你想要修改的角色的图片资源（下面会有获取方法）

## 一、获取官方图片素材
- **如果你已经有了自己想替换的角色的mod模板，那么可以直接跳过这一部分！！**

> 如果你没有模板，那么直接从官方的资源中获取你想要修改的图片会省去你调整图片尺寸的很多功夫
- 第一步，打开雀魂官网，同时按下F12打开开发者工具
![F12获取资源](https://github.com/40chyan/majsoul-plus-wiki/blob/master/imagemod_pics/1.png?raw=true)

- 如图，选择Network，然后选择Img来查看网页的图片资源，这里应该会需要按一下 Ctrl+R 来重启一遍网页
重启完之后网页的图片素材就会琳琅满目的显示在列表里。
---
- 第二步，你需要过一遍角色图片会出现的地方来让列表里出现**全部5张**你需要的图片模板
它们分别是：

     文件名|图片描述|可能出现画面
     --|:--:|--:
    full.png|全身立绘|主菜单，寮舍
    waitingroom.png|房间里细长立绘|房间准备画面
    bighead.png|大头照|寮舍中的头像
    smallhead.png|小头照|牌局中的头像
    half.png|半身立绘|鸣牌，立直
    
- 当你的游戏中出现过这些图片，那么你就可以在F12的资源列表里找到这张图，由于加密的原因，他们的文件名暂时都是**乱码**（如图所示）
- 将五张图片全都保存下来，存在一个文件夹里，将它们的文件名一一修改，完成后基本上就是如图所示：
![改好名字的图片资源](https://github.com/40chyan/majsoul-plus-wiki/blob/master/imagemod_pics/2.png?raw=true)

- 这样，我们的mod模板就初步完成了
---

## 二、改图
- 第一步，在改图的这个步骤里我们以 ~~柚子社最新最热作品RiddleJoker中的~~ 茉优学姐来作为例子修改八木唯的立绘。
首先你要有这么一张立绘，它的大小要超过原素材的任何一张，如果你不想让你的~~waifu~~角色变成马赛克的的话。
![一张美丽的立绘](https://github.com/40chyan/majsoul-plus-wiki/blob/master/imagemod_pics/3.png?raw=true)
---
- 第二步，接下来有一个虽然不必要但是从美观角度上考虑很重要的一个步骤那就是加**发光黑边**。
   如果仔细观察雀魂的每一张立绘你会发现每一个角色的立绘都是有黑色描边的，如果你自己的立绘不加上描边的话，虽然不影响使用，但是大幅影响美观，而且会让你的立绘看起来很突兀。（除非你把整个游戏的画风都改了）
![加黑边](https://github.com/40chyan/majsoul-plus-wiki/blob/master/imagemod_pics/4.png?raw=true)
---

- 第三步，正式替换原素材的图片，记得一定要**和原素材保持图片尺寸的一致**，为了美观，尽量保证立绘身体的比例大小差不多。
![改图](https://github.com/40chyan/majsoul-plus-wiki/blob/master/imagemod_pics/5.png?raw=true)
  到了这一步**我们先替换除了半身像以外的图片**，因为半身像的素材在下一步可能会进行一些特殊处理。
---

- 第四步，在我自己改图的时候，发现其他四张没有问题，就是鸣牌时的半身像
不知雀魂官方怎么处理这张图片的，就算两张图片的尺寸一模一样，只要半身像的左右**留了空白的透明部分**，它就会自动给你拉伸
> 目前纵向没有出现过这种情况，也有可能是个例，请各位自行研究
- 所以为了解决这个问题，我耍了小聪明，在图片最下方加了一层淡淡的黑色阴影来填充立绘左右的透明部分。才使得图片不被拉伸
 ![半身像](https://github.com/40chyan/majsoul-plus-wiki/blob/master/imagemod_pics/6.png?raw=true)

- ![半身像](https://github.com/40chyan/majsoul-plus-wiki/blob/master/imagemod_pics/7.png?raw=true)
---
- 这些问题都顺利的处理完成后，我们的改图步骤就大功告捷啦！
现在你的文件夹看起来应该是这样的
![改图完成](https://github.com/40chyan/majsoul-plus-wiki/blob/master/imagemod_pics/8.png?raw=true)
---

## 三、打包模组
- **在这一部分里，如果你已经有了角色立绘mod或者模板那就非常方便了，直接替换掉你的图片文件，然后跳跃到最后吧！**

- 当然，你也可以从头开始制作模组包。
-这里请仔细阅读[模组制作入门](https://github.com/MajsoulPlus/majsoul-plus-wiki/blob/master/CourseMod.md)中的**认识目录**和**新建模组**部分。

那么既然你已经懂了如何打包模组资源，那你接下来需要的东西就只有一个：**对应角色立绘的路径**
由于资源加密，路径不是那么好在开发者工具中看到，方便起见在这里直接列出目前角色立绘的路径：

- 一姬`~0/v0.4.1.w/extendRes/charactor/yiji/`
- 二阶堂`~/0/v0.4.83.w/extendRes/charactor/erjietang/`
- 爽哥`~0/v0.4.1.w/extendRes/charactor/qianzhi/`
- 巫女`~0/v0.4.1.w/extendRes/charactor/xiangyuanwu/`
- 抚子`~0/v0.4.1.w/extendRes/charactor/fuzi/`
- 加奈`~0/v0.4.1.w/extendRes/charactor/jianai/`
- 八木`~/0/v0.4.237.w/extendRes/charactor/bamuwei/`
- 九条`~/0/v0.4.237.w/extendRes/charactor/jiutiao/`
> 提示：老角色中，只有二阶堂因为更新过所以版本号不一样，八木和九条是新角色，所以版本号也不一样

- 接下来，了解了资源路径之后你就可以开始打包模组了，在`/mod/你的模组名字/files`里面照搬上面的路径，如图。
![打包模组](https://github.com/40chyan/majsoul-plus-wiki/blob/master/imagemod_pics/9.png?raw=true)

-  最后，一切就绪，在`/mod/你的模组名字/`里添加一下你的模组的预览图和描述，如图。
![后续工作](https://github.com/40chyan/majsoul-plus-wiki/blob/master/imagemod_pics/10.png?raw=true)
---
## 四、完成收尾
- 一切就绪后，打开[雀魂 Plus](https://github.com/MajsoulPlus/majsoul-plus)的客户端或者刷新模组页面，你的模组就完成了，赶快启动测试吧
 ![完成](https://github.com/40chyan/majsoul-plus-wiki/blob/master/imagemod_pics/11.png?raw=true)

~~不要改成色图哦~~

