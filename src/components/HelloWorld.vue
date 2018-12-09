<template>
   <div class="wrapper">
     <div class="label" @click="label"></div>
     <div class="point" :class="{animate:lottery}" :style="{transform:`rotate(${deg}deg)`}" @webkitTransitionEnd='end'></div>
   </div>
</template>

<script>
export default {
  data(){
    return{
      lottery:false,
      deg:0
    }
  },
  mounted(){
    this.$nextTick(()=>{
    })
  },
  methods:{
    label(){
      if(this.lottery){
        return false
      }
      this.deg=0
      setTimeout(()=>{
         this.lottery=true
         this.deg=this.rotate()
      },10)  
    },
    rotate(){
      let deg=Math.random()*360;
      deg+=360*3
      return deg;
    },
    end(){
      this.lottery=false;
      console.log(this.deg)
    }
  }
}
</script>

<style lang='scss' scoped>
.wrapper{
  width: 100%;
  height: 628px;
  position: relative;
  background: url(../assets/shuffle-bg.png) no-repeat;
  background-size:cover;
  .label{
    position: absolute;
    top: 50%;
    left: 50%;
    width: 114px;
    height: 114px;
    margin-top: -66px;
    margin-left: -57px;
    cursor: pointer;
    background: url(../assets/label.png) no-repeat;
    z-index: 100;
  }
  .point{
    position: absolute;
    top: 50%;
    left: 50%;
    width: 49px;
    height: 224px;
    margin-top:-144px;
    margin-left:-25px;
    z-index: 99;
    background: url(../assets/pointer.png) no-repeat;
    -webkit-transform:rotate(0deg);
    -webkit-transform-origin: 25px 132px;
  }
  .animate{
      -webkit-transition: -webkit-transform 3s cubic-bezier(.23,.48,.45,.84);
  }
}
</style>