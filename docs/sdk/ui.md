# 页面

## 前置配置

有时候需要在打开微应用之前，就对微应用 ui 做一个设置，比如微应用中使用暗黑模式等情况，可以在 `config/config.ts` 中前置配置一下的参数。

```bash
  microTheme: {
    navBar: {
      backgroundColor: '#FFF',
        color: '#000',
          fontsize: '24',
            display: "flex",
    },
    backgroundColor: '#FFF',
  }
```

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

## 设置状态栏颜色

目前只支持黑色和白色

### 使用方法

```js
alita.ui.setStatusBar({ theme: 'light' | 'dark' });
```