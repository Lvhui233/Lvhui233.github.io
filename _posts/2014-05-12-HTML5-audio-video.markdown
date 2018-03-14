---
layout:     post
title:      "HTML5 音频与视频"
subtitle:   "HTML5 audio and video"
date:       2014-05-12 12:00:00
author:     "LvI"
header-img: "img/post-bg-os-metro.jpg"
header-mask: 0.3
catalog: true
tags:
    - HTML5
---

## 音频元素

audio标签 嵌入音频

```
//control显示控制条,loop循环播放,autoplay自动播放
<audio src="音频地址" controls="controls" loop="loop" autoplay="autoplay"></audio>

<audio controls="controls" loop="loop" autoplay="autoplay">
	<source src="音频地址" />
</audio>
```

## 视频元素

video标签 嵌入视频

视频格式支持：mp4(H.264编码)、webm、ogg

属性
- controls 显示控制条
- loop 循环播放
- autoplay 自动播放
- poster 封面
- width/height 宽度/高度 

```
<video src="视频地址" controls="controls" loop="loop" autoplay="autoplay" id='video'></video>

//js中控制播放
var video = document.getElementById("video");
//播放
video.play();
//暂停
video.pause();
//快进
video.currentTime = video.currentTime + 3;
//1.5倍播放
video.playbackRate = 1.5;
```

[video.js插件的使用](http://www.jq22.com/jquery-info404)

[视频/音频手册](http://www.w3school.com.cn/tags/html_ref_audio_video_dom.asp)