---
layout: post
title: "FFMPEG 常用命令使用"
date: 2017-08-02 00:01:01
category: streammedia
tags: [FFMPEG,FFPLAY]
---
在流媒体应用中，ffmpeg可谓是不可或缺的应用工具，在我们自己的产品中，也有ffmpeg的身影，通过对ffmpeg封装，进行接入rtsp，rtmp，转码，打包ts等等。一下关于ffmpeg命令使用需要掌握哪些语法或者参数选项加以说明。

ffmpeg 常用命令格式如下：
ffmpeg -i [输入文件名] [参数选项] -f [格式] [输出文件] 
ffmpeg [[options][`-i’ input_file]]… {[options] output_file} ... 

1、参数选项说明如下：
 A、-an: 去掉音频 
 B、-acodec: 音频选项， 一般后面加copy表示拷贝 
 C、-vcodec:视频选项，一般后面加copy表示拷贝 

2、格式说明
 A、 h264: 表示输出的是h264的视频裸流 
 B、 mp4: 表示输出的是mp4的视频 
 C、 mpegts: 表示ts视频流
缺省情况下，ffmpeg试图尽可能的无损转换，采用与输入同样的音频视频参数来输出。除非指定转换码率，分辨率，帧率等参数。

以下拿几个常用的转换示例加以说明：

A、将264视频转ts视频流
ffmpeg -i test.h264 -vcodec copy -f mpegts test.ts
B、H264视频转mp4
ffmpeg -i test.h264 -vcodec copy -f mp4 test.mp4
C、mp4视频转flv 
ffmpeg -i test.mp4 -acodec copy -vcodec copy -f flv test.flv
D、udp ts流推送
ffmpeg -re -i 1.ts -c copy -f mpegts udp://192.168.0.106:1234

后面文章会分享更多的关于音视频多媒体相关的开发，使用中遇到的问题。









