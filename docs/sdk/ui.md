# 页面

## 设置导航栏

此接口用于设置 NavBar 。

### 使用方法

```js
alita.ui.setNavBar({
  backgroundColor: '#FFF', // 背景颜色
  color:'#000', // 标题字体颜色、返回按钮、关闭按钮颜色
  fontSize:'24', // 标题字号
});
```

## 设置导航栏标题

设置项目的 document.title，容器会自动修改导航栏标题。

### 使用方法

在项目中使用

```
import React from 'react';
import { Helmet } from 'alita';
const Application = () => {
 return (
    <div className="application">
      <Helmet>
        <title>My Title</title>
      </Helmet>
    </div>
  );
}
export default Application;
```

## 设置 `WebView` 背景色

设置加载h5的`WebView`背景颜色

### 使用方法

```js
alita.ui.setBackgroundColor({ backgroundColor: '#0000FF' });
```
