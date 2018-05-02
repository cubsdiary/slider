# slider
> 基于vue 开发的多功能 轮播图

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

```

# slider 里面包括了三类轮播 图
##### slider-common (通用的)
![手机预览](https://www.pinkpig.top/image/slider_common1.png)

[在线预览](https://www.pinkpig.top/slider/slider1/#/)

##### slider-special (仿慕课网)
![手机预览](https://www.pinkpig.top/image/slider_special.png)

[在线预览](https://www.pinkpig.top/slider/slider2/#/)

##### slider-animate (仿爱奇艺泡泡社区 发现栏目 的轮播图)
![手机预览](https://www.pinkpig.top/image/slider_animate.png)

[在线预览](https://www.pinkpig.top/slider/slider3/#/)

## 使用方法

``` bash
  # 引入组件
  import Swiper from '@/components/swiper-slider-common'

  # 使用组件
  <Swiper  :autoplay="autoPlay" :duration="duration" :slidetype="slideType" :recommends="recommends" :color="color" :pagination="pagination"></Swiper>

  # autoPlay 切屏延时(如果传值则表示自动播放)  单位： ms (5000)
  # duration 动画延时  单位： ms
  # slideType 自动播放时 ，左划还是右划   (left or right)
  # pagination 是否显示分页  (false or true)
  # color 分页显示颜色 支持 rgb ,十六进制

```
