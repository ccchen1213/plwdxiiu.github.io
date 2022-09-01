---
title: 数字验证码组件(Vue实现)
date: 2022-09-01 10:23:37
tags: 组件
categories: 'COMPONENTS'
cover: https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/微信截图_20220901102530_202209011025.png
---

- **组件展示**

![image.png](https://safesfiles.oss-cn-beijing.aliyuncs.com/safes/ZHNX30835/1661998777257-5a6bd77e-53f8-4f20-8c34-c8137fe4f51c_202209011026.png)


- **组件源码**
```javascript
<template>
  <div class="s-canvas">
    <canvas
      id="s-canvas"
      :width="contentWidth"
      :height="contentHeight"
    />
    <span class="a-tag" @click="$emit('change')">看不清，换一个</span>
  </div>
</template>

<script>
export default {
  name: 'NumberVerify',
  props: {
    // 默认注册码
    identifyCode: {
      type: String,
      default: '1234',
    },
    // 字体最小值
    fontSizeMin: {
      type: Number,
      default: 25,
    },
    // 字体最大值
    fontSizeMax: {
      type: Number,
      default: 35,
    },
    // 验证码图片背景色最小值
    backgroundColorMin: {
      type: Number,
      default: 200,
    },
    // 验证码图片背景色最大值
    backgroundColorMax: {
      type: Number,
      default: 220,
    },
    // 背景干扰点最小值
    dotColorMin: {
      type: Number,
      default: 60,
    },
    // 背景干扰点最大值
    dotColorMax: {
      type: Number,
      default: 120,
    },
    // 容器宽度
    contentWidth: {
      type: Number,
      default: 116,
    },
    // 容器高度
    contentHeight: {
      type: Number,
      default: 38,
    },
  },
  watch: {
    identifyCode() {
      this.drawPic()
    },
  },
  mounted() {
    this.drawPic()
  },
  methods: {
    // 生成一个随机数
    randomNum(min, max) {
      return Math.floor(Math.random() * (max - min) + min)
    },
    // 生成一个随机的颜色
    randomColor(min, max) {
      const r = this.randomNum(min, max)
      const g = this.randomNum(min, max)
      const b = this.randomNum(min, max)
      return 'rgb(' + r + ',' + g + ',' + b + ')'
    },
    drawPic() {
      const canvas = document.getElementById('s-canvas')
      const ctx = canvas.getContext('2d')
      ctx.textBaseline = 'bottom'
      // 绘制背景
      ctx.fillStyle = this.randomColor(this.backgroundColorMin, this.backgroundColorMax)
      ctx.fillRect(0, 0, this.contentWidth, this.contentHeight)
      // 绘制文字
      for (let i = 0; i < this.identifyCode.length; i++) {
        this.drawText(ctx, this.identifyCode[i], i)
      }
      this.drawLine(ctx)
      this.drawDot(ctx)
    },
    drawText(ctx, txt, i) {
      ctx.fillStyle = this.randomColor(50, 160) // 随机生成字体颜色
      ctx.font = this.randomNum(this.fontSizeMin, this.fontSizeMax) + 'px SimHei' // 随机生成字体大小
      const x = (i + 1) * (this.contentWidth / (this.identifyCode.length + 1))
      const y = this.randomNum(this.fontSizeMax, this.contentHeight - 5)
      const deg = this.randomNum(-30, 30)
      // 修改坐标原点和旋转角度
      ctx.translate(x, y)
      ctx.rotate(deg * Math.PI / 180)
      ctx.fillText(txt, 0, 0)
      // 恢复坐标原点和旋转角度
      ctx.rotate(-deg * Math.PI / 180)
      ctx.translate(-x, -y)
    },
    drawLine(ctx) {
      // 绘制干扰线
      for (let i = 0; i < 4; i++) {
        ctx.strokeStyle = this.randomColor(100, 200)
        ctx.beginPath()
        ctx.moveTo(this.randomNum(0, this.contentWidth), this.randomNum(0, this.contentHeight))
        ctx.lineTo(this.randomNum(0, this.contentWidth), this.randomNum(0, this.contentHeight))
        ctx.stroke()
      }
    },
    drawDot(ctx) {
      // 绘制干扰点
      for (let i = 0; i < 30; i++) {
        ctx.fillStyle = this.randomColor(0, 255)
        ctx.beginPath()
        ctx.arc(this.randomNum(0, this.contentWidth), this.randomNum(0, this.contentHeight), 1, 0, 2 * Math.PI)
        ctx.fill()
      }
    },
  },
}
</script>

<style lang="less" scoped>
.a-tag{
  color: #6280f5;
  text-decoration: underline;
  padding: 12px;
  font-size: 26px;
}
</style>
```


- **使用**
```javascript
<template>
  <numberVerify
    :identifyCode="identifyCode"
    :contentWidth="240"
    :contentHeight="65"
    :fontSizeMin="35"
    :fontSizeMax="55"
    @change="getRandomNumber"
  />
</template>

<script>
import numberVerify from './numberVerify.vue'
import {getUUID} from './util.js'
export default {
  components: {
    zhnxPage,
    numberVerify,
  },
  data() {
    return {
      identifyCode: '',
    }
  },
  methods: {
    getRandomNumber() {
      this.identifyCode = getUUID(4)
    },
  }
}
  
```


- **获取随机数的方法：（数字+字母）**
```javascript
// 生成随机数
export const getUUID = function(len) {
  len = len || 6
  len = parseInt(len, 10)
  len = isNaN(len) ? 6 : len
  const seed = '0123456789abcdefghijklmnopqrstubwxyzABCEDFGHIJKLMNOPQRSTUVWXYZ'
  const seedLen = seed.length - 1
  let uuid = ''
  while (len--) {
    uuid += seed[Math.round(Math.random() * seedLen)]
  }
  return uuid
}
```
