<template>
  <div id="app">
    <mainHeader></mainHeader>
    <div class="tab">
      <div class="tab-item">商品</div>
      <div class="tab-item">评价</div>
      <div class="tab-item">商家</div>
    </div>
    <div class="content">content</div>
    
  </div>
</template>

<script>
  import mainHeader from "./components/header/header.vue";

export default {
  components: {
    mainHeader,
  }
}
</script>

<style lang="stylus" scoped>
  #app
    .tab
      display: flex;
      width: 100%;
      height : 40px;
      line-height : 40px;
      .tab-item
        flex : 1;
        text-align : center;
</style>
