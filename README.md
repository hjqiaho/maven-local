# maven-local

//maven仓库配置如下
//Users/c30/nee/maven-local 为本地maven仓库地址
```
repositories {
    maven { url 'https://maven.aliyun.com/repository/central' }
    maven { url 'https://maven.aliyun.com/repository/public' }
    mavenCentral()
    google()
    maven { url "https://jitpack.io" }
    maven { url uri("/Users/c30/nee/maven-local") }
}
```


#引入
```
implementation 'com.fundot.local:fundotlauncher:1.0.7'
```


#初始化 在Application 的onCreate方法中

```

FundotLauncherHelper.register(this, object : FundotLauncherHelper.FundotLauncherCallback{
     override fun fundotInfoChange(fundotInfoModel: com.fundot.openinfo.FundotOpenModel) {

    }
})

```
#**********依赖库中相关功能都需要先完成初始化后再使用**********

***获取sn***
```
val sn = FundotLauncherHelper.getData().SerialNumber
```

***加载页面***
```
一起课程 SyncCourseFragment.newInstance()
提升 UpgradeFragment.newInstance()

例如
class MainActivity : BaseActivity(R.layout.activity_main) {
    override fun initView() {
//        loadRootFragment(R.id.fragment_content, SyncCourseFragment.newInstance())
        loadRootFragment(R.id.fragment_content, UpgradeFragment.newInstance())

    }
}
```

***退出登录 桌面有退出登录入口的时候 调用此方法退出到登录页面***
```
FundotLauncherHelper.sendLogoutBoardCast(this)
```

***打开管控后台管理员页面 某些情况下或异常的时候需要打开管理员设置页面修改设备设置 掉用此方法打开管理员页面***
***一般可以放在长按清空缓存，或者连续点击三次logo等隐藏操作中***
```
FundotLauncherHelper.sendOpenAdminBoardCast(this)
```

#引入
***application可能需要***
```
tools:replace="android:allowBackup"
```

***gradle.properties***
```
org.gradle.jvmargs=-Xmx1536m
android.useAndroidX=true
android.enableJetifier=true
```
