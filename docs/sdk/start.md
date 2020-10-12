# 启动参数

启动参数完全由微应用自由配置，项目参数会通过微应用中的约定和配置来自动产生应用包中的 `asset-manifest.json` 文件。

`asset-manifest.json` 文件包含如下参数，容器在启动微应用时会自动读取，并将其传递给容器本身。

| 名称 | 类型 | 说明 | 默认值 |
|  :-  | :-:  | :-: | :-: |
| name | string | 应用名称 | - |
| version | string | 当前应用版本号，保证唯一值，默认使用生成应用包时的时间戳 | - |
| defaultTitle | string | 默认标题，在页面第一次加载之前显示在标题栏上。 | - |
| readTitle | booble | 是否读取网页标题显示在 titleBar 上。 | true |
| showOptionMenu | booble | 是否显示右上角的“…”按钮。 | true |  |
| toolbarMenu | string | JSON 字符串，更多的菜单项列表（放在分享后面） | - |
| backgroundColor | string | 设置背景颜色 | FFFFFF |
