<template>
    <tab-bar>
      <tab-bar-item path="/home">
      <img slot="item-icon" src="~assets/img/tabbar/home.svg" alt="">    <!--替换插槽-->
      <img slot="item-icon-active" src="~assets/img/tabbar/home_active.svg" alt="">
        <div slot="item-text">首页</div>                             <!--替换插槽-->
      </tab-bar-item>
      <tab-bar-item path="/category">
      <img slot="item-icon" src="~assets/img/tabbar/category.svg">    <!--替换插槽-->
      <img slot="item-icon-active" src="~assets/img/tabbar/category_active.svg" alt="">
        <div slot="item-text">分类</div>     
      </tab-bar-item>
      <tab-bar-item path="/cart">
      <img slot="item-icon" src="~assets/img/tabbar/cart.svg">    <!--替换插槽-->
      <img slot="item-icon-active" src="~assets/img/tabbar/cart_active.svg" alt="">
        <div slot="item-text">购物车</div>     
      </tab-bar-item>
      <tab-bar-item path="/profile">
      <img slot="item-icon" src="~assets/img/tabbar/profile.svg">    <!--替换插槽-->
      <img slot="item-icon-active" src="~assets/img/tabbar/profile_active.svg" alt="">
        <div slot="item-text">我的</div>     
      </tab-bar-item>
    </tab-bar>
</template>

<script>
//导入
import TabBar from 'common/tabbar/TabBar'    //把组件导入 
import TabBarItem from 'common/tabbar/TabBarItem'
export default {
    name: 'MainTabBar',
    components: {
       TabBar,   //注册
        TabBarItem 
    }
}
</script>

<style>
 @import "~assets/css/base.css";
 
</style>