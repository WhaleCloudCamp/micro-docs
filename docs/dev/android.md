## Android 端集成

##  1. 获取SDK Key和SDK Secret
使用SDK需要申请SDK Key和SDK Secret，只有在SDK初始化的时候配置了正确的SDK Key和SDK Secret，才能初始化成功并正常使用。

##  2. 导入SDK
### 2.1 添加微应用arr包到工程
从demo工程中把arr包加入到工程中
### 2.2 在gradle中依赖SDK
在gradle文件的dependencies中添加对miniAlita的依赖：

    implementation(name: 'miniAlita_sdk', ext: 'aar')

##  3. SDK初始化
我们强烈建议在Application中对SDK进行初始化，初始化SDK需要传入的各项参数如下：

### 3.1 初始化SDK
在Application的onCreate()下调用初始化接口初始化SDK：

MiniAppConfigure.init(this,"appkey","appSecret");

##  4. SDK使用示例
###  4.1 启动微应用
需要启动微应用，请调用方法：
MiniAppManager.getInstance(mActivity).startWebApp("versionId", "appName", "appid", "version");

###  4.2 获取微应用列表

MiniAppManager.getInstance(this).getWebAppList(new MiniAppManager.RequestCallback() {
            @Override
            public void onError(String errorCode, String errorMessage) {
                //错误日志
            }

            @Override
            public void onSuccess(ArrayList<WebAppBean.WebAppData> records) {
                //列表数据
            }
        });


