# ijkplayer



### Before Build
```
下载安装android studio:版本4.0
在android studio 中下载安装
cmake:版本3.18.1
ndk:版本:16.1.4479499

# install homebrew, git, yasm
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew install git
brew install yasm

# add these lines to your ~/.bash_profile or ~/.profile
# export ANDROID_SDK=<your sdk path>
# export ANDROID_NDK=<your ndk path>
# export ANDROID_CMAKE_BIN=<your cmake bin path> 即cmake命令所在的文件夹


# on Cygwin (unmaintained)
# install git, make, yasm
```

- For Ubuntu/Debian users.
```
# choose [No] to use bash
sudo dpkg-reconfigure dash
```

- If you'd like to share your config, pull request is welcome.

### Build Android
```
git clone https://github.com/befovy/ijkplayer.git ijkplayer-android
cd ijkplayer-android
./init-android.sh
cd android/contrib
./compile-openssl.sh all
./compile-libsrt.sh all
./compile-ffmpeg.sh all
Open Android peoject in android/ijkplayer using Android Studio
run/debug ijkplayer-example in Android Studio

To get a released aar
run `./gradlew :fijkplayer-full:assembleRelease`

```

### Build iOS
```
git clone https://github.com/befovy/ijkplayer.git ijkplayer-ios
cd ijkplayer-ios
git checkout -B latest k0.8.8

./init-ios.sh

cd ios
./compile-ffmpeg.sh clean
./compile-ffmpeg.sh all

# Demo
#     open ios/IJKMediaDemo/IJKMediaDemo.xcodeproj with Xcode
# 
# Import into Your own Application
#     Select your project in Xcode.
#     File -> Add Files to ... -> Select ios/IJKMediaPlayer/IJKMediaPlayer.xcodeproj
#     Select your Application's target.
#     Build Phases -> Target Dependencies -> Select IJKMediaFramework
#     Build Phases -> Link Binary with Libraries -> Add:
#         IJKMediaFramework.framework
#
#         AudioToolbox.framework
#         AVFoundation.framework
#         CoreGraphics.framework
#         CoreMedia.framework
#         CoreVideo.framework
#         libbz2.tbd
#         libz.tbd
#         MediaPlayer.framework
#         MobileCoreServices.framework
#         OpenGLES.framework
#         QuartzCore.framework
#         UIKit.framework
#         VideoToolbox.framework
#
#         ... (Maybe something else, if you get any link error)
# 
```

### Build for Mac OS

Build ffmpeg for Max OS
```
./init-osx.sh
cd osx && ./compile-ffmpeg.sh
```

Build ijkplayer for Max OS

```
cd desktop
mkdir cmake-build-debug && cd cmake-build-debug
cmake .. -DCMAKE_BUILD_TYPE="Debug"
make IjkPlayer
make tuidemo
```

**Or you can open ijkplayer as a CMakeLists.txt project using Clion.**

tuidemo is a terminal UI demo for ijkplayer in progress, it can't display video yet.

`libIjkPlayer.dylib` is the output dynamic library.

### Support (支持) ###

- Please do not send e-mail to me. Public technical discussion on github is preferred.
- 请尽量在 github 上公开讨论[技术问题](https://github.com/befovy/ijkplayer/issues)，不要以邮件方式私下询问，恕不一一回复。


### License

```
Copyright (c) 2017 Bilibili
Licensed under LGPLv2.1 or later
```

ijkplayer required features are based on or derives from projects below:
- LGPL
  - [FFmpeg](http://git.videolan.org/?p=ffmpeg.git)
  - [libVLC](http://git.videolan.org/?p=vlc.git)
  - [kxmovie](https://github.com/kolyvan/kxmovie)
  - [soundtouch](http://www.surina.net/soundtouch/sourcecode.html)
- zlib license
  - [SDL](http://www.libsdl.org)
- BSD-style license
  - [libyuv](https://code.google.com/p/libyuv/)
- ISC license
  - [libyuv/source/x86inc.asm](https://code.google.com/p/libyuv/source/browse/trunk/source/x86inc.asm)

android/ijkplayer-exo is based on or derives from projects below:
- Apache License 2.0
  - [ExoPlayer](https://github.com/google/ExoPlayer)

android/example is based on or derives from projects below:
- GPL
  - [android-ndk-profiler](https://github.com/richq/android-ndk-profiler) (not included by default)

ios/IJKMediaDemo is based on or derives from projects below:
- Unknown license
  - [iOS7-BarcodeScanner](https://github.com/jpwiddy/iOS7-BarcodeScanner)

ijkplayer's build scripts are based on or derives from projects below:
- [gas-preprocessor](http://git.libav.org/?p=gas-preprocessor.git)
- [VideoLAN](http://git.videolan.org)
- [yixia/FFmpeg-Android](https://github.com/yixia/FFmpeg-Android)
- [kewlbear/FFmpeg-iOS-build-script](https://github.com/kewlbear/FFmpeg-iOS-build-script) 

### Commercial Use
ijkplayer is licensed under LGPLv2.1 or later, so itself is free for commercial use under LGPLv2.1 or later

But ijkplayer is also based on other different projects under various licenses, which I have no idea whether they are compatible to each other or to your product.

[IANAL](https://en.wikipedia.org/wiki/IANAL), you should always ask your lawyer for these stuffs before use it in your product.
