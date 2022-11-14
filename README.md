# vudio.js

## Archived, transferred to https://github.com/alex2wong/vudio for better version control in NPM

### 一个简单的音频数据可视化模块

多種視覺效果:

![多種視覺效果](https://github.com/alex2wong/vudio/blob/master/demo_src/snapshot.jpg?raw=true)

------
#### 概述：
- 支持诸多样式调整
- 动画效果基于Canvas和requestAnimationFrame，丝般顺滑
- 仅供娱乐，开心就好

#### 使用方法

模块式引入
```bash
# 使用npm安装此模块，以下是原始仓库版本，fork增强版（圆圈效果）的请安装 npm i vudio --save 或者 yarn add vudio
npm i vudio.js --save
# 或者使用yarn安装此模块
yarn add vudio.js
```
```javascript
import Vudio from 'vudio.js'
```
标签式引入
```html
<script src="https://unpkg.com/vudio@2.0.5/umd/vudio.js"></script>
```
实例化Vudio
```javascript
var vudio = new Vudio(HTMLAudioElement | MediaStream, HTMLCanvasElement, [option]);
vudio.dance();
```
第一个参数用于指定音频源，可以是一个Audio标签，或者一个Audio对象，也可以是通过navigator.mediaDevices.getUserMedia获取到的音频MediaStream对象

第二个参数用于指定显示可视化内容的Canvas，

第三个参数用于指定显示效果的个性化配置

#### 示例
在你的HTML文件中放入canvas和audio标签
```html
<canvas width="256px" height="100px" id="canvas"></canvas>
<audio src="./path/to/audio.mp3" controls id="audio"></audio>
```
引入Vudio.js
```html
<script src="path/to/vudio.js"></script>
```
> 注意，因为浏览器的同源策略，所以跨域情况下无法使用本模块（可在服务端进行控制）

开始搅基
```javascript
var audioObj = document.querySelector('#audio');
var canvasObj = document.querySelector('#canvas');
var vudio = new Vudio(audioObj, canvasObj, {
    effect : 'waveform', // 当前只有'waveform'这一个效果，哈哈哈
    accuracy : 128, // 精度,实际表现为波形柱的个数，范围16-16348，必须为2的N次方
    width : 256, // canvas宽度，会覆盖canvas标签中定义的宽度
    height : 100, // canvas高度，会覆盖canvas标签中定义的高度
    waveform : {
        maxHeight : 80, // 最大波形高度
        minHeight : 1, // 最小波形高度
        spacing: 1, // 波形间隔
        color : '#f00', // 波形颜色，可以传入数组以生成渐变色
        shadowBlur : 0, // 阴影模糊半径
        shadowColor : '#f00', // 阴影颜色
        fadeSide : true, // 渐隐两端
        horizontalAlign : 'center', // 水平对齐方式，left/center/right
        verticalAlign: 'middle' // 垂直对齐方式 top/middle/bottom
    }
});

// 调用dance方法开始得瑟吧
vudio.dance();

// 也可随时停止得瑟
vudio.pause();

// 中途换个姿势得瑟也是可以的
vudio.setOption({
    waveform : {
        color : '#06f',
        verticalAlign: 'bottom'
    }
});
```

在线示例: http://alex2wong.github.io/vudio/

### Related VScode extension

![VScode extension snapshot](https://user-images.githubusercontent.com/10528482/64496866-f1eca780-d2db-11e9-92e5-cc179758d035.gif)
