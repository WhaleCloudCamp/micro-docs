# 原生能力

## 扫码解析
```js
    const res = await alita.device.scanCode(params);
```
### 参数
**Object params**

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| :- | :- | :- | :- | :- |
| onlyFromCamera | boolean | false | 否 | 是否只能从相机扫码，不允许从相册选择图片 |
| scanType | Array<string\> | ['qrCode'] | 否 | 扫码类型，目前只支持二维码 |

### 响应
**Object res**

| 属性 | 类型 | 说明 |
| :- | :- | :- |
| result | string | 所扫码的内容 |


## 获取相册
```js
    const res = await alita.media.chooseImage(params);
```

### 参数
**Object params**

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| :- | :- | :- | :- | :- |
| count | number | 9 | 否 | 最多可以选择的图片张数 |
| sizeType | Array<string\> | ['compressed'] | 否 | 所选的图片的尺寸，可选值`original`，`compressed`。建议使用`compressed`，图片会小很多 |
| sourceType | Array<string\> | ['album', 'camera'] | 否 | 选择图片的来源 |
| base64 | bool | true | 否 | 是否需要 `base64` 数据 |

### 响应
**Object res**

| 属性 | 类型 | 说明 |
| :- | :- | :- |
| files | Array<Object\> | 图片对象数组 |


**res.files**

| 属性 | 类型 | 说明 |
| :- | :- | :- |
| path | string | 原图本地文件路径，当`sizeType`包含`original`时返回 |
| thumbnail | string | 压缩图本地文件路径，当`sizeType`包含`compressed`时返回 |
| base64 | string | base64 数据，当入参`base64`为true时，返回 |

