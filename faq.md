

# FAQ

## 1. 图片审核的API请求总是返回body格式不正确，可能是什么原因？

图片审核的body要求是multipart/form-data格式，很有可能请求的body并非该格式。该格式是一种高效传输二进制内容的http body格式，并非只将Content-Type强行设置为multipart/form-data，而是要将body的参数按照该格式组织。

## 2. 视频审核的请求参数Interval该怎么设置？

视频审核本身是对视频逐帧抽取做图片审核，Interval表示抽帧的间隔。一般视频的帧率为25～30帧/秒。

Interval设置为25，大致相当于一秒钟的视频抽取一帧做分析。对于一般的视频设置50比较合适；对于变化缓慢的视频可以设置更大。