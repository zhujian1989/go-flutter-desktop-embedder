你好！
很冒昧用这样的方式来和你沟通，如有打扰请忽略我的提交哈。我是光年实验室（gnlab.com）的HR，在招Golang开发工程师，我们是一个技术型团队，技术氛围非常好。全职和兼职都可以，不过最好是全职，工作地点杭州。
我们公司是做流量增长的，Golang负责开发SAAS平台的应用，我们做的很多应用是全新的，工作非常有挑战也很有意思，是国内很多大厂的顾问。
如果有兴趣的话加我微信：13515810775  ，也可以访问 https://gnlab.com/，联系客服转发给HR。
<img src="./mascot.png" width="170" align="right">

# Go Flutter desktop embedder 

[![Join the chat at https://gitter.im/go-flutter-desktop-embedder/Lobby](https://badges.gitter.im/go-flutter-desktop-embedder/Lobby.svg)](https://gitter.im/go-flutter-desktop-embedder/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
<a href="https://stackoverflow.com/questions/tagged/flutter?sort=votes">
   <img alt="Awesome Flutter" src="https://img.shields.io/badge/Awesome-Flutter-blue.svg?longCache=true&style=flat-square" />
</a>

A Go (golang) [Custom Flutter Engine
Embedder](https://github.com/flutter/engine/wiki/Custom-Flutter-Engine-Embedders)
for desktop

# Purpose
This project doesn't compete with
[this](https://github.com/google/flutter-desktop-embedding) awesome one.
The purpose of this project is to support the 
[Flutter](https://github.com/flutter/flutter) framework on Windows, MacOS, and
Linux using a **SINGLE** code base.  

[**GLFW**](https://github.com/go-gl/glfw) fits the job because it
provides the right abstractions over the OpenGL's Buffer/mouse/keyboard for each platform.  

The choice of [Golang](https://github.com/golang/go) comes from the fact that it
has the same tooling on every platform.  
Plus golang is a great language because it keeps everything simple and readable,
which, I hope, will encourage people to contribute :grin:.

## How to install

<details>
<summary> :package: :penguin: Linux</summary>
<h4>From binaries</h4>
Check out the <a href="https://github.com/Drakirus/go-flutter-desktop-embedder/releases">Release</a> page for prebuilt versions.

<h4>From source</h4>

Go read first: [go-gl/glfw](https://github.com/go-gl/glfw/)  


```bash
# Clone
git clone https://github.com/Drakirus/go-flutter-desktop-embedder.git
cd go-flutter-desktop-embedder

# Build the flutter simpleDemo project
cd example/simpleDemo/
cd flutter_project/demo/
flutter build bundle
cd ../..

# Download the share library, the one corresponding to your flutter version.
go run engineDownloader.go

# REQUIRED before every `go build`. The CGO compiler need to know where to look for the share library
export CGO_LDFLAGS="-L${PWD}"
# The share library must stay next to the generated binary.

# Get the libraries
go get -u -v github.com/Drakirus/go-flutter-desktop-embedder

# Build the example project
go build main.go

# `go run main.go` is not working ATM.
```

</details>

<details>
<summary> :package: :checkered_flag: Windows</summary>
<h4>From binaries</h4>
Check out the <a href="https://github.com/Drakirus/go-flutter-desktop-embedder/releases">Release</a> page for prebuilt versions.

<h4>From source</h4>

Go read first: [go-gl/glfw](https://github.com/go-gl/glfw/)  


```bash
# Clone
git clone https://github.com/Drakirus/go-flutter-desktop-embedder.git
cd go-flutter-desktop-embedder

# Build the flutter simpleDemo project
cd example/simpleDemo/
cd flutter_project/demo/
flutter build bundle
cd ../..

# Download the share library, the one corresponding to your flutter version.
go run engineDownloader.go

# REQUIRED before every `go build`. The CGO compiler need to know where to look for the share library
set CGO_LDFLAGS=-L%cd%
# The share library must stay next to the generated binary.
# If you ran into a MinGW ld error, checkout: https://github.com/Drakirus/go-flutter-desktop-embedder/issues/34

# Get the libraries
go get -u -v github.com/Drakirus/go-flutter-desktop-embedder

# Build the example project
go build main.go

# `go run main.go` is not working ATM.
```

</details>

<details>
<summary> :package: :apple: MacOS</summary>
<h4>From binaries</h4>
Check out the <a href="https://github.com/Drakirus/go-flutter-desktop-embedder/releases">Release</a> page for prebuilt versions.

<h4>From source</h4>

Go read first: [go-gl/glfw](https://github.com/go-gl/glfw/)  


```bash
# Clone
git clone https://github.com/Drakirus/go-flutter-desktop-embedder.git
cd go-flutter-desktop-embedder

# Build the flutter simpleDemo project
cd example/simpleDemo/
cd flutter_project/demo/
flutter build bundle
cd ../..

# Download the share library, the one corresponding to your flutter version.
go run engineDownloader.go

# REQUIRED before every `go build`. The CGO compiler need to know where to look for the share library
export CGO_LDFLAGS="-F${PWD} -Wl,-rpath,@executable_path"
# The share library must stay next to the generated binary.

# Get the libraries
go get -u -v github.com/Drakirus/go-flutter-desktop-embedder

# Build the example project
go build main.go

# `go run main.go` is not working ATM.
```

</details>



## Flutter Demos Projects

The examples are available [here](./example/).

<img src="./stocks.jpg" width="900" align="center" alt="Screenshot of the Stocks demo app on macOS">

## Support

- [x] Linux :penguin:
- [x] Windows :checkered_flag:
- [x] MacOS :apple:
- [x] Importable go library
- [ ] Plugins [Medium article on how the the Flutter's messaging works](https://medium.com/flutter-io/flutter-platform-channels-ce7f540a104e)
   - [x] JSON MethodChannel
   - [ ] StandardMethodCodec, ...
- [ ] System plugins [Platform channels used by the Flutter system](https://github.com/flutter/flutter/blob/master/packages/flutter/lib/src/services/system_channels.dart)
  - [x] Window Title
  - [x] Text input
  - [x] Clipboard (through shortcuts)
  - [ ] Clipboard (through the click)
  - [x] Keyboard shortcuts
    - [x] <kbd>ctrl-c</kbd>  <kbd>ctrl-v</kbd>  <kbd>ctrl-x</kbd>  <kbd>ctrl-a</kbd>
    - [x] <kbd>Home</kbd>  <kbd>End</kbd>  <kbd>shift-Home</kbd>  <kbd>shift-End</kbd>
    - [x] <kbd>Left</kbd>  <kbd>ctrl-Left</kbd>  <kbd>ctrl-shift-Left</kbd>
    - [x] <kbd>Right</kbd>  <kbd>ctrl-Right</kbd>  <kbd>ctrl-shift-Right</kbd>
    - [x] <kbd>Backspace</kbd>  <kbd>ctrl-Backspace</kbd> <kbd>Delete</kbd>
    - [ ] <kbd>ctrl-Delete</kbd>
  - [ ] Key events
