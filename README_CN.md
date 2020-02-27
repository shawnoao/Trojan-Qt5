<h1 align="center">
  <img src="https://github.com/TheWanderingCoel/Trojan-Qt5/blob/master/resources/icons/trojan-qt5.png?raw=true" alt="Trojan-Qt5" width="200">
  <br>
  Trojan-Qt5
  <br>
</h1>

一个跨平台的Trojan图形客户端

[![Build status](https://travis-ci.com/TheWanderingCoel/Trojan-Qt5.svg?branch=master)](https://travis-ci.com/TheWanderingCoel/Trojan-Qt5)
[![Build status](https://ci.appveyor.com/api/projects/status/shjhg9mlvc3c74ek?svg=true)](https://ci.appveyor.com/project/CoelWu/trojan-qt5)
[![HitCount](http://hits.dwyl.io/TheWanderingCoel/Trojan-Qt5.svg)](http://hits.dwyl.io/TheWanderingCoel/Trojan-Qt5)
![GitHub Releases](https://img.shields.io/github/downloads/TheWanderingCoel/Trojan-Qt5/latest/total?style=flat-square&logo=github)
![GitHub All Releases](https://img.shields.io/github/downloads/TheWanderingCoel/Trojan-Qt5/total?label=downloads-total&logo=github&style=flat-square)
[![License](https://img.shields.io/badge/license-GPL%20V3-blue.svg?longCache=true)](https://www.gnu.org/licenses/gpl-3.0.en.html)

## 安装

你可以在 [release](https://github.com/TheWanderingCoel/Trojan-Qt5/releases) 页面下载到编译好的二进制程序

## 编译

### 0.前置依赖
- Windows, macOS, Linux
- c++ 编译器(cl, clang, gcc)
- Qt 5.13.0 +
- QHttpServer(根据下面的方法来安装)
```
git clone https://github.com/qt-labs/qthttpserver.git
cd qthttpserver
qmake
make -j$(nproc) // Windows上是nmake
make install // Windows上是nmake install
```

### 1.Windows
- 1. 初始化环境
```
C:\"Program Files (x86)"\"Microsoft Visual Studio"\2019\Community\VC\Auxiliary\Build\vcvarsall.bat x86
```
- 2. 克隆需要的库
```
git clone https://github.com/TheWanderingCoel/Trojan-Qt5-Libraries.git C:\TQLibraries
```
- 3. 手动安装Boost库(在大陆很慢)
```
curl -Lo boost_1_72_0-msvc-14.2-32.exe https://sourceforge.net/projects/boost/files/boost-binaries/1.72.0/boost_1_72_0-msvc-14.2-32.exe/download
powershell ".\\boost_1_72_0-msvc-14.2-32.exe /SILENT /SP- /SUPPRESSMSGBOXES /DIR='C:\TQLibraries\boost_1_72_0'"
```
- 4. 进行构建
```
mkdir build && cd build
qmake ..
nmake
```

### 2.macOS
- 1. 安装HomeBrew包管理器
```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
- 2. 安装依赖
```
brew install zbar qrencode boost openssl@1.1 zlib pcre
```
- 3. 进行构建
```
mkdir build && cd build
qmake ..
make -j$(nproc)
```

### 3.Linux

- 1. 下载安装依赖
```
sudo apt-get install libgl-dev git build-essential g++ python-dev autotools-dev libicu-dev libbz2-dev checkinstall zlib1g-dev -y
```
- 2. 编译依赖
```
sudo bash scripts/linux_compile.sh
```
- 3. 配置Privoxy
```
cd src/privoxy
autoheader && autoconf && ./configure
cd ../..
```
- 4. 进行构建
```
mkdir build && cd build
qmake ..
make -j$(nproc)
```

## 常见问题 (FAQ)

### 1. 配置文件编辑器里的东西和Trojan配置文件有什么关系?
![Profile Editor](https://i.imgur.com/xA58JNG.png)

### 2. Defender报垃圾软件, 360报毒?
- [VirusTotal](https://www.virustotal.com/gui/file/247faa5d67592af7583a7ebd53654383d25e258de329ee145f7d8abbf2ba7034/detection)  
- 下载后请检查md5和sha1 hash是否一致
- 如果你要去那宽阔的世界看看，请不要使用360全家桶

### 3. 如何计算文件的md5 hash?
#### 1. Windows
```
certutil -hashfile Trojan-Qt5-Windows.zip MD5
```
#### 2. macOS
```
md5 -r Trojan-Qt5-macOS.dmg
```
#### 3. Linux
```
md5sum Trojan-Qt5-Linux.AppImage
```

### 4. 如何计算文件的sha1 hash?
#### 1. Windows
```
certutil -hashfile Trojan-Qt5-Windows.zip SHA1
```
#### 2. macOS
```
shasum Trojan-Qt5-macOS.dmg
```
#### 3. Linux
```
sha1sum Trojan-Qt5-Linux.AppImage
```
## 特别感谢

这个项目基于以下几个项目:

- [libQtShadowsocks](https://github.com/shadowsocks/libQtShadowsocks) LGPL-3.0
- [Shadowsocks-qt](https://github.com/trojan-gfw/trojan-qt) LGPL-3.0
- [trojan](https://github.com/trojan-gfw/trojan) GPL-3.0
- [trojan-qt](https://github.com/trojan-gfw/trojan-qt) GPL-3.0
- [Privoxy](https://www.privoxy.org) GPL-2.0
- [sysproxy](https://github.com/Noisyfox/sysproxy/) Apache-2.0