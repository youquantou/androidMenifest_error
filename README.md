# androidMenifest_error
androidManifest爆红处理方法

app下的build.gradle
apply plugin: 'com.android.application'

android {
    compileSdkVersion 22
    defaultConfig {
        applicationId "com.boya.idcardusb"

        minSdkVersion 19
        targetSdkVersion 22
        ndk {
            // 设置支持的SO库架构
            abiFilters 'armeabi-v7a' //, 'x86', 'armeabi-v7a', 'x86_64', 'arm64-v8a'
        }
    }

    sourceSets.main {
        jni.srcDirs = []
        jniLibs.srcDir "libs"
    }

    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.txt'
        }
    }
    
添加下列两句话 
    lintOptions {
        checkReleaseBuilds false
        abortOnError false
    }
添加上列两句话 
    productFlavors {
    }
}

dependencies {
    implementation fileTree(include: ['*.jar'], dir: 'libs')
    //compile 'com.android.support:support-v4:19.1.0'
//    compile 'io.github.silvaren:easyrs:0.5.3'
    // compile fileTree(include: ['*.jar'], dir: 'libs')
   // compile 'com.github.CymChad:BaseRecyclerViewAdapterHelper:2.9.22'
    //    implementation fileTree(dir: 'libs', include: ['*.jar'])
    //    compile 'com.android.support:appcompat-v7:26.0.0-beta1'
//    compile 'com.android.support.constraint:constraint-layout:1.0.2'
//    compile 'com.github.bumptech.glide:glide:3.7.0'
//   // compile 'com.android.support:appcompat-v7:26.0.1'
//   // compile 'com.android.support:recyclerview-v7:26.0.1'
//    compile files('libs/sdtapi.jar')
}
