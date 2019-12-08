<template>
  <div id="home">
    <nav-bar class="nav-bar">
      <div slot="center">购物街</div>
    </nav-bar>
     
    <scroll class="content" ref="scroll" :probe-type="3" @scroll="clickscroll">
    <!--轮播图--> 
      <home-swiper :banners="banners"></home-swiper>
    <!--推荐-->
      <recommend-view :recommends="recommends"></recommend-view>
      <feature-view></feature-view>
      <tab-control class="tab-control" :titles="['流行','新款','精选']" @tabClick="tabClick"></tab-control>
      <!--<goods-list :goods="goods[currentType].list"/>     因为名字太长了，所以要搞个计算属性-->
      <goods-list :goods="showGoods"/>
    </scroll>
    <back-top @click.native="backClick"></back-top>

    
  </div>
</template>

<script>
//因为home.js没有用default导出所以要用{}
  
  import HomeSwiper from './childComps/HomeSwiper'
  import RecommendView from './childComps/RecommendView'
  import FeatureView from './childComps/FeatureView'

  import NavBar from 'common/navbar/NavBar'
  import TabControl from 'content/tabControl/TabControl'
  import GoodsList from 'content/goods/GoodsList'
  import Scroll from 'common/scroll/Scroll'
  import BackTop from 'content/backtop/BackTop'


  import {getHomeMultidata,getHomeGoods} from 'network/home'


  export default {
  name: 'Home',
  components: {
    HomeSwiper,
    RecommendView,
    FeatureView,

    NavBar,
    TabControl,
    GoodsList,
    Scroll,
    BackTop
  },
  data() {  
    // 保存数据
    return {
      // result: null      //用浏览器的vue插件检查     数据太多了
      banners: [],
      recommends: [],
      goods: {
        'pop': {page: 0, list: []},
        'new': {page: 0, list: []},
        'sell': {page: 0, list: []}
      },
      currentType: 'pop'
    }
  },
  computed: {
    showGoods(){
      // return goods[currentType].list     要加this
      return this.goods[this.currentType].list

    }
  },
  created() {     //创建后
    //1.请求多个数据
    this.getHomeMultidata()

    //2.请求商品数据
    this.getHomeGoods('pop')
    this.getHomeGoods('new')
    this.getHomeGoods('sell')

  },
  methods: {
    /*
    *事件监听
    */
    tabClick(index) {
      console.log(index);
      switch (index) {
        case 0:
          this.currentType = 'pop'
          break
        case 1:
          this.currentType = 'new'
          break
        case 2: 
          this.currentType = 'sell'
          break
      }
    },
    backClick(){
      // this.$refs.scroll.scroll.scrollTo(0,0,500)
      this.$refs.scroll.scrollTo(0,0,500)
    },
    clickscroll(position){
      console.log(position);
    },


    /*
    *网络请求
    */
    //1.请求多个数据
    getHomeMultidata() {
      getHomeMultidata().then(res => {
      console.log(res);
      // this.result = res;
      this.banners = res.data.banner.list;     //直接拿到里面的数据，多余的不要，要看请求回来的结构
      this.recommends = res.data.recommend.list;
    })
    },
    //2.请求商品数据
    getHomeGoods(type) {
      const page = this.goods[type].page + 1
      getHomeGoods(type,page).then(res => {
      console.log(res);
      this.goods[type].list.push(...res.data.list)   //把加载的数据追加到list里面
      this.goods[type].page += 1     //追加后要加页码
    })
    }
  }
}
</script>

<style scoped>     
#home {
  height: 100vh;
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
  z-index: 9;
}
.content {
  
  overflow: hidden; 
  position: absolute;
  top: 44px;
  bottom: 49px;
  left: 0;
  right: 0;
}
</style>
