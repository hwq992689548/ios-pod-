
### 自定义pod插件流程

### 1. 在github上创建仓库如TestPod， 创建完成后会显示创库地址：
###


git init
git add README.md

git commit -m "first commit"

git branch -M main

git remote add origin https://github.com/xxxxxx.git

git push -u origin main



git remote add origin https://github.com/xxxxxx.git

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

s.homepage = ‘https://github.com/xxxxxx’

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
git remote add origin https://gitee.com/xxxxxx.git

git add .

git commit -a -m "first commit"

git push -u origin master（或 git push --set-upstream origin master）

###

### 6、tag版本号

git tag 0.1.0

git push --tags



### 7、 最后把spec索引推送到cocoapod上

pod repo push xxxxxx xxxxxx.podspec --allow-warnings


如果提示xxxxxx不存在问题，Unable to find the `xxxxxx ` repo


执行：

 pod repo add xxxxxx https://gitee.com/xxxxxx.git


###其它：

注册trunk

pod trunk register xxxxxx@qq.com ‘xxxxxx‘ --description='Personal Laptop'

用trunk提交：

pod trunk push xxxxxx.podspec --allow-warnings

远程验证：

 pod spec lint --sources='http://192.168.2.10:9000/xxxxxx.git,https://github.com/CocoaPods/Specs.git' --verbose  
 
本地验证：

pod spec lint --sources='http://192.168.2.10:9000/xxxxxx.git,https://github.com/CocoaPods/Specs.git' --verbose  


推送的话：

pod repo push xxxxxx xxxxxx.podspec --sources='https://github.com/xxxxxx.git,https://github.com/CocoaPods/Specs.git' --verbose

 

###
    注：如果是用的非GitHub进行托管的（如gitlab），pod search 是搜不到的,

	因为他是私有的（如果想开源给大家，那就上github，然后发布到开源库）

	需要在podfile里声明你的podspec仓库地址 source 'https://xxxxx.git' 

	如： pod 'xxxxxx', :git => "https://gitee.com/xxxxxx"

###
