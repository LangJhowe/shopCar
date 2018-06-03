<template>
  <div class="tab_bar">
    <div class="tab_bar_left">
      <a href="javascript:;" ><input type="checkbox" @click="selectedAll(isSelectedAll)"  :checked="isSelectedAll" > </a>
      <span >全选</span>
      <div class="select_all">
        合计：<span class="total_price">{{totalPrice|moneyFormat(totalPrice)}}</span>
      </div>
    </div>
    <div class="tab_bar_right">
      <!--<a href="" class="pay">去结算</a>-->
      <button class="btn btn-info">去结算</button>
    </div>

  </div>
</template>

<script>
  export default {

  }
</script>

<style>

</style>
