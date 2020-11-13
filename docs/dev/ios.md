## iOS 接入
在 `Podfile` 文件（没有的话在工程根目录运行 `pod init` 新建）加入：
```ruby
pod 'AlitaNativeLib', :git => 'https://github.com/alitajs/micro-app-ios-framework.git'
```
然后运行
```sh
pod install
```

## 接口
### 注册主应用
```objc
#import <AlitaNativeLib/AlitaNativeLib.h>

@implementation AppDelegate

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // xxx 替换成主应用id
    [AlitaNative registerWithAppId:@"xxx"];
    return YES;
}

@end
```
### 获取微应用列表
```objc
#import <AlitaNativeLib/AlitaNativeLib.h>
...
__weak typeof(self) weakSelf = self;
[AlitaMicroApp microAppListWithCallback:^(NSArray<AlitaMicroApp *> * _Nullable list, AlitaPagination * _Nullable pagination, NSError * _Nullable error) {
        NSLog(@"%@\n%@\n%@", list, pagination, error);
        weakSelf.appList = list;
        [weakSelf.tableView reloadData];
    }]
```
### 打开微应用
```objc
AlitaMicroApp *app = self.appList[indexPath.row];
[AlitaNative viewController:self openMicroApp:app withUserData:@{} completion:^(NSError * _Nullable error) {
        if (error) {
            NSLog(@"%@", error.localizedDescription);
        }
    }];
```

### 例子
https://github.com/WhaleCloudCamp/micro-app-example-ios.git
