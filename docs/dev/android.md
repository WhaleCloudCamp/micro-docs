## Android 端集成

##  1. 获取 SDK Key 和 SDK Secret
使用SDK需要申请SDK Key 和 SDK Secret，只有在 SDK 初始化的时候配置了正确的 SDK Key，才能初始化成功并正常使用。

##  2. 导入 SDK
### 2.1 maven依赖配置
在工程build.gradle配置脚本中buildscript和allprojects段中添加maven仓库地址

       maven { url 'https://jitpack.io' }

### 2.2 在 gradle 中依赖 SDK
在 gradle 文件的 dependencies 中添加对 AlitaNativeLib 的依赖：

       implementation 'com.github.alitajs:micro-app-android-framework:1.0.16'

##  3. SDK 初始化
我们强烈建议在 Application 中对 SDK 进行初始化，初始化 SDK 需要传入的各项参数如下：

### 3.1 初始化 SDK
在 Application 的 onCreate() 下调用初始化接口初始化 SDK：

        AlitaConfigure.init(this,"appkey");

### 3.2 日志开关
在 Application 的 onCreate() 下开启日志开关，默认关闭：

        AlitaConfigure.setLogEnable(true);

##  4. SDK 使用示例
###  4.1 启动微应用
需要启动微应用，请调用方法：

        AlitaManager.getInstance(Activity).startMicorApp(MicorAppBean.MicorAppData, "userData");

启动微应用，若需要下载回调，请调用方法：

        AlitaManager.getInstance(Activity).startMicorApp(MicorAppBean.MicorAppData, "userData", DownloadCallback);

###  4.2 获取微应用列表

        AlitaManager.getInstance(Activity).getMicorAppList(new AlitaManager.RequestCallback() {

            @Override
            public void onError(String errorCode, String errorMessage) {
                //错误日志
            }

            @Override
            public void onSuccess(ArrayList<MicorAppBean.MicorAppData> datas) {
                //列表数据
            }
        });

###  4.3 初始化下载loading弹窗
请在启动微应用之前初始化，只需调用一次即可，未初始化则下载不会有默认的loading弹窗调用方法：

       AlitaManager.getInstance(this).initLoadingDialog(R.color.colorValue);

