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

// 画出裁剪后的图片
function drawImage(crop){
  cropCanvas.width = cropWidth;
  cropCanvas.height = cropHeight;
  cropCtx.drawImage(img, crop.x, crop.y, crop.width, crop.height, 0, 0, cropWidth, cropHeight);
  var src = cropCanvas.toDataURL("image/jpeg");
  $('#img').attr('src', src);
}

```

今天研究了一下他给提供的[testdemo](https://29a.ch/sandbox/2014/smartcrop/examples/testbed.html)，测试了一下。发现当宽度较小，高度较大时裁剪的图片会裁掉人像部分。感觉有点怪，不知道是不是他的bug。

附上自己的DEMO[戳这里](https://smileyby.github.io/smartcrop.js/)

### 测试结果

* 未开启`ruleOfThirds`时---在宽度很小，高度很大的时候裁剪不准确  **建议裁剪区域的宽高比为1:1会更精确**
* smartcrop.js还可以借助第三方规则来实现准确的裁剪 [jQuery/Zepto facedetection](http://facedetection.jaysalvat.com/) [trackingjs](https://trackingjs.com/)
* 它还有很多参数可以配置，具体请参考[smartcrop.js](https://github.com/jwagner/smartcrop.js)
* 主要用到canvas的两个属性，具体请参考[drawImage MDN](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/drawImage),[toDataURL MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLCanvasElement/toDataURL)
* 最终将裁剪后的图片转成base输出
