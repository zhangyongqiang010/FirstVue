<template>
  <div id="shop-cart">
    <div class="cart-title">
      <ul>
        <li><span class="select" :class="{'selected':isSelectAll}" @click="selectAll(isSelectAll)"></span>全选</li>
        <li>商品</li>
        <li>数量</li>
        <li>单价(元)</li>
        <li>金额(元)</li>
        <li>操作</li>
      </ul>
    </div>
    <div class="cart-content">
      <ul>
        <li v-for="(item, index) in productList">
          <div class="selecteList"><span class="select" :class="{'selected':item.select}" @click="item.select=!item.select"></span>勾选</div>
          <div class="product">
            <div class="prodcutImg"><img src="../assets/logo.png"></div>
            <div class="prodcutTxt">
              <h3>{{ item.pro_name }}</h3>
              <p class="description">{{ item.pro_depot }}</p>
            </div>
          </div>
          <div class="productCount">
            <div class="numBox">
              <span class="decrease" @click="decreaseNum(index)"></span>
              <input class="num-input" type="text" v-model="item.pro_num"> 
              <span class="increase" @click="increaseNum(index)"></span>
            </div>
          </div>
          <div class="unitPrice">
            <p>￥ {{ item.pro_price.toFixed(2) }}</p>
          </div>
          <div class="totalPrice">
            <p>￥ {{ (item.pro_price * item.pro_num).toFixed(2) }}</p>
          </div>
          <div class="opration">
            <a class="delSingal" href="javascript:;" @click="delSingal(index)">删除</a>
          </div>
        </li>
      </ul>
    </div>
    <div class="bottom">
      <div class="left">
        <span class="delAll" @click="delAllProduct"></span>删除所选商品
        <span class="buyContinue"></span>继续购物
      </div>
      <div class="right">
        <span class="allTotalCount">{{ getTotal.totalCount }}</span>件商品总计(不含运费)：<span class="allTotalPrice">￥{{ getTotal.totalPrice }}</span><a href="javascript:;">去结算</a>
      </div>
    </div>
  </div>
</template>
<script>
  export default {
    name: 'Cart',
    data: function(){
      return {
        productList:[
          {
            'pro_name': '【斯文】甘油 | 丙三醇',//产品名称
            'pro_brand': 'skc',//品牌名称
            'pro_place': '韩国',//产地
            'pro_purity': '99.7%',//规格
            'pro_min': "215千克",//最小起订量
            'pro_depot': '上海仓海仓储',//所在仓库
            'pro_num': 1,//数量
            'pro_img': '../../images/ucenter/testimg.jpg',//图片链接
            'pro_price': 800//单价
          },
          {
            'pro_name': '【斯文】甘油 | 丙三醇',//产品名称
            'pro_brand': 'skc',//品牌名称
            'pro_place': '韩国',//产地
            'pro_purity': '99.7%',//规格
            'pro_min': "215千克",//最小起订量
            'pro_depot': '上海仓海仓储',//所在仓库
            'pro_num': 1,//数量
            'pro_img': '../../images/ucenter/testimg.jpg',//图片链接
            'pro_price': 800,//单价
            'select':true
          },
          {
            'pro_name': '【斯文】甘油 | 丙三醇',//产品名称
            'pro_brand': 'skc',//品牌名称
            'pro_place': '韩国',//产地
            'pro_purity': '99.7%',//规格
            'pro_min': "215千克",//最小起订量
            'pro_depot': '上海仓海仓储',//所在仓库
            'pro_num': 1,//数量
            'pro_img': '../../images/ucenter/testimg.jpg',//图片链接
            'pro_price': 800,//单价
            'select':true
          },
          {
            'pro_name': '【斯文】甘油 | 丙三醇',//产品名称
            'pro_brand': 'skc',//品牌名称
            'pro_place': '韩国',//产地
            'pro_purity': '99.7%',//规格
            'pro_min': "215千克",//最小起订量
            'pro_depot': '上海仓海仓储',//所在仓库
            'pro_num': 1,//数量
            'pro_img': '../../images/ucenter/testimg.jpg',//图片链接
            'pro_price': 800,//单价
            'select':true
          }
        ]
      }
    },
    props: {
      
    },
    computed: {
      isSelectAll: function(){
        //当勾选列表全选时总选框自动勾选
        return this.productList.every(function(val){
          return val.select;
        })
      },
      //获取总产品的价格以及件数
      getTotal: function(){
        //此处返回的是被勾选的产品列表，filter返回数组中满足条件的子集数组
        var proList = this.productList.filter(function(val){ return val.select });
        var totalPrice = 0;
        for(var i=0;i<proList.length;i++){
          totalPrice += proList[i].pro_num * proList[i].pro_price;
        }
        return { totalCount:proList.length, totalPrice:totalPrice.toFixed(2) };
      }
      
    },
    methods: {
      selectAll(isSelectAll){
        //点击总选项，勾选列表勾选状态只需要对总选项的状态取反即可
        for(var i=0;i<this.productList.length;i++){
          this.productList[i].select = !isSelectAll;
        }
      },
      delSingal(index){
        //一处当前项目的数据
        this.productList.splice(index,1);
      },
      delAllProduct: function(){
        //返回没有被选的数据
        this.productList = this.productList.filter(function(val){ return !val.select })
      },
      increaseNum(index){
        if(this.productList[index].pro_num >=0 && this.productList[index].pro_num  <10){
          this.productList[index].pro_num += 1;
        }else{
          alert("厂家就生产了十个，别再点了")
        }
      },
      decreaseNum(index){
        if(this.productList[index].pro_num >0 && this.productList[index].pro_num  <=10){
          this.productList[index].pro_num -= 1;
        }else{
          alert("不想要可以不勾选或者删除")
        }
      }
    },
    mounted:function () {
      //为productList添加select（是否选中）字段，初始值为true
      var _this=this;
      //为productList添加select（是否选中）字段，初始值为true
      this.productList.map(function (item) {
          _this.$set(item, 'select', true);
      })
      //要像上面这样写双向绑定才能起效，下面的写法是有问题的，双向绑定不起效的！
      this.productList.map(function (item) {item.select = true})
    }
  }
</script>
<style lang="scss" scoped>
  #shop-cart{
    .cart-title{
      border: 1px solid #aaa;
      font-size:18px;
      height:50px;
      text-align: center;
      ul{
        display: flex;
        justify-content: center;
        li{
          display: block;
          flex:1;
          float: left;
          font-family: sans-serif;
          list-style: none;
          font-size: 20px;
          font-weight: bold;
          line-height: 50px;
          text-align: center;
          .select{
              display: inline-block;
              margin-right: 5px;
              width:25px;
              height:25px;
              background-image: url(../assets/iconback.png);
              background-position:0% -9%; 
              
            }
            .selected{
              display: inline-block;
              margin-right: 5px;
              width:25px;
              height:25px;
              background-image: url(../assets/iconback.png);
              background-position:0% 60%;
            }
        }
      }
    }
    .cart-content{
      ul{
        li{
          font-family: sans-serif;
          list-style: none;
          font-size: 20px;
          display: flex;
          >div{
            flex:1;
            border-bottom: 1px solid #bbb;
          }
          div.selecteList{
            text-align: center;
            .select{
              display: inline-block;
              margin-top:25px;
              margin-right: 5px;
              vertical-align: -7px;
              width:25px;
              height:25px;
              background-image: url(../assets/iconback.png);
              background-position:0% -9%; 
              
            }
            .selected{
              background-position:0% 60%;
            }
          }
          div.product{
            display: flex;
            .prodcutImg{
              flex: 1;
              width:70px;
              height: 70px; 
              img{
                width: 70px;
                height: 70px;
                border: 1px solid #aaa;
              }
            }
            .prodcutTxt{
              flex: 1;
              margin-left: 3px;
              padding:5px 0px;
              text-align: left;
              h3{
                font-size: 15px;
              }
              .description{
                margin-top: 5px;
                height: 28px;
                line-height: 15px;
                overflow: hidden;
                font-size: 13px;
                color: #aaa;
              }
            }
          }
          div.productCount{
            padding: 20px 0px;
            .numBox{
              margin:0px auto;
              width:100px;
              border:1px solid #aaa;
              .increase{
                display: inline-block;
                width:25px;
                height:20px;
                background-image: url(../assets/iconback.png);
                background-position: -73% 43%;
              }
              .num-input{
                display: inline-block;
                width:32px;
                height:26px;
                vertical-align: 6px;
                text-align: center;
                outline:none;
                border: 0px;
                border-left:1px solid #aaa;
                border-right:1px solid #aaa;
              }
              .decrease{
                display: inline-block;
                width:25px;
                height:15px;
                background-image: url(../assets/iconback.png);
                background-position:26% 43%; 
              }
            }
          }
          div.unitPrice{
            p{
              line-height: 70px;
            }
          }
          div.totalPrice{
            p{
              line-height: 70px;
            }
          }
          div.opration{
            a{
              line-height: 70px;
              text-decoration: none;
              color:#df6705;
            }
          }
        }
      }
    }
    .bottom {
      display: flex;
      // padding: 20px 0px 40px 30px;
      // justify-content: center;
      // align-items: middle;
      .left{
        flex:1;
        text-align: left;
        .delAll{
          display: inline-block;
          width:25px;
          height:25px;
          background-image: url(../assets/iconback.png);
          background-position:52% -23%; 
        }
        .buyContinue{
          display: inline-block;
          width:25px;
          height:25px;
          margin-left:50px;
          background-image: url(../assets/iconback.png);
          background-position:32% -23%; 
        }
      }
      .right{
        flex:1;
        text-align: right;
        .allTotalCount{
          color: #df6705;
          margin-right:5px;
        }
        .allTotalPrice{
          margin-right:20px;
          color: #df6705;
          font-size:24px;
        }
        a{
          padding:20px 20px;
          display: inline-block;
          background: #df6705;
          color: #fff;
          text-decoration: none;
        }
      }
    }
  }
</style>