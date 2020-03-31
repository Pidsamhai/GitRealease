# GitRelease
[![](https://jitpack.io/v/Pidsamhai/GitRelease.svg)](https://jitpack.io/#Pidsamhai/GitRelease)

<p align="center">
<img src="./art/vdo.gif" height="600" />
</p>

## Jitpack
```kotlin
allprojects {
  repositories {
    ...
    maven { url 'https://jitpack.io' }
  }
}
```
```kotlin
dependencies {
  implementation 'com.github.Pidsamhai:GitRelease:0.1-alpha'
  // This project uses kotlinx-coroutines.
  implementation 'org.jetbrains.kotlinx:kotlinx-coroutines-android:1.3.5'
}
```
## Setup
Permission AndroidManifest.xml
```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.REQUEST_INSTALL_PACKAGES"/>
```
Add file provider in application tag
```xml
<provider
            android:authorities="{Your package name}.provider" 
            android:name="androidx.core.content.FileProvider"
            android:grantUriPermissions="true"
            android:exported="false">
            <meta-data
                android:name="android.support.FILE_PROVIDER_PATHS"
                android:resource="@xml/filepath"/>
</provider>
```
filepath.xml   res > xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<paths>
    <external-files-path name="files" path="." />
</paths>
```
## Quick start
```kotlin
class MainActivity : AppCompatActivity() {

    @SuppressLint("SetTextI18n")
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        
        val owner = "Pidsamhai"
        val repo = "release_file_test"
        val currentVersion = BuildConfig.VERSION_NAME
        
        val gitRelease = GitRelease(this, owner, repo, currentVersion).apply {
            loading = true
            title = "Massage Test"
            massage = "Title Test"
        }
        
        gitRelease.checkNewVersion()
    }
}
```
## License
```
            DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE
                    Version 2, December 2004

 Copyright (C) 2020 Pidsamhai <meng348@gmail.com>

 Everyone is permitted to copy and distribute verbatim or modified
 copies of this license document, and changing it is allowed as long
 as the name is changed.

            DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE
   TERMS AND CONDITIONS FOR COPYING, DISTRIBUTION AND MODIFICATION

  0. You just DO WHAT THE FUCK YOU WANT TO.
```
