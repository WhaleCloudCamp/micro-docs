# File

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
无