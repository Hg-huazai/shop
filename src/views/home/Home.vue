<template>
  <div id="home">
    <nav-bar class="nav-bar">
      <div slot="center">购物街</div>
    </nav-bar>
     <!--轮播图-->
    <home-swiper :banners="banners"></home-swiper>
    <!--推荐-->
    <recommend-view :recommends="recommends"></recommend-view>
    <feature-view></feature-view>
    <tab-control class="tab-control" :titles="['流行','新款','精选']"></tab-control>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>

    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>

    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>

    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>
    <div>1</div>


  </div>
</template>

<script>
//因为home.js没有用default导出所以要用{}
  
  import HomeSwiper from './childComps/HomeSwiper'
  import RecommendView from './childComps/RecommendView'
  import FeatureView from './childComps/FeatureView'

  import NavBar from 'common/navbar/NavBar'
  import TabControl from 'common/tabControl/TabControl'


  import {getHomeMultidata} from 'network/home'


  export default {
  name: 'Home',
  components: {
    HomeSwiper,
    RecommendView,
    FeatureView,

    NavBar,
    TabControl
  },
  data() {  
    // 保存数据
    return {
      // result: null      //用浏览器的vue插件检查     数据太多了
      banners: [],
      recommends: []
    }
  },
  created() {     //创建后
    //1.请求多个数据
    getHomeMultidata().then(res => {
      console.log(res);
      // this.result = res;
      this.banners = res.data.banner.list;     //直接拿到里面的数据，多余的不要，要看请求回来的结构
      this.recommends = res.data.recommend.list;
    })
  }
}
</script>

<style>
#home {
  padding-top: 44px;
}
.nav-bar {
  background-color: var(--color-tint);
  color: #fff;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 9;
}
.tab-control {
  position: sticky;
  top: 44px;
}
</style>
