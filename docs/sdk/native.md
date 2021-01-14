# 原生能力

## 获取原生参数
```js
    cons res = await alita.device.getUserData();
```
### 参数
无
### 响应
**Object res**

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

## 获取系统信息
```js
const res = await alita.device.systemInfo();
```
### 参数
### 响应
**Object res**

| 属性 | 类型 | 说明 |
| :- | :- | :- |
| platform | string | `ios` or `android` |
| version | string | 主app版本，如1.0.0 |
| uuid | string | 设备唯一标识 |
| statusBarHeight | number | 导航栏高度 |
| SDKVersion | string | 微应用基础库版本号，如1.0.0 |

## 打开web页面
```js
alita.device.openWeb(url: string)
```
### 参数
**String url**

| 属性 | 类型 | 说明 |
| :- | :- | :- |
| url | string | 要打开的URL |

### 响应

## 打开文件
```js
alita.file.openDocument(params: {url: string});
```
支持 doc、xls、ppt、pdf 等格式

### 参数
**Object params**

| 属性 | 类型 | 说明 |
| :- | :- | :- |
| url | string | 要打开文件的URL |

### 响应

## 下载保存文件到本地
```js
alita.file.saveFile(params: {url: string});
```

### 参数
**Object params**

| 属性 | 类型 | 说明 |
| :- | :- | :- |
| url | string | 要保存文件的URL |

### 响应

## 获取微应用列表
```js
const res = await alita.device.fetchMicroAppList();
```
### 参数
无
### 响应
**Array<`MicroApp`\> res**

`MicroApp`: 微应用对象

| 属性 | 类型 | 说明 |
| :- | :- | :- |
| appid | string | 微应用唯一标识 |
| appsecret | string | 微应用 `appsecret` |
| appName | string | 微应用名称 |
| appDesc | string | 微应用描述 |
| appIconUrl | string | 微应用缩略图链接 |
| versionId | string | 微应用版本 id |

## 打开微应用
```js
const res = await alita.device.openMicroApp(params);
```
### 参数
**Object params**

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| :- | :- | :- | :- | :- |
| app | `MicroApp` | 无 | app 或 appURL 必传其一 | 要打开的微应用对象 |
| appURL | string | 无 | app 或 appURL 必传其一 | 要打开的微应用链接 |
| userData | object | 无 | 否 | 传给要打开微应用的参数 |

## 查询安装的地图

```js
const res = await alita.device.mapsList();
```

### 参数
无

### 响应

**Array<Map\>** res

`Map`: 地图对象

| 属性 | 类型 | 说明 |
| :- | :- | :- |
| type | string | `baidu` \| `amap` \| `apple` \| `google` \| `qq` |

### 配置

`iOS` 需要在 `Info.plist` 中的 `LSApplicationQueriesSchemes` 加下面几个 URLScheme

- baidumap
- iosamap
- comgooglemaps
- qqmap


## 打开 URLScheme

```js
alita.device.openURLScheme(params: { url: string });
```

### 参数

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| :- | :- | :- | :- | :- |
| url | string | 无 | 是 | 要打开的`URLSchema` |

### 响应

无

## 获取当前位置

```js
const location = await alita.location.getLocation();
```

### 参数

无

### 响应

| 属性 | 类型 | 说明 |
| :- | :- | :- |
| latitude | number | 纬度，范围为 -90~90，负数表示南纬 |
| longitude | number | 经度，范围为 -180~180，负数表示西经 |

## js 给原生发送通知

```js
alita.notice.postMessage({
    name: '通知名',
    userInfo: {},
});
```

### 参数

| 属性 | 类型 | 默认值 | 必填 | 说明 |
| :- | :- | :- | :- | :- |
| name | string | 无 | 是 | 通知名 |
| userInfo | { [key string]: any } | 无 | 否 | 额外参数 |

### 响应

无