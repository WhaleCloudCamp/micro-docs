# 原生能力

## 扫码解析


## 获取相册
### `alita.media.chooseImage`
```js
    try {
        const data: ChooseImageResult = await alita.media.chooseImage(params: ChooseImageParams);
    } catch (e) {

    }
```

`ChooseImageParams`: Object  

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| :- | :- | :- | :- | :- |
| count | number | 9 | 否 | 最多可以选择的图片张数 |
| sizeType | Array<string\> | ['original', 'compressed'] | 否 | 所选的图片的尺寸 |
| sourceType | Array<string\> | ['album', 'camera'] | 否 | 选择图片的来源 |
| base64 | bool | true | 否 | 是否需要 `base64` 数据 |


`ChooseImageResult`: Object  

| 属性 | 类型 | 说明 |
| :- | :- | :- |
| files | Array<ChooseImageResultItem\> | 图片对象数组 |


`ChooseImageResultItem`: Object

| 属性 | 类型 | 说明 |
| :- | :- | :- |
| path | string | 本地文件路径 |
| base64 | string | base64 数据，当入参base64为true时，返回该字段 |

