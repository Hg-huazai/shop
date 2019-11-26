<template>
  <div id="app">
    <router-view></router-view>
    <main-tab-bar></main-tab-bar>
  </div>
</template>

<script>
import MainTabBar from 'components/content/MainTabBar/MainTabBar'
export default {
  name: 'app',
  components: {
    MainTabBar   //注册
  }
}
</script>

<style>
  @import "./assets/css/base.css";


</style>
