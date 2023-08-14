
今天近视眼逛博客把的一个服务器借我练练手，作为一个从来没用过服务器的我来说简直是太兴奋了！但是登陆服务器以后我迷茫了！内心在问自己我在那？我是谁？我在干什么？

然后我又去问他我该干什么？他告诉安装宝塔系统！于是我谷歌了下可算把宝塔安装完了！发现界面简直太好操作了！于是我就想到了这Gridea通过githb来同步到服务器！看看是怎么操作的，后来上网搜了下发现可以通过webhook来实现同步！但是网上的教程实在太坑了！给一大堆复制粘贴的代码，也不告诉你修改的格式应该注意什么！再或者就是给你一堆马赛克的图片！不明白发图片教程你关键位置打毛线马赛克啊！发这图片有毛线意义啊？节省点服务器空间不好吗？

教程开始：
第一步安装git `yum install git`

然后上宝塔软件商店安装宝塔WebHook并添加如下代码：
``` 

#!/bin/bash
echo ""
#输出当前时间
date --date='0 days ago' "+%Y-%m-%d %H:%M:%S"
echo "Start"
#git项目路径
gitPath="/www/wwwroot/***.com"
#git 网址
gitHttp="https://github.com/***/**.git"

echo "Web站点路径：$gitPath"

#判断项目路径是否存在
if [ -d "$gitPath" ]; then
        cd $gitPath
        #判断是否存在git目录
        if [ ! -d ".git" ]; then
                echo "在该目录下克隆 git"
                git clone $gitHttp gittemp
                mv gittemp/.git .
                rm -rf gittemp
        fi
        #拉取最新的项目文件
        git reset --hard origin/master
        git pull
        #设置目录权限
        chown -R www:www $gitPath
        echo "End"
        exit
else
        echo "该项目路径不存在"
        echo "End"
        exit
fi
```
4.点击查看密钥，并复制密钥
5.到达 github repo，找到 settings，选择 Webhooks，点击 add Webhooks，确认密码
6.在 Payload URL 中输入 ' http://*.*.*.*:8888/hook?access_key=(第4步中的密钥)
' 好了就这么简单！代码部分转载于谷歌的一个公共平台！且亲测可用的！
