<template>
  <div class="shopCart_list">
    <section v-for="(shop,index) in shopListArr">
      <div class="shopCart_list_title">
        <span class="cart_logo"></span>
        <span class="cart_title">京东自营</span>
        <span class="cart_sale">您享受满100元免运费服务</span>
      </div>
      <div class="shopCart_list_con">
        <div class="list_con_left">
          <label :for="shop.shopId"><div :id="shop.shopId" :class="{'shop-actived':shop.shopChecked}" @click="singerShopSelected(shop)" :checked="shop.checked"></div></label>
        </div>
        <div class="list_con_right">
          <div class="shop_img">
            <img width="100" height="100" :src="shop.shopImage" alt="图片未下载">
          </div>
          <div class="shop_con">
            <a href="javascript:void(0)" v-text="shop.shopName"></a>
          </div>
          <div class="shop_price">
            <div class="singer"><i>￥</i>{{moneyFormat(shop.shopPrice)}}</div>
            <div class="total"><i>￥</i>{{moneyFormat(shop.shopPrice*shop.shopNumber)}} </div>
          </div>
          <div class="shop_deal">
            <div class="shop_deal_left">
              <span @click="singerShopPrice(shop,false)">-</span>
              <input type="tel" v-model="shop.shopNumber" value="shop.shopNumber">
              <span @click="singerShopPrice(shop,true)">+</span>
            </div>
            <div class="shop_deal_right">
              <a  href="javascript:void(0)" @click="clickTrash(shop)" data-toggle="modal" data-target="#myModal">
                删除
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
  export default {
    props:{
      shopListArr:{
        type:Array,
        required:true
      }
    },
    data(){
      return{
      }
    },
    methods:{
      //是否确定选择商品
      singerShopSelected(shop){
        shop.shopChecked = !shop.shopChecked
      },
      singerShopPrice(shop,dir){
        if(shop.shopNumber === 1 && dir ===false){
          alert("该商品一件起售");
          return;
        }
        shop.shopNumber = dir ? shop.shopNumber + 1 : shop.shopNumber - 1;
        shop.shopNumber = shop.shopNumber < 0 ? 0 : shop.shopNumber
      },
      clickTrash(shop){
        this.shopListArr.splice(this.shopListArr.findIndex(eshop => eshop.shopId === shop.shopId),1);
      },
      moneyFormat(allprice){
        return allprice.toFixed(2)
      }
    }
  }
</script>
<style  scoped lang="stylus">
  .shopCart_list{
    section{
      border-top 1px solid #eee
      border-bottom 1px solid #eee
      background-color #fff
      margin-bottom 10px
      .shopCart_list_title{
        border-bottom 1px solid #eee
        padding 0 10px
        .cart_logo{
          float left
        }
        .cart_title{

        }
        .cart_sale{
          float right
          color red

        }
      }
      .shopCart_list_con{
        height 150px
        padding 0 8px
        .list_con_left{
          position relative
          label{
            color: rgb(51, 51, 51);
            display: block;
            font-family: -apple-system, Helvetica, sans-serif;
            font-size: 12px;
            font-style: normal;
            height: 150px;
            left: 0px;
            line-height: 18px;
            outline-color: rgb(51, 51, 51);
            outline-style: none;
            outline-width: 0px;
            position: absolute;
            top: 0px;
            width: 63px;
            z-index: 1;
            div{
              margin-top 60px
              margin-left 15px
              width 20px
              height 20px
              border-radius 50%
              border 1px solid rgb(166,166,166)
            }
            .shop-actived{
              background url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACgAAAAoCAMAAAC7IEhfAAAANlBMVEUAAADpPD3tO0HrPD7qPD7qOz7qPD3pOz7qPD3qPD3pPD7rPD/pQkLzRkbqQEDpPUH/VVXpOz3Rbw31AAAAEXRSTlMA6iuA81DZ07+rpXIjFgw7CVCvuuwAAADZSURBVDjLjdVbrsMgDATQoThAeYTO/jd7fy6ioU7wfCXKEY4lMLimlpyCSEi5VNym+civRN9UdnrhEvHnrzsclbhjdZ438Rf2efM27w9mptOkUndT/eAm/x2dbgfdOQsbijfZQ2lzwf2S8eHf+ugzAvXBvdDHc0V5ci83XgqyyTEjmRwTgskxQEyOAjE5yix9dHfvGGYzfXzUHBPysozumFG4SNWxoC4t6I4ViFepuzi22ZSqo183rutdc9LMR8F+uOzH1T4A9iPFPqTsY88+SO2j2T7szdfHHy1xS+1j0wOxAAAAAElFTkSuQmCC")
              background-size 100% 100%
            }
          }
        }
        .list_con_right{
          padding-left 63px
          position relative

          .shop_img{
            position absolute
            top 25px
          }
          .shop_con{
            position absolute
            padding-top 20px
            padding-left 105px
            text-align left
            a{
              display inline-block
              height 30px
              text-overflow ellipsis
              font-size 12px
              line-height 15px
              color: #000
              text-decoration none
            }
          }
          .shop_price{
            padding-top 100px
            padding-left 100px
            overflow hidden
            color: darkred
            .singer{
              float left
            }
            .total{
              float right
            }
          }
          .shop_deal{
            display block
            padding-left 100px
            text-align left
            .shop_deal_left{
              display inline-block
              *{
                float left
                height 20px
              }
              input{
                display inline-block
                width 50px
                text-align center
              }
              span{
                display inline-block
                width 20px
                background-color #eee
                text-align center
              }
              span:hover{
                background-color #e7e7e7
              }
            }
            .shop_deal_right{
              float right
              a{
                display inline-block
                padding 3px
                height 20px
                line-height 12px
                color: #000
                text-decoration none
                cursor pointer
                border-radius 3px
                border 2px solid #eee
              }
              a:hover{
                background-color #eee
              }
            }

          }
        }

      }
    }

  }

</style>
