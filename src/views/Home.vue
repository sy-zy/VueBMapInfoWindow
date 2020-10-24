<template>
  <div class="home">
   <infoWindow
     :map="map"
     :markers="markers"
     @on-change="change">
     <h1>{{content}}</h1>
   </infoWindow>
  </div>
</template>

<script>
import infoWindow from '@/components/infoWindow/infoWindow.vue'
export default {
  name: 'home',
  components: {
      infoWindow,	  
  },
  data() {
    return {
      // 地图配置
      map: {
        ak: '百度地图浏览器端AK秘钥',
        center: {
          lng: '112.97935279',
          lat: '28.21347823',
        },
        zoom: 12,
        width: '100%',
        height: '100%',
      },
      // 地图标记点
      markers:[
        {
          lng: '112.685238',
          lat: '28.136284',
          value: '信息窗口1'
        },
        {
          lng: '112.958309',
          lat: '28.214387',
          value: '信息窗口2'
        },

      ],
      content: '',
    };
  },
  methods: {
    // 切换标记点 marker当前标记点对象
  	change (marker) {
      this.content = marker.value;
      console.log(marker.value);
    }
  },
}
</script>

<style lang="css">
.home{
  height: 100%;
}
</style>
