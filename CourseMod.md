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
推荐放置一个方形预览图以更加简单地描述本模组的作用
并在其下放置名为 `Table_Dif.jpg` 的文件以替换缓存
## 清单文件
## 测试&打包模组

打开雀魂 Plus 浏览器，选择左侧的"模组"页面，若前面的步骤进行无误，你应该能看到你自己的模组，模组右下角的开关默认为未启用状态，需要手动启用，可以启动游戏进行测试
  "author": "Handle",
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
推荐放置一个方形预览图以更加简单地描述本模组的作用
并在其下放置名为 `Table_Dif.jpg` 的文件以替换缓存
## 清单文件
## 测试&打包模组

打开雀魂 Plus 浏览器，选择左侧的"模组"页面，若前面的步骤进行无误，你应该能看到你自己的模组，模组右下角的开关默认为未启用状态，需要手动启用，可以启动游戏进行测试
  "author": "Handle",
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

## 文件结构

你可以先启动一次游戏，确保需要替换的缓存已经被加载，然后在雀魂 Plus 浏览器的 `static` 文件夹下寻找需要替换的缓存文件（善用搜索功能，绝大多数是拼音命名……），记住其路径，在 mod 的 `files` 文件夹（可通过清单文件进行配置，以下使用 `files` 代称）下建立相同的路径，放置同名文件即可替换缓存

如：要替换的文件为 `/resources/app/static/0/v0.4.1.w/scene/Assets/Resource/tablecloth/tablecloth_default/Table_Dif.jpg`

你需要建立路径：

`/resources/app/mod/mymod/files/0/v0.4.1.w/scene/Assets/Resource/tablecloth/tablecloth_default`
推荐放置一个方形预览图以更加简单地描述本模组的作用
并在其下放置名为 `Table_Dif.jpg` 的文件以替换缓存
## 清单文件
## 测试&打包模组

打开雀魂 Plus 浏览器，选择左侧的"模组"页面，若前面的步骤进行无误，你应该能看到你自己的模组，模组右下角的开关默认为未启用状态，需要手动启用，可以启动游戏进行测试
  "author": "Handle",
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
推荐放置一个方形预览图以更加简单地描述本模组的作用
并在其下放置名为 `Table_Dif.jpg` 的文件以替换缓存
## 清单文件
## 测试&打包模组

打开雀魂 Plus 浏览器，选择左侧的"模组"页面，若前面的步骤进行无误，你应该能看到你自己的模组，模组右下角的开关默认为未启用状态，需要手动启用，可以启动游戏进行测试
  "author": "Handle",
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
推荐放置一个方形预览图以更加简单地描述本模组的作用
并在其下放置名为 `Table_Dif.jpg` 的文件以替换缓存
## 清单文件
## 测试&打包模组

打开雀魂 Plus 浏览器，选择左侧的"模组"页面，若前面的步骤进行无误，你应该能看到你自己的模组，模组右下角的开关默认为未启用状态，需要手动启用，可以启动游戏进行测试
  "author": "Handle",
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
      "to": "/0/v0.4.1.w/myres2/tablecloth/tablecloth_default/preview\\.jpg"
    }

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
