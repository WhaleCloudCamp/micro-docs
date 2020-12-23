# 非 Alita 开发

本文介绍 js 不使用 alita 怎么开发微应用

## 原生集成 sdk

原生还是得按原来那样集成相应 sdk

## js 配置

1. 安装 `alita-micro`

```js
yarn add alita-micro
```

2. 等待初始化完成

判断 `window.alitanative` 和 `window.WebViewJavascriptBridge` 是否存在，如果存在表示已经初始化，可以正常使用 alita 插件。如果不存在，则监听 `AlitaBridgeReady` 事件，当该事件发生表示初始化完成，可以正常使用 alita 插件

```js
import "../styles/globals.css";
import { useEffect, useState } from "react";

function MyApp({ Component, pageProps }) {
  const [isAlitaMicroLoaded, setIsAlitaMicroLoaded] = useState(false);
  useEffect(() => {
    const initAlita = async () => {
      await import("alita-micro");
      // window.alitanative 存在：表示是 微应用 环境 或 微应用开发环境，此时要等待 WebViewJavascriptBridge 初始化完成
      if (window.alitanative && !window.WebViewJavascriptBridge) {
        document.addEventListener("AlitaBridgeReady", () => {
          setIsAlitaMicroLoaded(true);
        });
      } else {
        setIsAlitaMicroLoaded(true);
      }
    };
    initAlita();
  }, []);
  return isAlitaMicroLoaded ? <Component {...pageProps} /> : null;
}

export default MyApp;
```
