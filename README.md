# maven-local

//maven仓库配置如下
//Users/c30/nee/maven-local 为本地maven仓库地址

repositories {
    maven { url 'https://maven.aliyun.com/repository/central' }
    maven { url 'https://maven.aliyun.com/repository/public' }
    mavenCentral()
    google()
    maven { url "https://jitpack.io" }
    maven { url uri("/Users/c30/nee/maven-local") }
}
