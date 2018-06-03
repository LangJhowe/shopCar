<template>
  <div id="app">
    <Header></Header>
    <SafeTip></SafeTip>
    <ShopCarList :shopListArr="this.shopListArr"></ShopCarList>
    <Footer :shopListArr="this.shopListArr" @allSelected="allSelected"></Footer>
  </div>
</template>

<script>
import Header from './components/header'
import SafeTip from './components/safetip'
import ShopCarList from './components/shopCarList'
import Footer from './components/footer'
import $ from 'jquery'

export default {
  name: 'App',
  components: {
    Header,
    SafeTip,
    ShopCarList,
    Footer
  },
  data(){
    return{
      //购物车中的数据
      shopListArr:[],
    }
  },
  //组件已经加载完毕，请求网络数据，业务处理
  mounted(){
    //1.请求本地的数据
    this.getLocalData();
  },
  methods:{
    getLocalData(){
      this.$http.get('../static/data/cart.json').then(response =>{
        const res = response.body;
        if(res){
          this.shopListArr = res.allShops.shopList
        }
        console.log(this.shopListArr)
      },response =>{
        alert('请求数据失败')
        //  error calback
      })
    },
    allSelected(selected){
      let SelectedArr = this.shopListArr.filter(shop => shop.shopChecked === !selected);
      this.shopListArr.map(shop => shop.shopChecked = !selected);
    }
  }

}
</script>


<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
