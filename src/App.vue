<template>
  <div id="app">
    <mainHeader :seller="seller"></mainHeader>
    <div class="tab">
      <div class="tab-item"><router-link to="/goods">商品</router-link></div>
      <div class="tab-item"><router-link to="/ratings">评价</router-link></div>
      <div class="tab-item"><router-link to="/seller">商家</router-link></div>
    </div>
    <router-view></router-view>
    
  </div>
</template>

<script>
  import mainHeader from "./components/header/header.vue";
  import axios from "axios"

export default {
  components: {
    mainHeader,
  },
  data() {
    return {
      seller: {}
    }
  },
  created() {
    axios.get("/data.json").then((res) => {
      if (200 == res.status && res.data) {
        let data = res.data;
        console.log(data);
        this.seller = data.seller;
      }
    }).catch((error) => {
      console.log("出错了", error);
    })
  },
}
</script>

<style lang="stylus" scoped>
  #app
    .tab
      display: flex
      width: 100%
      height : 0.8rem
      line-height : 0.8rem
      .tab-item
        flex : 1
        text-align : center
        height : 0.8rem
        & > a
          display : block   /*点到标签的边上也可以点中，不然无法点中*/
</style>
