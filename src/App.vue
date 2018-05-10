<template>
  <div id="app">
    <Swiper :duration="duration" :recommends="recommends" @tapcard="_tapCard">

    </Swiper>
  </div>
</template>

<script>
// import Swiper from '@/components/swiper-slider-common'
// import Swiper from '@/components/swiper-slider-special'
// import Swiper from '@/components/swiper-slider-animate'
import Swiper from '@/components/swiper-slider-view'
export default {
  name: 'App',
  data () {
    return {
      recommends: [{
        id: 1,
        linkUrl: 'https://y.qq.com/m/act/chunwan2018/v3/index.html?ADTAG=jiaodiantu',
        picUrl: 'http://y.gtimg.cn/music/photo_new/T003R720x288M0000044SNAC19jwin.jpg'
      },{
        id: 2,
        linkUrl: 'http://y.qq.com/w/album.html?albummid=001u8nwR0H4x7z',
        picUrl: 'http://y.gtimg.cn/music/photo_new/T003R720x288M000003b2lHy424XQS.jpg'
      },{
        id: 3,
        linkUrl: 'https://y.qq.com/apg/156/index.html?ADTAG=5',
        picUrl: 'http://y.gtimg.cn/music/photo_new/T003R720x288M000000HDstc2PVKnq.jpg'
      },{
        id: 4,
        linkUrl: 'http://y.qq.com/w/album.html?albummid=003l5sT818BTyn',
        picUrl: 'http://y.gtimg.cn/music/photo_new/T003R720x288M000001LLLb51HkIVE.jpg'
      },{
        id: 5,
        linkUrl: 'https://c.y.qq.com/node/m/client/music_headline/index.html?_hidehd=1&_button=2&zid=619582',
        picUrl: 'http://y.gtimg.cn/music/photo_new/T003R720x288M000000Wq2eW3VkzJ9.jpg'
      }],
      autoPlay: 5000,
      duration: 500,
      slideType: 'left',
      color: '#000',
      pagination: true
    }
  },
  methods: {
    _tapCard (id) {
      console.log(id)
    }
  },
  components: {
    Swiper
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 100%;
  height: 100%;
}
body, html{
  width: 100%;
  height: 100%;
}
*{
  margin: 0;
  padding: 0;
}
</style>
