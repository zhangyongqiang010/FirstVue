<template>
    <div class="product-wrap">
        <div class="product-main">
          <p class="img-box">
            <!-- <img :src="imgUrl" alt=""/> -->
          </p>
          <div class="con-box">
              <p>
                <em class="price">￥100.00</em>
              </p>
          </div>
          <!-- <div v-else>
              <p class="price-box" v-if="1">
                <span class="name">会员PLUS价</span>
                <em class="price" v-show="lowerPrice">￥{{parseFloat(plusPrice).toFixed(2)}}</em>
              </p>
              <p class="price-box" v-else>
                  <span  class="name">京东价</span>
                  <em class="price" v-show="lowerPrice">￥{{parseFloat(lowerPrice).toFixed(2)}}</em>
                </p>
          </div> -->
          <div class="other">
            <span class="praise" v-if="good">好评率 98%</span>
            <!-- <span :class="['icon-label',icon]" v-if="text">{{text}}</span> -->
          </div>
        </div>
      </div>
      <div class="btn-box">
        <button class="btn" @click="goBuy">立即购买</button>
      </div>
  </div>
</template>
<script>
  export default {
    name: 'Product',
    data: function() {
      return {
        sku: 1161689,
        productName: '雅培(Abbott) 亲体 金装喜康宝婴儿配方奶粉 1段（0-6个月婴幼儿适用）900克',
        imgUrl: 'https://img14.360buyimg.com/n4/s280x280_jfs/t12223/184/496496336/324104/74ab9eb0/5a0d3eb2N5604ef8d.jpg!q90.webp',
        lowerPrice: "20",  // 较低价格
        higherPrice: "30.99", // 较高价格
        spreadPrice: "10.99", // 差价
        plusPrice: "24", // plus价格
        plusPriceValid: true, // plus会员价是否可用
        plusUser: true,  // 是否是plus会员
        srcId: 1, // 数据源：秒杀:1, 历史订单:2, 购物车:3, 关注:4, 浏览:5, 搜索:6, 7:飞单, 8:渠道价
        good: '99',
        text: '购物车已有',
        icon: 'icon-car',
      };
    },
    props:{

    },
    //监测数据sku的变化
    watch: {
      srcId(val){
        if(val==1){
          this.text="秒杀商品";
          this.icon="icon-kill";
        }
        if(srcId==2){
          this.text="历史订单";
          this.icon="icon-history";
        }
        if(srcId==3){
          this.text="购物车已有";
          this.icon="icon-car";
        }
        if(srcId==4){
          this.text="已关注";
          this.icon="icon-attention";
        }
        if(srcId==5){
          this.text="最近浏览";
          this.icon="icon-look";
        }
        if(srcId==6){
          this.text="";
          this.icon="";
        }
        if(srcId==7){
          this.text="";
          this.icon="";
        }
        if(srcId==8){
          this.text="";
          this.icon="";
        }
      }
    },

    computed: {
      url() {
        return 'http://jd.com/item/' + this.sku;
      },
    },
    
    created() {
      window.onload = () => {
        this.getResult()
        .then((response) => {
          return JSON.parse(response);
        })
        .then((json) => {
          console.log(json);
          const data = json.data;
          this.obj = data;
        })
        .catch((error) => {
          console.log('通过Native接口获取商品信息错误');
        });
      };
    },

    methods:{
      goBuy() {
        console.log("执行了goBuy")
        window.captain.confirmPurchase();
      },
      jumpToUrl() {
        this.localtion.href = this.url;
      },
      getResult() {
        return new Promise((resolve, reject) => {
          resolve(window.sharp.getResult());
          reject(new Error());
        });
      }
    }
  }
</script>

