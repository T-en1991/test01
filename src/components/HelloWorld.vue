<template>
  <div>
    经度：
    <el-input style="width: 200px;" v-model="a"></el-input>
    纬度：
    <el-input style="width: 200px;" v-model="b"></el-input>
    <el-button @click="btn">111</el-button>
    <baidu-map style="width: 100%;height: 800px" :center="center" class="map" :zoom="zoom" :scroll-wheel-zoom="true">
      <bm-marker :position="{lng: 11, lat: 11}" scroll-wheel-zoom="true"
                 :icon="{url: '../../static/greenGuo.png', size: {width: 100, height: 100},imageSize:'100%'}">
      </bm-marker>
      <bm-marker :position="{lng: 22, lat: 22}" scroll-wheel-zoom="true"
                 :icon="{url: 'http://developer.baidu.com/map/jsdemo/img/fox.gif', size: {width: 300, height: 157}}">
      </bm-marker>
      <bm-marker :position="{lng: 33, lat: 33}" scroll-wheel-zoom="true"
                 :icon="{url: 'http://developer.baidu.com/map/jsdemo/img/fox.gif', size: {width: 300, height: 157}}">
      </bm-marker>
      <bm-marker :position="{lng: 44, lat: 44}" scroll-wheel-zoom="true"
                 :icon="{url: 'http://developer.baidu.com/map/jsdemo/img/fox.gif', size: {width: 300, height: 157}}">
      </bm-marker>
      <bm-overlay
        pane="markerPane"
        style="width:200px;height: 120px;background-color: rgba(0,0,0,.4);"
        @mouseover.native="active = true"
        @mouseleave.native="active = false">
        <el-row>
          <el-col :span="16">
            某某某监测站
          </el-col>
          <el-col :span="8" style="color: white">
            <i class="el-icon-edit"></i>
            <i class="el-icon-close" @click="test"></i>
          </el-col>
          <el-divider></el-divider>
          <el-row style="color: white">
            <el-col :span="8">
              二级
            </el-col>
            <el-col :span="16">
              <el-col>
                站点位置
              </el-col>
              <el-col>
                站点类型
              </el-col>
              <el-col>
                考核目标
              </el-col>
            </el-col>
          </el-row>
        </el-row>
      </bm-overlay>
      <bm-local-search :auto-viewport="true" :location="center"></bm-local-search>
    </baidu-map>
  </div>
</template>

<script>
  export default {
    name: 'HelloWorld',
    data() {
      return {
        center: {lng: 11, lat: 11},
        zoom: 10,
        a: 0,
        b:0,
        location: '北京',
        keyword: '百度',
        infoWindow: {
          show: true,
          contents: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.'
        }
      }
    },
    methods: {
      infoWindowClose(e) {
        this.infoWindow.show = false
      },
      infoWindowOpen(e) {
        this.infoWindow.show = true
      },
      clear() {
        this.infoWindow.contents = ''
      },
      btn() {
        console.log(this.a, this.b);

        this.$set(this.center, 'lng', this.a)
        this.$set(this.center, 'lat', this.b)
        this.zoom = 10;
      },
      test(){
        console.log(1);
      }
    }

  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .bm-view {
    width: 100%;
    height: 500px;
  }
.disN{
  display: none;
}
</style>
