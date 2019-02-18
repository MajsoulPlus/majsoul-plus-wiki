# 模组制作入门

本页面将会从零开始一步一步教你制作一个『[雀魂 Plus 浏览器](https://github.com/MajsoulPlus/majsoul-plus)』的模组。

## 事前准备

- 一款文本编辑器

> 推荐使用 [VSCode](https://code.visualstudio.com/) 或 [NotePad++](https://notepad-plus-plus.org/)；
> 如果您希望一步到位制作一个优秀的模组，一款优秀的文本编辑器必不可少。

> **警告：** 如果您是 Windows 用户，请**不要**使用「记事本」进行编辑！

- [熟悉 JSON 文件的格式](https://github.com/MajsoulPlus/majsoul-plus/wiki/JsonFormat)

> 您亦可参考，雀魂 Plus README 文档中的 [制作模组](https://github.com/MajsoulPlus/majsoul-plus#%E5%88%B6%E4%BD%9C%E6%A8%A1%E7%BB%84) 部分的 'mod.json' 文件模板，您可以参考这个文件进行编辑操作。

- 修改编码格式统一为 `UTF-8 无 BOM` （一般情况下无需修改，不排除出现错误的可能性）

- **务必**使用半角符号

~~四零：连这个都不懂做个屁 Mod~~

## 认识目录

- 游戏数据缓存目录
  - `(雀魂 Plus 根目录)/resources/app/static/` 

> **警告：** 请**不要**直接在缓存目录中修改文件, 以免清除缓存后文件丢失

- 模组存放位置
  - `(雀魂 Plus 根目录)/resources/app/mod/`
- 插件存放位置
  - `(雀魂 Plus 根目录)/resources/app/execute/`
- 工具存放位置
  - `(雀魂 Plus 根目录)/resources/app/tool/`
  
> **注：** 若您勾选了 `「使用 AppData 存储拓展资源」` 则游戏数据及模组等内容不会存储在上述目录中, 而将会存储在AppData文件夹中

## 新建模组

1. 在「模组存放位置」下, 新建文件夹并命名(后称为模组文件夹)

- **模组命名规范：** 
  1. 以 `(主要内容)` 为名称
  2. 以 `(素材名称)-(替换内容)` 为名称
  3. 后续补充

2. (必要)在模组文件夹中, 新建 `mod.json` 文件, 并复制 README 文档中 [制作模组](https://github.com/MajsoulPlus/majsoul-plus#%E5%88%B6%E4%BD%9C%E6%A8%A1%E7%BB%84) 部分的 'mod.json' 文件模板, 保存 

3. (非必要但推荐)在模组文件夹中, 选择一个 **256 * 256** 像素图片当作预览图

4. (必要)在模组文件夹中, 根据 `mod.json` 文件中 `dir` 的值创建文件夹, 默认值为 `/files`

## 简易制作模组流程

1. 从「游戏数据缓存目录」中选取想要修改的内容, 从 `/0` 文件夹开始复制目录到模组文件夹中
2. 修改 `mod.json` 文件中的 `"name"` 条目为「模组的名称」
3. 修改 `mod.json` 文件中的 `"author"` 条目为「作者的名字」
4. 修改 `mod.json` 文件中的 `"description"` 条目为「模组的简介」
5. 开始修改/替换已经复制的内容
