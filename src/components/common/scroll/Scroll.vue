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
  props: {
    probeType: {
      type:Number,
      default: 0
    }
  },
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
      //1.创建BScroll对象
      this.scroll = new BScroll(this.$refs.wrapper,{
        click: true,   //滚动区域里面想要div被监听点击事件必须设置click="true" 默认为felse      而button不用设置
        probeType: this.probeType
      })
      //2.监听滚动的区域（位置）
      this.scroll.on('scroll',(position) => {
        // console.log(position);
        this.$emit('scroll',position)    //传给home来
      })
      // this.scroll.scrollTo(0,0)
      
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