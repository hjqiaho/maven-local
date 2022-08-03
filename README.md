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


引入   
```
implementation 'com.fundot.local:fundotlauncher:1.0.4'
```

初始化 在Application 的onCreate方法中

```
FundotOpenInfoHelper.register(this, object : FundotOpenInfoHelper.FunDotInfoCallback{
        override fun fundotInfoChange(fundotOpenModel: FundotOpenModel) {
            //用户信息变化

        }
    })

val sn = FundotOpenInfoHelper.Companion.fundotData.SerialNumber

```

加载页面
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

注意 application可能需要
```
tools:replace="android:allowBackup"
```


gradle.properties

```
org.gradle.jvmargs=-Xmx1536m
android.useAndroidX=true
android.enableJetifier=true
```
