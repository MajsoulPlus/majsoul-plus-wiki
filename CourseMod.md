# 模组制作入门

本页面将会从零开始一步一步教你制作一个『[雀魂 Plus 浏览器](https://github.com/MajsoulPlus/majsoul-plus)』的模组。

## 事前准备

- 一款文本编辑器

> 推荐使用 [VSCode](https://code.visualstudio.com/) 或 [NotePad++](https://notepad-plus-plus.org/)；
> 如果您希望一步到位制作一个优秀的模组，一款优秀的文本编辑器必不可少。

> **警告：** 如果您是 Windows 用户，请**不要**使用「记事本」进行编辑！

- [熟悉 JSON 文件的格式](https://github.com/MajsoulPlus/majsoul-plus/wiki/JsonFormat)

- 修改编码格式统一为 `UTF-8 无 BOM` （一般情况下无需修改，不排除出现错误的可能性）

- **务必**使用半角符号

~~四零：连这个都不懂做个屁 Mod~~

## 文件结构

- 游戏数据缓存目录
  - `(雀魂 Plus 根目录)/resources/app/static/`

> **警告：** 请**不要**直接在缓存目录中修改文件，以免清除缓存后文件丢失

- 模组存放位置
  - `(雀魂 Plus 根目录)/resources/app/mod/`
- 插件存放位置
  - `(雀魂 Plus 根目录)/resources/app/execute/`
- 工具存放位置
  - `(雀魂 Plus 根目录)/resources/app/tool/`

> **注：** 若您勾选了 `「使用 AppData 存储拓展资源」` 则游戏数据及模组等内容不会存储在上述目录中，而将会存储在您的系统用户程序数据文件夹中，如 Windows 下则为 `%appdata%/Majsoul Plus`

## 创建新模组

1. 在「模组存放位置」下，新建文件夹并命名，以下使用 `mymod` 指代；

> 建议的命名：
> 
>- 以 `(主要内容)` 为名称
>- 以 `(素材名称)-(替换内容)` 为名称
>- 后续补充

2. 在模组文件夹中，新建 `mod.json` 清单文件，以下是一个典型清单文件的示例：

```json
{
  "name": "默认桌布替换为示例桌布",
  "author": "Handle",
  "description": "将默认桌布替换为第一届Sim杯日式麻将比赛桌布，\n仅用于本届比赛使用。",
  "//注释": "可选，设置Mod静态资源相对路径，默认值为 /files",
  "dir": "/files",
  "//注释": "可选，设置Mod预览图的相对路径，默认值为 preview.jpg",
  "//注释": "可选，用于替换原始资源路径 replace 属性可以支持多组正则表达式",
  "preview": "preview.jpg",
  "replace": [
    {
      "//注释": "将会作为正则表达式处理",
      "from": "/0/[^/]+/scene/Assets/Resource/tablecloth/tablecloth_default/Table_Dif\\.jpg",
      "//注释": "匹配目标，可以使用形如 $1、$2 的占位符",
      "to": "/0/v0.4.1.w/scene/Assets/Resource/tablecloth/tablecloth_default/Table_Dif\\.jpg"
    },
    {
      "from": "/0/[^/]+/myres2/tablecloth/tablecloth_default/preview\\.jpg",
      "to": "/0/v0.4.1.w/myres2/tablecloth/tablecloth_default/preview\\.jpg"
    }
  ],
  "//注释": "可选，一个内置在模组内的插件，其定义请参考 Wiki 文档中插件部分",
  "execute": {}
}
```

3. 在模组文件夹中，根据 `mod.json` 文件中 `dir` 的值创建文件夹，默认值为 `/files`；

4. （可选）推荐在模组文件夹中，创建一张矩形图像并指定给 `mod.json` 的 `preview` 属性作为预览图。

## 简易制作模组流程

1. 从「游戏数据缓存目录」中找到想要修改的内容，保持相同的相对路径，复制文件到模组文件夹中；

如：要替换的文件为 `/resources/app/static/0/v0.4.1.w/scene/Assets/Resource/tablecloth/tablecloth_default/Table_Dif.jpg`

你需要建立路径：

`/resources/app/mod/mymod/files/0/v0.4.1.w/scene/Assets/Resource/tablecloth/tablecloth_default`

> 缓存目录有时不会包含您希望替换的资源，您可以尝试启动游戏并确保要替换的资源已经被加载后再次尝试。

2. 修改 `mod.json` 文件中的 `"name"` 条目为「模组的名称」；

3. 修改 `mod.json` 文件中的 `"author"` 条目为「作者的名字」；

4. 修改 `mod.json` 文件中的 `"description"` 条目为「模组的简介」；

5. 对已经复制的内容进行编辑或替换。

## 测试&打包模组

打开雀魂 Plus 浏览器，选择左侧的「模组」标签页，若步骤进行无误，您应该已经可以在右侧面板中找到您的模组。模组右下角的开关默认为未启用状态，在您启用后，就可以启动游戏进行测试了。

测试无问题后，点击右上角纸笔图案的「编辑」按钮，此时模组右下角的开关位置变为了删除和打包选项（再点击一次「编辑」按钮可恢复），点击打包并选择保存位置即可。

## 附录：进阶功能

清单文件中的 `replace` 字段与 `execute` 字段均为可选功能：

- 前者可将不同路径的文件指向同一替换文件，一定程度上防止版本更新造成的模组失效 & 避免重复文件难以维护，需要一定正则表达式基础
- 后者可运行自定义脚本以完成一些高级功能，需要一定 `Javascript` 基础（具体请参考 `README` 文档中[开发插件](https://github.com/MajsoulPlus/majsoul-plus#开发插件)部分）

[正则表达式入门教程](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions)

[Javascript 入门教程](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/First_steps)
