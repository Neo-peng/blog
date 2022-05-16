title: 使用 infuse 登录 emby server
author: John Doe
date: 2022-05-16
tags: emby,infuse
cover: https://imgs.mcurr.xyz/i/2022/05/16/6281f4e8d8929.png
---
infuse 因为会扫库，所以被很多的 emby 公益服禁用。最近刚开始玩 emby，之前不知道公益服会禁用infuse，还专门买了个。
后续研究中，找到了方法可以绕过这个限制，使用 infuse。
<!--more-->
## 为何 emby 公益服大多禁用infuse？
因为infuse会扫库。
所谓的扫库是指，infuse会下载视频的开头片段，然后生成封面（这个描述可能不准确，我也不太确定具体下载视频片段是为何）。
而媒体库一般好几万个视频，每个视频就算只下载开头的片段，这一过程也会占用服务器大量的带宽。
经过我实测，infuse扫我存放在gdrive的视频时候，峰值下载带宽会达到100MB/s，注意是MB！！。
最扯淡的是，不知道为什么，infuse会频繁的扫库，每次重新扫库都要重新扫好几万的视频，这个带宽占用，想想就头皮发麻。

## 如何绕过限制？
通过修改header，具体方法就不发了。
我在测试了成功用infuse 登录MisakaF公益服后，就删掉了infuse的登录信息，因为用这个着实有点良心不安。

## emby服主如何堵上这个漏洞？
因为没有研究过emby server，目前想到的方法就是通过api的请求速度来判断是否有人在扫库，然后根据判断封禁就好了