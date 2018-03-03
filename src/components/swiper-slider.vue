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
    </div>
    <div class="slider"  @touchstart="touchS" @touchend="touchE" @touchmove="touchM">
      <div class="slider-group" ref="slideGroup" :style="{left: (domLeft-bridge) + 'px' }">
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
        moveY: 0
      },
      imgIndex: 0,
      domLeft: 0,
      bridge: 0
    }
  },
  methods: {
    touchS (event) {
      let _touchStart = event.touches[0]
      this.touchInfo.startX = _touchStart.pageX
      this.touchInfo.startY = _touchStart.pageY
    },
    touchE (event) {
      let _touchEnd = event.changedTouches[0]
      this.touchInfo.endX = _touchEnd.pageX
      this.touchInfo.endY = _touchEnd.pageY

      if (this.touchInfo.startX > this.touchInfo.endX) {
        if ((this.touchInfo.startX - this.touchInfo.endX) > 187) {
          this.imgIndex += 1
          this.bridge = 0
          this.animateImg(0)
        }
      } else {
        if ((this.touchInfo.endX - this.touchInfo.startX) > 187) {
          this.imgIndex -= 1
          this.bridge = 0
          this.animateImg(1)
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
    animateImg (id) {
      if (id < 2) {
        this.domLeft = -this.imgIndex*375
      } else if (id >= 2) {
        this.bridge = this.touchInfo.startX - this.touchInfo.moveX
      }
    }
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
    position: absolute;
    left: -375px;
    right: 0;
    width: 2625px;
    height: 150px;
    overflow: hidden;
  }
  .slider-group > div {
    float: left;
  }
  .slide-item{
    float: left;

    box-sizing: border-box;
    overflow: hidden;
    text-align: center;
  }
  .slider-group a{
    display: block;
    width: 375px;
    margin: 0;
    padding: 0;
    overflow: hidden;
    text-decoration: none;
  }
  .slider-group img{
    display: inline-block;
    width: 375px;
  }
</style>
