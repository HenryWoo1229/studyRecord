# gradle 里设置 Android 签名

标签（空格分隔）： Android

---

1. 通过 Android Studio 生成 keystore，记住密码和设置的一些信息 （build signed apk 时可以 create）
2. 将 keystore 文件放到工程的 app 目录下
3. app/build.gradle 添加如下信息
```
signingConfigs {
        debug {
            storeFile file("vehicletest_debug.jks")  // keystore
            storePassword "12345678"
            keyAlias "debug"
            keyPassword "12345678"
        }
        release {
        }
    }
    
buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
        debug {
            signingConfig signingConfigs.debug   // 引用签名文件
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
```
4. 查看 keystore 文件信息的命令，需要记住设置的密码
```
keytool.exe -v -list -keystore vehicletest_debug.jks
```



