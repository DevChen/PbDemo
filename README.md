# PbDemo
PbDemo for iOS
Pb3.2 Protocol Buffers for iOS 正确的使用教程

一、入坑

1.官方大坑

	https://github.com/alexeyxo/protobuf-objc

	按照官方指引，但在 Build it! ./scripts/build.sh 后编译器报错，最终无解

	验证办法：demo里的person.proto转换成OC文件

2.避坑教程

	先卸载protobuf

     //如何卸载protobuf
    brew uninstall --ignore-dependencies protobuf

	http://www.cnblogs.com/tandaxia/p/6181534.html

	思路：放弃CocoaPods的源码下载, 直接把从https://github.com/google/protobuf V3.2下载下来的库拖进工程安装。

3.转换OC文件

	环境配置完成后，把定义好的proto文件，在相关目录下执行

      protoc --objc_out=./ ./person.proto



二、使用


1.导入pod

	1）更新pod到最新  sudo gem install cocoapods --pre 

	2） platform :ios, '7.1' //7.0不可以

	3） pod 'Protobuf', '~> 3.1.0' //3.2目前pod上还不支持 搜索后结果 3.0以上才有

	4）-fno-objc-arc //导出的model文件 非arc

	目前cocoapods库里有最新的3.1.0，能正常使用3.2格式的文件，使用正常。

2.导入工程库

	工程里引入ProtocolBuffers_iOS.xcodeproj，能凑合用，但对整体工程架构影响太大。

