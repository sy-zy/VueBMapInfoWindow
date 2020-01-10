<template>
  <div class="map-container">
    <baidu-map
      :style="{width: map.width, height: map.height}"
      :ak="map.ak"
      :zoom="map.zoom"
      :center="{lng: map.center.lng, lat: map.center.lat}"
      :scroll-wheel-zoom="true"
    >
      <!--动态添加的点坐标-->
      <bm-marker
        v-for="(marker,index) of markers"
        :key="index"
        :position="{lng: marker.lng, lat: marker.lat}"
        :icon="marker.markerIcon"
        @click="infoWindowOpen(index, marker)"
      >
        <bm-info-window
          :show="marker.infoWindow.show"
          @close="infoWindowClose(index, marker)"
          @open="infoWindowOpen(index, marker)"
        >
          <slot></slot>
        </bm-info-window>
      </bm-marker>
      <!--比例尺控件-->
      <bm-scale anchor="BMAP_ANCHOR_TOP_RIGHT"></bm-scale>
      <!--缩放控件-->
      <bm-navigation anchor="BMAP_ANCHOR_BOTTOM_RIGHT"></bm-navigation>
    </baidu-map>
  </div>
</template>

<script>
import BaiduMap from 'vue-baidu-map/components/map/Map.vue'
import BmScale from 'vue-baidu-map/components/controls/Scale'
import BmNavigation from 'vue-baidu-map/components/controls/Navigation'
import BmMarker from 'vue-baidu-map/components/overlays/Marker'
import BmInfoWindow from 'vue-baidu-map/components/overlays/InfoWindow'
import './infoWindow.css'
export default {
  name: 'infoWindow',
  props: {
  	map: {
  		type: Object,
  		default () {
  			return {
		        center: {
		          lng: 116.402544,
		          lat: 39.912057,
		        },
		        zoom: 10,
		        width: '100%',
		        height: '100%',
		     };
  		}
  	},
  	markers: {
  		 Array,
	  	default () {
	  		return [];
	  	}
  	}
  },
  components: {
    BaiduMap,
	  BmScale,
	  BmNavigation,
	  BmMarker,
	  BmInfoWindow,
  },
  data() {
    return {};
  },
  watch: {
    map: {
    	handler (newVal) {
    		this.map = newVal;
    	},
    	deep: true,
    },
    markers: {
    	handler (newVal) {
    		this.markers = newVal;
    	},
    	deep: true,
    }
  },
  methods: {
    infoWindowOpen (index, marker) {//打开窗口
      marker.infoWindow.show = true;
      this.$set(this.markers, index, marker);
    },
    infoWindowClose (index, marker) {//关闭窗口
      marker.infoWindow.show = false;
      this.$set(this.markers, index, marker);
    },
  },
}
</script>

<style lang="css">
.BMap_cpyCtrl {
  display: none !important;
}
.anchorBL {
  display: none !important;
}
.map-container{
  height: 100%;
}
</style>
