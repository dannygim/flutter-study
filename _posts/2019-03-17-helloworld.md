---
layout: post
title:  "Hello World!"
date:   2019-03-17 00:01:03 +0900
categories: jekyll update
---
## Let's start to study about [Flutter](https://flutter.dev/).
Flutter勉強を始めよう。
まずはFlutter公式サイトの[Get started](https://flutter.dev/docs/get-started/install)から。

## Flutter install
macOSのインストール [https://flutter.dev/docs/get-started/install/macos](https://flutter.dev/docs/get-started/install/macos)

#### Flutter SDK

```sh
$ mkdir -p ~/Documents/tools/flutter
$ cd ~/Documents/tools/flutter
$ unzip ~/Downloads/flutter_macos_v1.2.1-stable.zip
$ echo "export PATH="$PATH:~/Documents/tools/flutter/bin" >> ~/.bash_profile
$ source ~/.bash_profile
```

#### Run flutter doctor

`flutter doctor` を実行すると必要なDependencyなどがチェックできるらしい。

```
$ flutter doctor
Doctor summary (to see all details, run flutter doctor -v):
[✓] Flutter (Channel stable, v1.2.1, on Mac OS X 10.14.3 18D109, locale en-US)
[!] Android toolchain - develop for Android devices (Android SDK version 28.0.3)
    ✗ Android licenses not accepted.  To resolve this, run: flutter doctor --android-licenses
[!] iOS toolchain - develop for iOS devices (Xcode 10.1)
    ✗ libimobiledevice and ideviceinstaller are not installed. To install with Brew, run:
        brew update
        brew install --HEAD usbmuxd
        brew link usbmuxd
        brew install --HEAD libimobiledevice
        brew install ideviceinstaller
    ✗ ios-deploy not installed. To install:
        brew install ios-deploy
    ✗ CocoaPods not installed.
        CocoaPods is used to retrieve the iOS platform side's plugin code that responds to your
        plugin usage on the Dart side.
        Without resolving iOS dependencies with CocoaPods, plugins will not work on iOS.
        For more info, see https://flutter.io/platform-plugins
      To install:
        brew install cocoapods
        pod setup
[!] Android Studio (version 3.2)
    ✗ Flutter plugin not installed; this adds Flutter specific functionality.
    ✗ Dart plugin not installed; this adds Dart specific functionality.
[✓] VS Code (version 1.32.3)
[!] Connected device
    ! No devices available

! Doctor found issues in 4 categories.
```

いろいろ言われてるけどとりあえず`iOS toolchain`のところだけ対応してみる。

対応後再度チェック。`iOS toolchain`の**✗**が消えた。

```
$ flutter doctor
Doctor summary (to see all details, run flutter doctor -v):
[✓] Flutter (Channel stable, v1.2.1, on Mac OS X 10.14.3 18D109, locale en-US)
[!] Android toolchain - develop for Android devices (Android SDK version 28.0.3)
    ✗ Android licenses not accepted.  To resolve this, run: flutter doctor --android-licenses
[✓] iOS toolchain - develop for iOS devices (Xcode 10.1)
[!] Android Studio (version 3.2)
    ✗ Flutter plugin not installed; this adds Flutter specific functionality.
    ✗ Dart plugin not installed; this adds Dart specific functionality.
[✓] VS Code (version 1.32.3)
[!] Connected device
    ! No devices available

! Doctor found issues in 3 categories.
```

#### Create and run Flutter app

`helloworld` projectを作ってシミュレーターで動かしてみる。

```
$ flutter create helloworld
$ cd helloworld
$ open -a Simulator
$ flutter run
```

特に問題なく動いた。

![first flutter app]({{ site.baseurl }}/assets/2019/03/17/1.png)

自動生成された`lib/main.dart`のコードを消してシンプルに Hello World を表示するシンプルなコードに変更してみた。

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Hello World!',
      home: Scaffold(
        appBar: AppBar(
          title: Text('Hello World'),
        ),
        body: Center(
          child: Text('Hello World'),
        ),
      ),
    );
  }
}
```

ここまでは特に問題なし！

![first flutter app]({{ site.baseurl }}/assets/2019/03/17/2.png)