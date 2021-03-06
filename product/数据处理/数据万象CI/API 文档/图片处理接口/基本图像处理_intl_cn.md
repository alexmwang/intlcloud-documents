## 简介

imageView2 是腾讯云数据万象提供的一种使用简单，功能强大的图像处理接口，包括裁剪、压缩、格式转换等。开发者根据业务需求，只需在下载 url 后面附加相应的参数，就可以生成相应的缩略图，目前支持大小在 20M 以内、长宽小于 9999 像素的图片处理。

## 接口形式

><font color="#0000cc">**注意：** </font>
>请忽略下面代码中的回车。

```
download_url?imageView2//w//h/
                         /format/
                         /q/
					     /rq/
                         /lq/
```

## 参数说明

| 参数                                      | 含义                                       |
| --------------------------------------- | ---------------------------------------- |
|download_url                            |文件的访问链接，具体构成为&lt;bucket id&gt;-&lt;appid&gt;.&lt;picture region&gt;.&lt;domain&gt;.com/&lt;picture name&gt;，如examples-1251000004.picsh.myqcloud.com/sample.jpeg|
| /1/w/&lt;Width>/h/&lt;Height&gt;      | 限定缩略图的宽高最小值。该操作会将图像等比缩放直至某一边达到设定最小值，之后将另一边居中裁剪至设定值。如只指定一边，则表示宽高相等的正方形。如原图大小为1000x500，将参数设定为?imageView2/1/w/500/h/400 后，图像会先等比缩放至800x400，之后左右各裁剪150，得到500x400大小的图像 |
| /2/w/&lt;Width&gt;/h/&lt;Height&gt;      | 限定缩略图的宽高最大值。该操作会将图像等比缩放至宽高都小于设定最大值。如原图大小为1000x500，将参数设定为?imageView2/2/w/500/h/400后，图像会等比缩放至500x250。如果只指定一边，则另一边自适应 |
| /3/w/&lt;Width>/h/&lt;Height&gt;      | 限定缩略图的宽高最小值。该操作会将图像等比缩放至宽高都大于设定最小值。如原图大小为1000x500，将参数设定为?imageView2/3/w/500/h/400后，图像会等比缩放至800x400。如果只指定一边，则另一边设为相同值 |
| /4/w/&lt;LongEdge>/h/&lt;ShortEdge&gt; | 限定缩略图的长边和短边的最小值分别为 LongEdge 和 ShortEdge ，进行等比压缩；如果只指定一边，代表另外一边为同样的值 |
| /5/w/&lt;LongEdge&gt;/h/&lt;ShortEdge&gt;| 限定缩略图的长边和短边的最大值分别为 LongEdge 和 ShortEdge ，进行等比压缩，居中裁剪；如果只指定一边，则表示宽高相等的正方形；缩放后其中一边多余的部分会被裁剪掉 |
| /format/&lt;Format&gt;                   | 目标缩略图的图片格式，Format 可为：jpg , bmp , gif , png , webp ,缺省为原图格式 |
| /q/&lt;Quality&gt;                              | 图片质量，取值范围 0-100 ，默认值为原图质量；取原图质量和指定质量的最小值；&lt;Quality&gt; 后面加!（注意为单字节），表示强制使用指定值 |
|/rq/&lt;quality&gt; | 图片的相对质量，取值范围 0-100 ，数值以原图质量为标准，如原图质量为 80，将 rquality 设置为80 后得到处理结果图的图片质量为 64（80x80%） |
|/lq/&lt;quality&gt; | 图片的最低质量，取值范围 0-100 ，设置结果图的质量参数最小值。如原图质量为 85，将 lquality 设置为 80 后处理结果图的图片质量为 85；如原图质量为 60，将 lquality 设置为 80 后处理结果图的图片质量会被提升至80 |



## 示例
```
http://examples-1251000004.picsh.myqcloud.com/sample.jpeg?imageView2/1/w/400/h/600/q/85
http://examples-1251000004.picsh.myqcloud.com/sample.jpeg?imageView2/2/w/400/h/600/q/85!
http://examples-1251000004.picsh.myqcloud.com/sample.jpeg?imageView2/3/w/400/format/png
```
