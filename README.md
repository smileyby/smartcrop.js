smartcrop.js
============

一个不会裁掉人脸的js插件

## 简单用法

```js

smartcrop.crop(image, {width: 100, height: 100}).then(function(result){
  console.log(result);
});

```

今天研究了一下他给提供的testdemo，测试了一下。发现当宽度较小，高度较大时裁剪的图片会裁掉人像部分。感觉有点怪，不知道是不是他的bug。

附上自己的DEMO[戳这里]()

现在只是实现了用`canvas`用红线把裁剪部分圈出来，但要怎么把圈出来的部分转换成另一张图片呢？这是一问题，带我研究出来在写在这里。