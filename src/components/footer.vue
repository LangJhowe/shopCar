<template>
  <div class="footer">
    <div class="footer-left">
      <div  @click="allSelected" :class="['all-selected',{'all-actived':allSelecte}]"></div>
      <span>全选</span>
    </div>
    <div class="footer-right">
      <div @click="pay" class="pay">去结算</div>
      <div class="total">
        <span>合计</span>
        <span class="total-price"><i>￥</i>{{allPrice}}</span>
      </div>
    </div>
  </div>
</template>

<script>
  export default{
    props:{
      shopListArr:{
        type:Array,
        required:true
      }
    },
    data(){
      return{
        allSelecte:false,
      }
    },
    computed:{
      allPrice(){
        let allPrice=0;
        let checkedArr = this.shopListArr.filter(shop => shop.shopChecked === true);

        //for( in )不可 allPrice为NaN
        // for(let shop in this.shopListArr){
        //   allPrice = allPrice + shop.shopNumber*shop.shopPrice;
        // }

        //for方法
        // for(let i = 0;i < checkedArr.length;i++){
        //   allPrice = allPrice + checkedArr[i].shopNumber* checkedArr[i].shopPrice;
        // }
        //map方法
        checkedArr.map(shop => allPrice = allPrice + shop.shopNumber*shop.shopPrice);
        // console.log(checkedArr[0].shopNumber * checkedArr[0].shopPrice);
        return allPrice.toFixed(2);
      },
    },
    methods:{
      //全选
      allSelected(){
        this.$emit('allSelected',this.allSelecte);
        this.allSelecte = !this.allSelecte
      },
      pay(){

      },
      moneyFormat(allprice){
        return allprice.toFixed(2)
      }
    }
  }
</script>
<style scoped lang="stylus">
.footer{
  position fixed
  width 100%
  height 50px
  padding 0 0 0 8px
  bottom 0
  background-color #fff
  border-top  1px solid #eee
  .footer-left{
      float left
      padding 15px
    .all-selected{
      float left
      width 20px
      height 20px
      border-radius 50%
      border 1px solid rgb(166,166,166)
    }
    .all-actived{
      background url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACgAAAAoCAMAAAC7IEhfAAAANlBMVEUAAADpPD3tO0HrPD7qPD7qOz7qPD3pOz7qPD3qPD3pPD7rPD/pQkLzRkbqQEDpPUH/VVXpOz3Rbw31AAAAEXRSTlMA6iuA81DZ07+rpXIjFgw7CVCvuuwAAADZSURBVDjLjdVbrsMgDATQoThAeYTO/jd7fy6ioU7wfCXKEY4lMLimlpyCSEi5VNym+civRN9UdnrhEvHnrzsclbhjdZ438Rf2efM27w9mptOkUndT/eAm/x2dbgfdOQsbijfZQ2lzwf2S8eHf+ugzAvXBvdDHc0V5ci83XgqyyTEjmRwTgskxQEyOAjE5yix9dHfvGGYzfXzUHBPysozumFG4SNWxoC4t6I4ViFepuzi22ZSqo183rutdc9LMR8F+uOzH1T4A9iPFPqTsY88+SO2j2T7szdfHHy1xS+1j0wOxAAAAAElFTkSuQmCC")
      background-size 100% 100%
    }
    span{
      float left
      padding:0 8px
    }

  }
  .footer-right{
    float right
    height 100%
    .pay{
      float right
      padding 0 10px
      height 100%
      line-height 50px
      background rgb(228,57,50)
      color: #fff
      font-weight bold
    }
    .total{
      float right
      height 100%
      span{
        height 100%
        line-height 50px
      }
      .total-price{
        padding 0 10px
        color rgb(228,57,50)
        font-size 20px
        i{
          font-size 12px
        }
      }
    }
  }
}
</style>
