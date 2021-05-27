
## 总览
- [为什么我推荐文章这种方式？](#为什么我推荐文章这种方式？)
- [mac上如何下载呢？](#mac上如何下载呢？)
- [windows上如何下载呢？](#windows上如何下载呢？)
- [注意事项](#注意事项)

***
## 为什么我推荐文章这种方式？
很大原因是现在的youtube的很多下载网站不满足需求，我想下载个8k的视频或者高清的视频，80%的网站不行，如果可以的话，都是要给钱，本身楼梯都花钱了，再为这个花钱非常不值得，还有就是稳定性的问题，也许目前可以用，过段时间网站就没了，所以就去G站找了个一劳永逸的办法！文章这种方式，可能对比网上那些网站的方式可能要麻烦些许，但是有非常高的自定义功能，也就是可控性更强！适合有一定计算器基础和懂得一些基本操作的朋友学习！如果你觉得自己不怎么会玩电脑。。好吧，就此打住，本篇可能不太适合。那直接进入主题

***
## mac上如何下载呢？

下载一个加速工具[点我下载](http://pigcha.com?from=youtube-dl)，注册登录加速后，新用户有免费流量，找到桌面上方栏的这一栏，点这个加速器图标，点会弹出如下界面  
![img](https://cdn.processon.com/6065e15ce0b34d28298e72ce)  
然后我们点**控制台代理**，**后面的全部命令行都在这个“控制台代理” 里面运行**

```
# 安装homebrew，已经安装了的话，不执行下面这句，跳过就行了
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)" 
```

```
# 安装youtubedr和ffmpeg工具
brew install youtubedr
brew install ffmpeg
```

好，上面是安装工具，下面就是怎么使用工具了，以后直接就运行下面这些命令了
```
# 查看需要下载的视频信息
youtubedr info 跟上视频地址
# 例：youtubedr info https://www.youtube.com/watch?v=1La4QzGeaaQ
```
输出应该长这个样子的信息
![img](https://cdn.processon.com/60ae5864e0b34d38418a1124)
是不是一脸懵逼。。莫方，很简单的，先看第三列的Video Quality，就是你想要下载的视频质量，也就是清晰度，我知道你们一般就喜欢下载高清的！！还要注意一点是最后一列的MIMETYPE告诉你视频的文件类型，一般就选mp4，综合这两条规则，我们就可以选出要下载哪个清晰度的视频了！！！根据偏好就可以得到ITAG为571。

### 🙉🙉所以下载视频？🙉🙉
```
# 下载视频
youtubedr download -q ITAG 跟上视频地址
# 例：youtubedr download -q 571 https://www.youtube.com/watch?v=1La4QzGeaaQ
```
你以为这就完了？？还没有。。只是下载了视频。。还没有下载音频啊朋友！！来来来，我们找到第五列 AUDIO CHANNELS找那些为2的行，第四行的AUDIO QUALITY尽量选medium的，并且第三行VIDEO QUALITY为空的，再看最后一列的MIMETYPE为audio/mp4，很容易了，我们定位到音频的ITAG为140。

### 🙉🙉所以下载音频？🙉🙉
```
# 下载音频
youtubedr download -q ITAG 跟上视频地址
# 例：youtubedr download -q 140 https://www.youtube.com/watch?v=1La4QzGeaaQ
```
然后你就发现rnm，原来下了一个视频和一个音频。。。还差合并这一步我们得合并下就大功告成了！！

![img](https://cdn.processon.com/60ae633de0b34d38418a2d04)
### 🙉🙉所以合并视频与音频？🙉🙉
```
# 合并下载的音频与视频
ffmpeg -i '源视频文件.mp4' -i '源音频文件.m4a' -vcodec copy -acodec copy 输出文件.mp4

# 例：ffmpeg -i 'Peru 8K HDR 60FPS (FUHD).mp4' -i 'Peru 8K HDR 60FPS (FUHD).m4a' -vcodec copy -acodec copy output.mp4
```

```
# 最后再打开文件位置
open .
```

**大功告成！合并后的文件就是output.mp4
🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈
一百只猴哥送上祝福**


***
## windows上如何下载呢？
同样和mac大体上是一致的  
- 下载一个加速工具[点我下载](http://pigcha.com?from=youtube-dl)，注册登录加速后，新用户有免费流量

- 下载安装youtubedr[点我去github下载](https://github.com/kkdai/youtube/releases)
![img](https://cdn.processon.com/60aee15f6376893238df67e2)，然后解压出youtubedr.exe 并放到C:\Windows目录下

- 下载安装ffmpeg[点我去他们官网下载](https://www.gyan.dev/ffmpeg/builds/)
![img](https://cdn.processon.com/60aee41107912962458ea7a3)，然后解压bin目录里面的ffmpeg.exe 并放到C:\Windows目录下

okay，到这里我们的ffmpeg和youtubedr都已安装成功了！以后直接就运行下面这些命令了来下载视频了，找到桌面下方栏的这一栏，点这个加速器图标，点会弹出如下界面，点**控制台代理**。。不是图片中的git代理  
![IMG](https://cdn.processon.com/5ffd440d1e0853437c3e1ad1)  
理论上应该弹出一个控制台，**然后就在弹出的控制台里面选择输入下面这些命令来下载了**


```
# 切换到D盘根目录
cd /d D:\
```

```
# 查看需要下载的视频信息
youtubedr info 跟上视频地址
例：youtubedr info https://www.youtube.com/watch?v=1La4QzGeaaQ
```
输出应该长这个样子的信息
![img](https://cdn.processon.com/60af0cf407912962458f5e3e)
是不是一脸懵逼。。莫方，很简单的，先看第三列的Video Quality，就是你想要下载的视频质量，也就是清晰度，我知道你们一般就喜欢下载高清的！！还要注意一点是最后一列的MIMETYPE告诉你视频的文件类型，一般就选mp4，综合这两条规则，我们就可以选出要下载哪个清晰度的视频了！！！根据偏好就可以得到ITAG为571。

### 🙉🙉所以下载视频？🙉🙉
```
# 下载视频
youtubedr download -q ITAG 跟上视频地址
# 例：youtubedr download -q 571 https://www.youtube.com/watch?v=1La4QzGeaaQ
```
你以为这就完了？？还没有。。只是下载了视频。。还没有下载音频啊朋友！！来来来，我们找到第五列 AUDIO CHANNELS找那些为2的行，第四行的AUDIO QUALITY尽量选medium的，并且第三行VIDEO QUALITY为空的，再看最后一列的MIMETYPE为audio/mp4，很容易了，我们定位到音频的ITAG为140。

### 🙉🙉所以下载音频？🙉🙉
```
# 下载音频
youtubedr download -q ITAG 跟上视频地址
# 例：youtubedr download -q 140 https://www.youtube.com/watch?v=1La4QzGeaaQ
```
然后你就发现rnm，原来下了一个视频和一个音频。。。还差合并这一步我们得合并下就大功告成了！！

![img](https://cdn.processon.com/60af0ce46376893238e020e9)
### 🙉🙉所以合并视频与音频？🙉🙉
```
# 合并下载的音频与视频
ffmpeg -i "源视频文件.mp4" -i "源音频文件.m4a" -vcodec copy -acodec copy "输出文件.mp4"

# 例：ffmpeg -i "Peru 8K HDR 60FPS (FUHD).mp4" -i "Peru 8K HDR 60FPS (FUHD).m4a" -vcodec copy -acodec copy "output.mp4"
```
**大功告成！合并后的视频文件就在D盘的output.mp4
🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈🙈
一百只猴哥送上祝福**

***
## 注意事项
- 如果是搬运视频，最好取得原作用同意~
- 如果哪天发现不好使了，可以考虑更新下youtubedr
- mac上更新youtubedr可以使用命令 brew upgrade youtubedr
- windows上更新youtubedr得去他们的github下载最新的并覆盖本地就好
- 也可以不使用前面的楼梯，但你要知道怎么设置cmd代理！适合高玩
