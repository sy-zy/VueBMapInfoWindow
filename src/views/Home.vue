<template>
  <div class="home">
   <infoWindow
     :map="map"
     :markers="markers">
     信息窗口
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
      map: {
        ak: '您百度地图的AK秘钥',
        center: {
          lng: 112.97935279,
          lat: 28.21347823,
        },
        zoom: 12,
        width: '100%',
        height: '100%',
      },
      markers:[
        {
          lng: 112.685238,
          lat: 28.136284,
          markerIcon: {
            url: 'http://api0.map.bdimg.com/images/marker_red_sprite.png', 
            size: {
              width: 30,
              height: 40
            }
          },
          infoWindow: {
            info: {
              SystemName: " ",
              ResultData1: " ",
              ModifyTime: " ",
              area: " ",
              OnLineState: " ",
            },
            show: true
          },
        },
        {
          lng: 112.958309,
          lat: 28.214387,
          markerIcon: {
            url: 'http://api0.map.bdimg.com/images/marker_red_sprite.png', 
            size: {
              width: 30,
              height: 40
            }
          },
          infoWindow: {
            info: {
              SystemName: " ",
              ResultData1: " ",
              ModifyTime: " ",
              area: " ",
              OnLineState: " ",
            },
            show: true
          },
        },

      ],
    };
  },
  methods: {
  	
  },
}
</script>

<style lang="css">
.home{
  height: 100%;
}
</style>
