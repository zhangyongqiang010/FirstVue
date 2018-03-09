<template>
  <div id="tab">
    <div class="tab-title">
      <ul>
          <li :class="{'tabli':true,'active':tabId===0}" @click="tabId=0">Tab一</li>
          <li :class="{'tabli':true,'active':tabId===1}" @click="tabId=1">Tab二</li>
          <li :class="{'tabli':true,'active':tabId===2}" @click="tabId=2">Tab三</li>
          <li :class="{'tabli':true,'active':tabId===3}" @click="tabId=3">Tab四</li>
          <li class="clear"></li>
      </ul>
    </div>
    <div class="tab-content">
        <div v-show="tabId===0">
          <Cart/>
        </div>
        <div v-show="tabId===1">
          <Cart/>
        </div>
        <div v-show="tabId===2">
          <Cart/>
        </div>

        <div v-show="tabId===3">
          别点了，没有了
        </div>
    </div>
  </div>
</template>
<script>
  import Cart from './Cart'
  export default{
    name: 'Tab',
    data: function(){
      return { 'tabId':0 }
    },
    components: {
      Cart
    }
  }
</script>
<style lang="scss" scoped>
  #tab{
    text-align: center;
    .tab-title{
      display: block;
      // height:50px;
      width: 100%;
      ul{
        margin:0;
        padding:0;
        display: flex;
        li.tabli{
          flex:1;
          padding: 10px 20px;
          margin: 0px; 
          float: left;
          font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
          font-size: 24px;
          color: #df6705;
          background: #fff;
          list-style: none;
          border: 1px solid #eee;
        }
        li.active{
          
          color:#fff;
          background: #df6705;
          border-bottom: 1px solid #df6705;
        }
        .clear{
          list-style: none;
          clear: both;
          zoom: 0;
        }
      }
    }
    .tab-content{
      margin-top:10px;
      width: 100%;
    }
  }
</style>