# 2.x 迁移指南

## 模组 -> 资源包

下文针对的是**只有资源替换**的模组，如果涉及到了代码，请迁移到*扩展*。

下文以修改默认桌布为例。

对于你想要替换的素材，首先你先要找到它的路径。在案例中，其路径为 `scene/Assets/Resource/tablecloth/tablecloth_default/Table_Dif.jpg`。

接下来需要的是你存放文件的路径。所有文件**必须**存放在 `assets` 目录下，你需要记下的是该文件相对 `assets` 目录的相对路径。在案例中，我们的文件名为 `Table_Dif.jpg`。

然后，你需要确定是否开启强制外服兼容。在案例中，我们选择开启。

最后，你需要在 `replace` 数组中加上这样的一项：

```json
{
  "replace": [
    {
      "from": "scene/Assets/Resource/tablecloth/tablecloth_default/Table_Dif.jpg",
      "to": "Table_Dif.jpg",
      "all-servers": true
    }
  ]
}
```

重复这样的过程，直到所有素材均替换完成。

## 插件 -> 扩展

对于单纯插件的迁移，你只需要修改描述文件即可。

## 模组 -> 扩展

将上述二者综合即可。

## 我在界面里看不到我的资源包/扩展/工具？

请详细阅读 [进阶概念](https://github.com/MajsoulPlus/majsoul-plus/wiki/v2_advanced#拓展的检查顺序)，你会在那里找到答案。
