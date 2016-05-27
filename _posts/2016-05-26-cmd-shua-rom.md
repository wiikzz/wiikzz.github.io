---
layout: post_layout
title: 命令行刷Rom
time: 2016年05月26日 星期四
location: 上海
pulished: true
excerpt_separator: "#"
---

准备工作
  - 下载[Android SDK](http://developer.android.com/intl/zh-cn/sdk/index.html)工具包，并设置好环境变量，确保手机能正常连上电脑。
  - 下载官方Rom包，解压（image*.zip也需要解压）。可以看到boot.img，cache.img，recovery.img，system.img，userdata.img等。


开始刷机
  - 手机关机，进入bootloader模式（一般是power+音量下键）。
  - 进入rom包解压目录。

刷bootloader，radio
```bash
$fastboot flash bootloader bootloader-hammerhead-hhz12k.img
$fastboot flash radio radio-hammerhead-m8974a-2.0.50.2.28.img
```

重启bootloader
```bash
$fastboot reboot-bootloader
```
```bash
pip install pygments
```
安装完成后, 你需要用它来生成一个 css 文件, 放在你的 jekyll 项目中, 生成命令为

```bash
pygmentize -S default -f html > style.css
# 这个 -S 就是 style, 默认的style 为 firendly 具体得 style 可以参考 [Styles](http://pygments.org/docs/styles/)
```


刷recovery，boot，system，cache，userdata
```bash
$fastboot flash recovery recovery.img
$fastboot flash boot boot.img 
$fastboot flash system system.img

$fastboot flash cache cache.img 
$fastboot flash userdata userdata.img 
```

重启手机
```bash
$fastboot reboot
```

等待手机重启完毕，OK。
