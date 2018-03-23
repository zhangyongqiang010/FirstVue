<template>
  <div id="pageation">
    <ul>
        <li v-show="current != 1" class="prev" @click="current-- && goto(current)">上一页</li>
        <li v-for="index in pages" @click="goto(index)" :class="{'active':current == index}" :key="index">{{index}}</li>
        <li v-show="allpage != current && allpage != 0" class="next" @click="current++ && goto(current)">下一页</li>
        <li class="clear"></li>
    </ul>
  </div>
</template>
<script>
  export default {
    name: 'Pageation',
    data: function(){
      return {
        current:1,  //当前点击状态的页码数
        showItem:5, //展示出来的页码数
        allpage:13 //总页数
      }
    },
    computed: {
      pages:function(){
        var pag = [];
        if( this.current < this.showItem ){ //如果当前的激活的项 小于要显示的条数
            //总页数和要显示的条数那个大就显示多少条
            var i = Math.min(this.showItem,this.allpage);
            //循环出五条数据
            while(i){
              pag.unshift(i--);
            }
          }else{ //当前页数大于显示页数了
          //middle值为起始页码
            var middle = this.current - Math.floor(this.showItem / 2 ),//从哪里开始 3
            i = this.showItem;
            //如果中间值大于
            if( middle >  (this.allpage - this.showItem)  ){
              middle = (this.allpage - this.showItem) + 1
            }
            while(i--){
              pag.push( middle++ );
            }
          }
        return pag
      }
    },
    methods: {
      goto(index){
        //点击当前点击状态的页码时不做处理直接return
        if(this.current == index) return false;
        this.current = index;
      }
    }
  }
</script>
<style lang="scss" scoped>
  #pageation{
    display: block;
    text-align: center;
    ul{
      display: inline-block;
      li{
        margin:20px 5px 20px 5px;
        padding:5px 10px;
        float: left;
        list-style: none;
        border:1px solid rgb(250, 240, 240);
        color: #408fcd;
        cursor: pointer;
      }
      li.active{
        color:#fff;
        background: #408fcd;
        border-bottom: 1px solid #aaa;
      }
      .clear{
        display: none;
        list-style: none;
        clear: both;
        zoom: 0;
      }
    }
  }
</style>