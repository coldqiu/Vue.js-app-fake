<template>
  <div id="app">
    <!--<img src="./assets/logo.png">-->
    <v-header :seller="seller"></v-header>
    <div class="tab border-1px">
      <div class="tab-item">
        <router-link to="/goods">商品</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/ratings">评论</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/seller">商家</router-link>
      </div>
    </div>
    <!--<keep-alive>-->
      <router-view :seller="seller"></router-view>
    <!--</keep-alive>-->

  </div>
</template>

<script tpye="text/ecmascript-6">

//export default {
//  name: 'app'
//}


import header from './components/header/header.vue'
const ERR_OK = 0;
export default {
  data() {
    return {
      seller: {}
    }
  },
   created () {
    this.$http.get('/api/seller').then(response => {
      response = response.body;

      if (response.errno === ERR_OK) {
        this.seller = response.data;
      }

    }, response => {
      // error callback

    });
  },

  components: {'v-header': header}
};
</script>


<style lang="stylus" rel="stylesheet/stylus">
  @import "./common/stylus/mixin.styl"


  #app
    .tab
      display: flex
      width: 100%
      height: 40px
      line-height: 40px
      //border-bottom: 1px solid rgba(7, 17, 27, 0.1)
      border-1px(rgba(7, 17, 27, 0.1))
      .tab-item
        flex: 1
        text-align: center
        & > a
          display: block
          font-size: 14px
          font-weight: 600
          color: rgb(77, 85, 93)
          &.router-link-active
            color: rgb(240, 20, 20)

</style>

<!--/*#app {*/-->
  <!--/*font-family: 'Avenir', Helvetica, Arial, sans-serif;*/-->
  <!--/*-webkit-font-smoothing: antialiased;*/-->
  <!--/*-moz-osx-font-smoothing: grayscale;*/-->
  <!--/*text-align: center;*/-->
  <!--/*color: #2c3e50;*/-->
  <!--/*margin-top: 60px;*/-->
<!--/*}*/-->

