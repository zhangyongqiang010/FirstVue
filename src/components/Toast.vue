<template>
  <div id="toast">
    <div class="noramal">
      <button class="btn"  @click="show1">show</button>
      <div v-show="this.wrap[0].wrap1" class="wrap warp1"><p>welcome to here!</p></div>
    </div>
    <div class="icon">
      <button class="btn"  @click="show2">show</button>
      <div v-show="this.wrap[1].wrap2" class="wrap warp2"><p class=" c-toast-icon icon-home icon">welcome \\to here!</p></div>
    </div>
    <!-- <img src="../assets/iconfont.f2114cb.svg"> -->
    <div class="loading">
      <button class="btn" @click="show3">show</button>
      <div v-show="this.wrap[2].wrap3" class="wrap wrap3"><p class="c-iconloading">welcome toopo here!</p></div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Toast',
    data () {
      return {
        wrap:[
          {wrap1:false},
          {wrap2:false},
          {wrap3:false}
        ]
      };
    },
    methods: {
      show1(){
        this.wrap[0].wrap1 = true;
        this.wrap[1].wrap2 =false;
        this.wrap[2].wrap3 = false;
        setTimeout( () =>{
          this.wrap[0].wrap1 = false
        },3000)
      },
      show2(){
        this.wrap[1].wrap2 = true;
        this.wrap[0].wrap1 =false;
        this.wrap[2].wrap3 = false;
        setTimeout( () =>{
          this.wrap[1].wrap2 = false
        },3000)
      },
      show3(){
        this.wrap[2].wrap3 = true;
        this.wrap[0].wrap1 =false;
        this.wrap[1].wrap2 = false;
        var that = this;
        setTimeout( () =>{
          this.wrap[2].wrap3 = false;
        },3000)
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
  #toast{
    >div{
      padding: 10px 5px;
      border-bottom: 1px solid #aaa;
      text-align: right;
      .btn{
        display: inline;
        position: relative;
        right: 0;
        padding:10px 20px;
        border: 1px solid #aaa;
        border-radius: 10px;
        background: #fff;
        color:#333;
        outline: none;
      }
      .wrap{
        position: fixed;
        left: 0;
        top: 0;
        z-index:10;
        p{
          position: fixed;
          z-index:10;
          left: 50%;
          top: 50%;
          padding: 10px 40px;
          transform: translate(-50%, -50%);
          -webkit-transform: translate(-50%, -50%);
          background: #333;
          color:#fff; 
        }
      }
    }
  }
</style>
