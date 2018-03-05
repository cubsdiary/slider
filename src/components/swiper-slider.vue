<template>
  <div class="">
    <div class="">
      <p>StartX:{{touchInfo.startX}}</p>
      <p>StartY:{{touchInfo.startY}}</p>
      <p>endX:{{touchInfo.endX}}</p>
      <p>endY:{{touchInfo.endY}}</p>
      <p>moveX:{{touchInfo.moveX}}</p>
      <p>moveY:{{touchInfo.moveY}}</p>
      <p>index:{{imgIndex}}</p>
      <p>domLeft:{{domLeft}}</p>
      <p>bridge:{{bridge}}</p>
      <p>startTime:{{touchInfo.startTime}}</p>
      <p>endTime:{{touchInfo.endTime}}</p>
    </div>
    <div class="slider"  @touchstart="touchS" @touchend="touchE" @touchmove="touchM" >
      <div class="slider-group" ref="slideGroup" :style="{transform: translate3d, transitionDuration: duration + 'ms'}">
        <slot>
        </slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'swiper',
  data () {
    return {
      touchInfo:{
        startX: 0,
        startY: 0,
        endX: 0,
        endY: 0,
        moveX: 0,
        moveY: 0,
        startTime: 0,
        endTime: 0
      },
      imgIndex: 1,
      domLeft: -375,
      bridge: 0,
      duration: 300,
      translate3d: ''
    }
  },
  methods: {
    touchS (event) {
      let _touchStart = event.touches[0]
      this.touchInfo.startX = _touchStart.pageX
      this.touchInfo.startY = _touchStart.pageY
      this.touchInfo.startTime = parseInt(event.timeStamp)
    },
    touchE (event) {
      let _touchEnd = event.changedTouches[0]
      this.touchInfo.endX = _touchEnd.pageX
      this.touchInfo.endY = _touchEnd.pageY
      this.touchInfo.endTime = parseInt(event.timeStamp)

      if (this.touchInfo.startX > this.touchInfo.endX) {
        if ((this.touchInfo.startX - this.touchInfo.endX) > 20 && (this.touchInfo.endTime - this.touchInfo.startTime) > 50) {
          this.imgIndex += 1
          this.bridge = 0
          this.animateImg(0, 0)
        } else if ((this.touchInfo.startX - this.touchInfo.endX) < 20 || (this.touchInfo.endTime - this.touchInfo.startTime) < 50) {
          this.bridge = 0
          this.animateImg(0, 0)
        } else if ((this.touchInfo.startX - this.touchInfo.endX) > 187) {
          this.imgIndex += 1
          this.bridge = 0
          this.animateImg(0, 0)
        } else {
          this.bridge = 0
          this.animateImg(0, 0)
        }
      } else {
        if ((this.touchInfo.endX - this.touchInfo.startX) > 20 && (this.touchInfo.endTime - this.touchInfo.startTime) > 50) {
          this.imgIndex -= 1
          this.bridge = 0
          this.animateImg(1, 1)
        } else if ((this.touchInfo.endX - this.touchInfo.startX) < 20 || (this.touchInfo.endTime - this.touchInfo.startTime) < 50) {
          this.bridge = 0
          this.animateImg(1, 1)
        } else if ((this.touchInfo.endX - this.touchInfo.startX) > 187) {
          this.imgIndex -= 1
          this.bridge = 0
          this.animateImg(1, 1)
        } else {
          this.bridge = 0
          this.animateImg(1, 1)
        }
      }
    },
    touchM (event) {
      let _touchMove = event.touches[0]
      this.touchInfo.moveX = _touchMove.pageX
      this.touchInfo.moveY = _touchMove.pageY
      if (this.touchInfo.startX > this.touchInfo.moveX) {
        this.animateImg(2)
      } else {
        this.animateImg(3)
      }
    },
    animateImg (id, index) {
      console.log(this.imgIndex)
      if (id < 2) {
        if (this.imgIndex === 0) {
          this.imgIndex = 5
          this.domLeft = -this.imgIndex*375
          this.setTranslate3D(0)
        }
        if (this.imgIndex === 6) {
          this.imgIndex = 1
          this.domLeft = -this.imgIndex*375
          this.setTranslate3D(0)
        }

        this.domLeft = -this.imgIndex*375
        this.setTranslate3D(1)
      } else if (id >= 2) {
        this.bridge = this.touchInfo.startX - this.touchInfo.moveX
      }
    },
    setTranslate3D (index) {
      if (index === 1) {
        this.duration = 300
      } else if (index === 0) {
        this.duration = 0
      }
      this.translate3d = 'translate3d(' + (this.domLeft - this.bridge) + 'px, 0px, 0px)'
    }
  },
  mounted () {
    this.setTranslate3D()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .slider{
    position: relative;
    width: 100%;
    height: 150px;
    overflow: hidden;
  }
  .slider-group{
    height: 100%;
    width: 100%;
    display: flex;
  }
  .slider-group > div {
    display: flex;
    align-items:center;
    justify-content: center;
    height: 100%;
    width: 100%;
    flex-shrink: 0;
    z-index: 10;
    /* 遇见过一次图片宽度很宽超过 slide 导致下一个 slide 也会有这个图片 */
    overflow: hidden;
  }
  .slide-item{
    float: left;

    box-sizing: border-box;
    overflow: hidden;
    text-align: center;
  }
  .slider-group a{
    display: block;
    width: 100%;
    margin: 0;
    padding: 0;
    overflow: hidden;
    text-decoration: none;
  }
  .slider-group img{
    display: inline-block;
    width: 100%;
  }
</style>
