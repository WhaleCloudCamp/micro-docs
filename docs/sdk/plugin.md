# 自定义插件

由于无法覆盖所有原生能力，我们为主应用提供了自定义插件给微应用调用的能力。

## iOS 自定义插件

1. 新建一个类继承 `AlitaPlugin`，实现 `pluginName` 和 `methodsList` 方法。`pluginName` 是插件名字，`methodsList` 是插件名列表，js 里通过 `pluginName` 和 `methodsList` 里方法名查找方法进行调用

```objc
#import <AlitaNativeLib/AlitaNativeLib.h>

@interface CustomPlugin : AlitaPlugin

@end

@implementation CustomPlugin

+ (NSString *)pluginName {
    return @"custom";
}

+ (NSArray *)methodsList {
    return @[@"echo"];
}

// 和 methodsList 里方法名相对应
- (void)echo:(AlitaCommand *)command {
    id params = command.params;
    // 使用 AlitaCommandResult 构造返回参数给 js
    NSDictionary *result = [AlitaCommandResult resultWithStatus:AlitaCommandStatus_OK message:@"success" responseData:params];
    command.responseCallback(result);
}

@end
```

2. 在原生注册插件

```objc
#import <AlitaNativeLib/AlitaNativeLib.h>
#import "CustomPlugin.h"
...
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    ...
    CustomPlugin *plugin = [CustomPlugin new];
    [AlitaNative registerPlugin:plugin];
    ...
}
```

3. 在 js 注册插件

```js
const CustomPlugin = {
  pluginName: "custom",
  methodsList: ["echo"],
};

if (window.alitanative && !window.WebViewJavascriptBridge) {
  document.addEventListener("AlitaBridgeReady", () => {
    window.WebViewJavascriptBridge.registerPlugin(CustomPlugin);
  });
} else {
  window.WebViewJavascriptBridge.registerPlugin(CustomPlugin);
}
```

4. 在 js 中使用插件

```js
alita.custom.echo("hello world").then((data) => {
  alert("echo:" + data);
});
```
