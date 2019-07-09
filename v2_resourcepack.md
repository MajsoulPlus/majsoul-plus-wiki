# 创建资源包（Resource Pack）[实现中]

在 `2.x` 版本的 雀魂 Plus 中，加入了资源包的设定，以取代原本的模组。资源包是原本模组的实质意义，并且在 `1.x` 模组的基础上增加了一些功能，以更方便素材的更改。

下面将简单介绍资源包的格式与规范。

## 资源路径（resource domain）

每个资源包都需要有一个唯一的资源路径。类似雀魂官方的 `v0.5.1.w`。在实际寻找资源时，雀魂 Plus 会替换原有的资源路径，以达到替换素材的目的。

## 目录格式

雀魂 Plus 资源包的目录格式如下所示：

```
- resource_pack_name
  - resource_pack.json
  - assets
    - folderA
      - fileBinFolderA.png
    - fileA.png
```

其中，resource_pack.json 负责描述该资源包的信息，而 `assets` 目录下负责存储该资源包对应资源路径的实际内容。

## resource_pack.json

下面给出一个资源包的 `resource_pack.json` 的样例：

```json
{
  "domain": "sample",
  "name": "sample_pack",
  "version": "1.0.0",
  "author": "Majsoul Plus Team",
  "description": "This is a sample resource pack.",
  "preview": "preview.png",

  "dependencies": {
    "majsoul": "^v0.5.1w",
    "majsoul_plus": "^2.0.0"
  },
  "replace": [
    "audio/sound/zeniya/fan_dora10.mp3",
    "scene/Assets/Resource/mjpai/en/mjp_default_0/8p.png"
  ]
}
```

## 可以执行的脚本呢？

由于功能调整，雀魂 Plus 中的资源包目前只能起到替换资源的作用。想要实现更强大的功能，请参考[拓展](v2_extension)。
