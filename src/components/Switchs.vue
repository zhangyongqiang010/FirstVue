<template>
  <div id="switchs">
    <div class="box" :class="{ active:isactive }" @click="toggle">
      <div class="circle"></div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Switchs',
    data () {
      return {
        isactive:false,
      }
    },
    methods: {
      toggle(){
        this.isactive = !this.isactive;
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
  #switchs{
    margin: 10px 20px;
    .box{
      padding: 10px;
      width: 50px;
      height: 25px;
      background: #aaa;
      border-radius: 25px;
      .circle{
        width: 25px;
        height: 25px;
        box-shadow: 0px 0px 2px #aaa;
        border-right:1px solid #aaa; 
        border-radius: 50%;
        background: #fff;
      }
    }
    .active{
      text-align: right;
      background: green;
      .circle{
        transition: transform 0.15s ease-in 0s;
        -webkit-transition: transform 0.15s ease-in 0s;
        transform: translateX(25px);
        -webkit-transform: translateX(25px);
      }
    }
  }
</style>
