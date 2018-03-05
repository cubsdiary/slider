<template>
  <div id="app">
    <swiper>
      <div v-for="(item, index) in recommends" :key="index">
        <a :href="item.linkUrl">
          <img :src="item.picUrl" alt="">
        </a>
      </div>
    </Swiper>
  </div>
</template>

<script>
import Swiper from '@/components/swiper-slider'
export default {
  name: 'App',
  data () {
    return {
      recommends: [{
        id: 4,
        linkUrl: 'https://c.y.qq.com/node/m/client/music_headline/index.html?_hidehd=1&_button=2&zid=619582',
        picUrl: 'http://y.gtimg.cn/music/photo_new/T003R720x288M000000Wq2eW3VkzJ9.jpg'
      },{
        id: 0,
        linkUrl: 'https://y.qq.com/m/act/chunwan2018/v3/index.html?ADTAG=jiaodiantu',
        picUrl: 'http://y.gtimg.cn/music/photo_new/T003R720x288M0000044SNAC19jwin.jpg'
      },{
        id: 1,
        linkUrl: 'http://y.qq.com/w/album.html?albummid=001u8nwR0H4x7z',
        picUrl: 'http://y.gtimg.cn/music/photo_new/T003R720x288M000003b2lHy424XQS.jpg'
      },{
        id: 2,
        linkUrl: 'https://y.qq.com/apg/156/index.html?ADTAG=5',
        picUrl: 'http://y.gtimg.cn/music/photo_new/T003R720x288M000000HDstc2PVKnq.jpg'
      },{
        id: 3,
        linkUrl: 'http://y.qq.com/w/album.html?albummid=003l5sT818BTyn',
        picUrl: 'http://y.gtimg.cn/music/photo_new/T003R720x288M000001LLLb51HkIVE.jpg'
      },{
        id: 4,
        linkUrl: 'https://c.y.qq.com/node/m/client/music_headline/index.html?_hidehd=1&_button=2&zid=619582',
        picUrl: 'http://y.gtimg.cn/music/photo_new/T003R720x288M000000Wq2eW3VkzJ9.jpg'
      },{
        id: 0,
        linkUrl: 'https://y.qq.com/m/act/chunwan2018/v3/index.html?ADTAG=jiaodiantu',
        picUrl: 'http://y.gtimg.cn/music/photo_new/T003R720x288M0000044SNAC19jwin.jpg'
      }]
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
