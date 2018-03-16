<template>
  <div class="todobox">
    <h2>小目标列表</h2>
    <h3>添加小目标</h3>
    <input type="text" class="keyBox" placeholder="输入小目标候按回车确认" @keyup.13="addList" v-model="addTxt"></br>
    <div class="goalTxtBox">
      <span class="goalTxt">共有<span class="goalCount">{{ finished+unfinished }}</span>个目标</span>
      <span class="goalTxt">已完成<span class="goalCount">{{ finished }}</span>个目标</span>
      <span class="goalTxt">未完成<span class="goalCount">{{ unfinished }}</span>个目标</span>
    </div>
    <div class="verbBox">
      <input type="radio" name="verbType" checked="true" @click="verbType(1)"><span>所有目标</span>
      <input type="radio" name="verbType" @click="verbType(2)"><span>已完成目标</span>
      <input type="radio" name="verbType" @click="verbType(3)"><span>未完成目标</span>
    </div>
    <ul>
      <li v-for="(item,index) in newList" @click="">
        <input type="checkbox" v-model="item.status" @click="item.status = !item.status">
        {{ item.name }}
        <span class="del" @click="delList(index)">X</span></br>
        <input class="edit" v-model="item.name">
      </li>
      
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'ToDoList',
    data () {
      return {
        addTxt:"",
        proList:[
          { name:"HTML5",status:false },
          { name:"CSS3",status:false },
          { name:"vue",status:false },
          { name:"react",status:false }
        ],
        newList: []
      }
    },
    computed: {
      finished(){
        return this.proList.filter(function(item){
          return item.status
        }).length;
      },
      //未完成的目标个数
      unfinished(){
        return this.proList.filter(function(item){
          return !item.status
        }).length;
      }
    },
    methods: {
      addList(){
        this.proList.push({
          name:this.addTxt,
          status:false
        })
        this.addTxt = "";
      },
      verbType(type){
        switch(type){
          case 1: this.newList = this.proList;break;
          case 2: this.newList = this.proList.filter(function(item){ return item.status});break;
          case 3: this.newList = this.proList.filter(function(item){ return !item.status});break;
        }
      },
      delList(index){
        //根据索引，删除数组某一项
        this.proList.splice(index,1);
        //更新newList  newList可能经过this.prolist.filter()赋值，这样的话，删除了prolist不会影响到newList  那么就要手动更新newList
        this.newList=this.proList;
      }
    },
    mounted(){
      //初始化状态，默认勾选所有目标
      this.newList = this.proList;
    }
    
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.todobox{
  padding:20px 30px;
  text-align: left;
  h2{
    font-weight: bold;
    font-size:26px;
  }
  h3{
    margin-top:20px;
    font-weight: normal;
    font-size:20px;
  }
  .keyBox{
    margin:5px 0px;
    padding:0px 10px;
    border:1px solid #aaa;
    width:50%;
    height:30px;
    outline:none;
  }
  .goalTxtBox{
    margin:5px 0px;
    .goalTxt{
      
      .goalCount{
        font-size:20px;
        margin:0px 5px;
        color:#df6705;
        font-weight:bold;
      }
    }
  }
  .verbBox{
    margin:10px 0px;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 5px 10px 5px 0px;
    width:50%;
    height:30px;
    line-height: 30px;
    border:1px solid #fff;
    .del{
      display: none;
      margin-left:500px;
      font-size:20px; 
      color: red;
    }
  }
  li:hover{
    border:1px solid #aaa;
    cursor: pointer;
    .del{
      display: block;
      padding:0px 10px;
      margin-top:-30px;
      text-align: right;
    }
  }
  a {
    color: #42b983;
  }
}
</style>