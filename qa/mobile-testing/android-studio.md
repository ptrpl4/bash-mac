# 🟢 Android Studio

#### links

* [https://developer.android.com/studio/run/emulator-commandline](https://developer.android.com/studio/run/emulator-commandline)

#### shell config

```
export ANDROID_HOME=~/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
export PATH=$PATH:$ANDROID_HOME/platform-tools
```

### emulator

syntax

```bash
emulator -avd avd_name [ {-option [value]} … ]
```

examples

```bash
# check ver
emulator -version

# list of AVD names
emulator -list-avds

# run
emulator -avd Pixel_3_API_30 -memory 1024 -partition-size 512 -no-boot-anim
emulator @Pixel_3a_API_34_extension_level_7_arm64-v8a -memory 1024 -partition-size 512 -no-boot-anim
```

#### Using local sockets

use 10.0.2.2

```
http://10.0.2.2:4200/
```
