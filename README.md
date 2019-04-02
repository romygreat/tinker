# tinker
使用方法
1、首先在工程gradle添加

classpath "com.tencent.tinker:tinker-patch-gradle-plugin:${TINKER_VERSION}"


2、然后在app gralde 中添加

  implementation("com.tencent.tinker:tinker-android-lib:${TINKER_VERSION}") { changing = true }
    // Maven local cannot handle transist dependencies.
    implementation("com.tencent.tinker:tinker-android-loader:${TINKER_VERSION}") { changing = true }
    annotationProcessor("com.tencent.tinker:tinker-android-anno:${TINKER_VERSION}") { changing = true }
    compileOnly("com.tencent.tinker:tinker-android-anno:${TINKER_VERSION}") { changing = true }
    implementation "com.android.support:multidex:1.0.1"
    
    
3、在gradle.properties添加

GRADLE_3=true
TINKER_VERSION=1.9.2
TINKERPATCH_VERSION=1.2.2


4、在app gradle添加
def javaVersion = JavaVersion.VERSION_1_7
android {
    compileSdkVersion 28
    compileOptions {
        sourceCompatibility javaVersion
        targetCompatibility javaVersion
    }
    //recommend
    dexOptions {
        jumboMode = true
        javaMaxHeapSize "4g"
    }
    在defaultConfig添加
    multiDexEnabled true
    后面参考app gradle
 5、复制官方的demo源码
 
 构建使用
 1、assembleDebug
 2、修改app gradle生成的app,在bak目录中
 2、tinkerPatchDebug
 最后使用adb push /sdcard/patch_signed_7zip.apk
 小米8使用测试出现有bug

