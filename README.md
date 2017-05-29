smartcrop.js
============

一个不会裁掉人脸的js插件

## 简单用法

```js

smartcrop.crop(image, {width: 100, height: 100}).then(function(result){
  console.log(result);
});

// result.topCrop 存储了裁剪区域开始位置和宽高
// 返回数据格式

var returnData = {
	height: 1365,
	score: Object,
	width: 1365,
	x: 655,
	y: 0
}

// 使用canvas将其画出来
function drawCrop(crop) {
  canvas.width = img.width;
  canvas.height = img.height;
  ctx.drawImage(img, 0, 0);
  ctx.strokeStyle = 'red';
  ctx.lineWidth = 4;
  ctx.strokeRect(crop.x, crop.y, crop.width, crop.height);
}

```

今天研究了一下他给提供的[testdemo](https://29a.ch/sandbox/2014/smartcrop/examples/testbed.html)，测试了一下。发现当宽度较小，高度较大时裁剪的图片会裁掉人像部分。感觉有点怪，不知道是不是他的bug。

附上自己的DEMO[戳这里](https://smileyby.github.io/smartcrop.js/)

### 测试结果

*	在宽度很小，高度很大的时候裁剪不准确

现在只是实现了用`canvas`用红线把裁剪部分圈出来，但要怎么把圈出来的部分转换成另一张图片呢？这是一问题，带我研究出来在写在这里。主要是都是英文看着累啊。呜呜宝宝心里苦，宝宝要学英语