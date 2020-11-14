<template>
  <div class="tab-bar-item" @click="itemClick">
    <slot v-if="!isActived" name="slot-img"></slot>
    <slot v-else name="slot-active-img"></slot>
    <div :style="activeStyle">
      <slot name="slot-text" ></slot>
    </div>
  </div>
</template>

<script>
  export default {
    name: "Tab-bar-item",
    data(){
      return{
        // isActived:false
      }
    },
    computed:{
      isActived(){
        return this.$route.path.indexOf(this.path)!==-1
      },
      activeStyle(){
        return this.isActived?{color:this.activeColor}:{}
      }
    },
    props:{
      path:String,
      activeColor:{
        type:String,
        default:"deepskyblue"
      }
    },
    methods:{
      itemClick(){
        // console.log('kkkkk')
        this.$router.push(this.path)
        // console.log(this.path)
      }
    }
  }
</script>

<style scoped>

  .tab-bar-item{
    text-align: center;
    height: 49px;/*移动端底部导航的固定像素，一般都为49px*/
  }
 /* .tab-bar-item>img{
    width: 24px;
    height: 24px;
  }*/
/*  .active{
    color:deepskyblue;
  }*/
</style>
