<template>
    <div class="wrapper" ref="wrapper">
      <div class="content">
        <slot></slot>
      </div>
    </div>
</template>

<script>
//导入
import BScroll from 'better-scroll'

export default {
    name: 'Scroll',
    data(){
      return {
        scroll: null
      }
    },
    components: {
    },
    // 挂载后
    mounted() {
      // console.log(this.$refs.wrapper);
      this.scroll = new BScroll(this.$refs.wrapper,{

      })
      this.scroll.scrollTo(0,0)
      
    },
    methods: {
      scrollTo(x,y,time=500){      //home.vue的backClick()可以通过$refs.scroll拿到scrollTo（）
        this.scroll.scrollTo(x,y,time)
      }
    }

}
</script>

<style scoped>
 
</style>