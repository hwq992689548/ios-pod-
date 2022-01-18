# ios-pod-

### 自定义pod插件流程

### 1. 在github上创建仓库如TestPod， 创建完成后会显示创库地址：
###


git init
git add README.md

git commit -m "first commit"

git branch -M main

git remote add origin https://github.com/xxx/MXTAlertView.git

git push -u origin main



git remote add origin https://github.com/xxx/MXTAlertView.git

git branch -M main

git push -u origin main

###


### 2、在本地新建一个文件夹demo，终端打开，执行命令：

pod lib create MXTAlertView

###

根据提示安装：

What platform do you want to use?? [ iOS / macOS ]

> ios

What language do you want to use?? [ Swift / ObjC ]

> swift


Would you like to include a demo application with your library? [ Yes / No ]

> yes


Which testing frameworks will you use? [ Quick / None ]

> none

Would you like to do view based testing? [ Yes / No ]

> no

完成后，会自动运行XCode项目

###


### 3、 在 MXTAlertView.podspec 设置配置信息： 

###
s.description = '自已写描述信息'

s.homepage = ‘https://github.com/xxx/MXTAlertView’

s.author = { 'xxx' => 'xxx' }

s.source = ‘xxx’

s.license = "MIT"

记得去掉中文的 “”, 根据实际的git改 

最后：

#这个 pods 还依赖于其他哪些 pods

s.dependency "AFNetWrok"

s.dependency "SnapKit"

###


### 4、命令行： 

cd Example文件夹，并执行： pod update --no-repo-update  (更新组件内容)


cd 到 demo/MXTAlertView下，执行: pod lib lint --allow-warnings  (验证)


### 5、关联远程地址，并push到远程

###
git remote add origin https://github.com/xxx/MXTAlertView.git

git add .

git commit -a -m "first commit"

git push -u origin master（或 git push --set-upstream origin master）

###

### 6、tag版本号

git tag 0.1.0

git push --tags



### 7、 最后把spec索引推送到cocoapod上

pod repo push MXTAlertView MXTAlertView.podspec --allow-warnings


如果提示MXTAlertView不存在问题，Unable to find the `MXTAlertView ` repo


执行： pod repo add MXTAlertView https://github.com/hwq992689548/MXTAlertView.git



###其它：

远程验证：

 pod spec lint --sources='https://github.com/github名字/xxx.git,https://github.com/CocoaPods/Specs.git' --verbose  

本地验证：

pod spec lint --sources='https://github.com/xxx/MXTAlertView.git,https://github.com/CocoaPods/Specs.git' --verbose  

推送的话：

pod repo push MXTAlertView MXTAlertView.podspec --sources='https://github.com/hwq992689548/MXTAlertView.git,https://github.com/CocoaPods/Specs.git' --verbose


















