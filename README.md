# tinker
ʹ�÷���
1�������ڹ���gradle���

classpath "com.tencent.tinker:tinker-patch-gradle-plugin:${TINKER_VERSION}"
2��Ȼ����app gralde �����

  implementation("com.tencent.tinker:tinker-android-lib:${TINKER_VERSION}") { changing = true }
    // Maven local cannot handle transist dependencies.
    implementation("com.tencent.tinker:tinker-android-loader:${TINKER_VERSION}") { changing = true }
    annotationProcessor("com.tencent.tinker:tinker-android-anno:${TINKER_VERSION}") { changing = true }
    compileOnly("com.tencent.tinker:tinker-android-anno:${TINKER_VERSION}") { changing = true }
    implementation "com.android.support:multidex:1.0.1"
3����gradle.properties���
GRADLE_3=true
TINKER_VERSION=1.9.2
TINKERPATCH_VERSION=1.2.2
4����app gradle���
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
    ��defaultConfig���
    multiDexEnabled true
    ����ο�app gradle
 5�����ƹٷ���demoԴ��
 ����ʹ��
 1��assembleDebug
 2���޸�app gradle���ɵ�app,��bakĿ¼��
 2��tinkerPatchDebug
 ���ʹ��adb push /sdcard/patch_signed_7zip.apk
 С��8ʹ�ò��Գ�����bug

