# 模组制作入门

本页面将会从零开始一步一步教你制作一个『[雀魂 Plus 浏览器](https://github.com/MajsoulPlus/majsoul-plus)』的模组。

## 事前准备

- 一款文本编辑器

> 推荐使用 [VSCode](https://code.visualstudio.com/) 或 [NotePad++](https://notepad-plus-plus.org/)；
> 如果您希望一步到位制作一个优秀的模组，一款优秀的文本编辑器必不可少。

> **警告：** 如果您是 Windows 用户，请**不要**使用「记事本」进行编辑！

- [熟悉 JSON 文件的格式](https://github.com/MajsoulPlus/majsoul-plus/wiki/JsonFormat)

- **务必**使用半角符号

~~四零：连这个都不懂做个屁 Mod~~

## 文件结构

## 文件结构

你需要在雀魂 Plus 浏览器的 `/resources/app/mod` 文件夹（若开启了`使用 AppData 存储拓展资源`选项，则在`%APPDATA%/Majsoul Plus/mod`文件夹下）下新建一个文件夹，建议使用能够说明本 mod 作用的英文字符作为文件夹名，以下使用`mymod` 指代

`mymod` 文件夹下必须要有一个清单文件，名为 `mod.json` （格式见下）

推荐放置一个方形预览图以更加简单地描述本模组的作用

## 清单文件

仓库中的`./mod/mallard`路径已经包含了一个示例模组，用于将默认千织替换为绿头鸭。 您可以参照这个模组进行修改和编辑

一个模组由一个`mod.json`文件和若干资源文件组成，模组会在游戏尝试加载资源时优先于官方资源被加载，以下为`mod.json`的一个示例：

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
      "//注释": "匹配目标，可以使用形如 $1, $2 的占位符",
      "to": "/0/v0.4.1.w/scene/Assets/Resource/tablecloth/tablecloth_default/Table_Dif\\.jpg"
    },
    {
      "from": "/0/[^/]+/myres2/tablecloth/tablecloth_default/preview\\.jpg",
      "to": "/0/v0.4.1.w/myres2/tablecloth/tablecloth_default/preview\\.jpg"
    }
  ],
  "//注释": "可选，一个内置在模组内的插件，其定义请参考 README 文档中插件部分",
  "execute": {}
}
```

## 缓存替换

你可以先启动一次游戏，确保需要替换的缓存已经被加载，然后在雀魂 Plus 浏览器的 `static` 文件夹下寻找需要替换的缓存文件（善用搜索功能，绝大多数是拼音命名……），记住其路径，在 mod 的 `files` 文件夹（可通过清单文件进行配置，以下使用 `files` 代称）下建立相同的路径，放置同名文件即可替换缓存
推荐放置一个方形预览图以更加简单地描述本模组的作用
如：要替换的文件为 `/resources/app/static/0/v0.4.1.w/scene/Assets/Resource/tablecloth/tablecloth_default/Table_Dif.jpg`
## 清单文件
你需要建立路径：

`/resources/app/mod/mymod/files/0/v0.4.1.w/scene/Assets/Resource/tablecloth/tablecloth_default`
  "author": "Handle",
并在其下放置名为 `Table_Dif.jpg` 的文件以替换缓存

## 测试&打包模组

打开雀魂 Plus 浏览器，选择左侧的"模组"页面，若前面的步骤进行无误，你应该能看到你自己的模组，模组右下角的开关默认为未启用状态，需要手动启用，可以启动游戏进行测试

测试无问题后，点击右上角纸笔图标，此时模组右下角的开关位置变为了删除和打包选项（再点击一次可恢复），点击打包并选择保存位置即可
  "//注释": "可选，设置Mod静态资源相对路径，默认值为 /files",
## 附录：进阶功能
  "//注释": "可选，设置Mod预览图的相对路径，默认值为 preview.jpg",
清单文件中的 `replace` 字段与 `execute` 字段均为可选功能：
      "//注释": "将会作为正则表达式处理",
- 前者可将不同路径的文件指向同一替换文件，一定程度上防止版本更新造成的 mod 失效 & 避免重复文件难以维护，需要一定正则表达式基础
- 后者可运行自定义脚本以完成一些高级功能，需要一定 `javascript` 基础（请参考 `README` 文档中[开发插件](https://github.com/MajsoulPlus/majsoul-plus#开发插件)部分）
      "//注释": "匹配目标，可以使用形如 $1, $2 的占位符",
[正则表达式入门教程](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions)
    },
[javascript 入门教程](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/First_steps)
      "from": "/0/[^/]+/myres2/tablecloth/tablecloth_default/preview\\.jpg",
    }
  ],
  "//注释": "可选，一个内置在模组内的插件，其定义请参考 README 文档中插件部分",
  "execute": {}
}
```

## 缓存替换

你可以先启动一次游戏，确保需要替换的缓存已经被加载，然后在雀魂 Plus 浏览器的 `static` 文件夹下寻找需要替换的缓存文件（善用搜索功能，绝大多数是拼音命名……），记住其路径，在 mod 的 `files` 文件夹（可通过清单文件进行配置，以下使用 `files` 代称）下建立相同的路径，放置同名文件即可替换缓存

如：要替换的文件为 `/resources/app/static/0/v0.4.1.w/scene/Assets/Resource/tablecloth/tablecloth_default/Table_Dif.jpg`

你需要建立路径：

`/resources/app/mod/mymod/files/0/v0.4.1.w/scene/Assets/Resource/tablecloth/tablecloth_default`

并在其下放置名为 `Table_Dif.jpg` 的文件以替换缓存

## 测试&打包模组

打开雀魂 Plus 浏览器，选择左侧的"模组"页面，若前面的步骤进行无误，你应该能看到你自己的模组，模组右下角的开关默认为未启用状态，需要手动启用，可以启动游戏进行测试

测试无问题后，点击右上角纸笔图标，此时模组右下角的开关位置变为了删除和打包选项（再点击一次可恢复），点击打包并选择保存位置即可

## 附录：进阶功能

清单文件中的 `replace` 字段与 `execute` 字段均为可选功能：

- 前者可将不同路径的文件指向同一替换文件，一定程度上防止版本更新造成的 mod 失效 & 避免重复文件难以维护，需要一定正则表达式基础
- 后者可运行自定义脚本以完成一些高级功能，需要一定 `javascript` 基础（请参考 `README` 文档中[开发插件](https://github.com/MajsoulPlus/majsoul-plus#开发插件)部分）

[正则表达式入门教程](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions)

[javascript 入门教程](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/First_steps)

