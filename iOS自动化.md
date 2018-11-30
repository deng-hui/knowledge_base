### iOS自动化

### xcodebuild自动构建命令

#### 简介

首先说明下使用文档：

> man xcodebuild

基本上现在的包管理都是以pod来的，也就是以workspace的形式，所以基本的形式为：

>xcodebuild [-project projectname] [-target targetname ...] 
[-configuration configurationname] [-sdk [sdkfullpath | sdkname]] [buildaction ...] 
[setting=value ...] [-userdefault=value ...]

解释两个参数：

- target，可以通过 xcodebuild -list 查看
- configrtion，也可以通过 xcodebuild -list 查看
- sdk，可用 xcodebuild -showsdks，一般默认就行

```
$ xcodebuild -list
Information about project "class-demo":
    Targets:
        class-demo
        class-demoTests
        class-demoUITests

    Build Configurations:
        Debug
        Release

    If no build configuration is specified and -scheme is not passed then "Release" is used.

    Schemes:
        class-demo
        class-demoTests
        class-demoUITests

```

1、正常编译
> xcodebuild -target class-demo -configuration


允许生成配置LinkMap
无workSpace

> xcodebuild -target class-demo -configuration Debug LD_GENERATE_MAP_FILE=YES  -showBuildSettings
> 

有workspace
> xcodebuild -workspace Demo.xcworkspace -scheme Demo -configuration Debug
 

参考资料：

[iOS - 自动化编译打包（Jenkins）](https://www.cnblogs.com/gongyuhonglou/p/8629017.html)

[xcodebuild通用命令指南](https://www.jianshu.com/p/c32263138af3)

