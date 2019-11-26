<template>
  <div id="tab-bar">
    <slot></slot>     <!--不具名插槽    组件中插组件要用到插槽-->
  </div>
</template>

<script>
export default {
  name: "TabBar"
}
</script>>

<style>
 #tab-bar {
   display: flex;
   background-color: #f6f6f6;

   position: fixed;
   left: 0;
   right: 0;
   bottom: 0;
  /*x轴向右为正， y轴向下为正*/
   box-shadow: 0px -2px 1px rgba(100,100,100,.1);    

 }
 .tab-bar-item {
   flex: 1;
   text-align: center;
   height: 49px;
 }
 .tab-bar-item img {
   width: 24px;
   height: 24px;
 }
</style>