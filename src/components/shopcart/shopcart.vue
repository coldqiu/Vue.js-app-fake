<template>
  <div class="shopcart">
    <div class="content">
      <div class="content-left">
          <div class="logo-wrapper">
            <div class="logo" :class="{'hightlight' : totalCount>0}">
              <i class="icon-shopping_cart" :class="{'hightlight' : totalCount>0}"></i>
            </div>
            <div class="num" v-show="totalCount>0">{{totalCount}}</div>
          </div>
          <div class="price" :class="{'hightlight' : totalPrice>0}">{{totalPrice}}元</div>
          <div class="desc">另需配送费￥{{deliveryPrice}}元</div>
      </div>
      <div class="content-right">
        <div class="pay">￥{{minPrice}}元起配送</div>
      </div>
    </div>
  </div>
</template>

<script tpye="text/ecmascript-6">

  export default {

    props: {
      selectFoods: {
        type: Array,
        default() {
          return [
            {price:10, count:1}
          ];
        }
      },

      deliveryPrice: {
        type: Number,
        default: 0
      },
      minPrice: {
        type: Number,
        default: 0
      }
    },
    computed: {
      totalPrice() {
        let total = 0;
        this.selectFoods.forEach((food) => {
          total += food.price * food.count;
        });
        return total;
      },

      totalCount() {
        let count = 0;
        this.selectFoods.forEach((food) => {
          count += food.count;
        });
        return count;
      },

    },



  };

</script>

<style lang="stylus" rel="stylesheet/stylus">

  .shopcart
    position: fixed
    left: 0
    bottom: 0
    z-index: 50
    width: 100%
    height: 48px
    //background: #000
    .content
      display: flex
      background: #141d27
      .content-left
        flex: 1
        .logo-wrapper
          display: inline-block
          position: relative
          top: -10px
          margin: 0 12px
          padding: 6px
          width: 56px
          height: 56px
          box-sizing: border-box
          vertical-align: top
          border-radius: 50%
          background: #141d27
          .logo
            width: 100%
            height: 100%
            border-radius: 50%
            text-align: center
            background: #2b343c
            &.hightlight
              background: rgb(0, 160, 220)
            .icon-shopping_cart
              line-height: 44px
              font-size: 24px
              color: #80858a
              &.hightlight
                color: #fff

          .num
            position: absolute
            top: 0
            left: 30px
            width: 24px
            height: 16px
            line-height: 16px
            text-align: center
            border-radius: 16px
            font-size: 9px
            font-weight: 700
            color: #fff
            background: rgb(240, 20 ,20)
            box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.4)

        .price
          display: inline-block
          vertical-align: top
          margin-top: 12px
          line-height: 24px
          padding-right: 12px
          box-sizing: border-box
          border-right: 1px solid rgba(255, 255, 255, 0.1)
          font-size: 16px
          font-weight: 700
          color: rgba(255, 255,2553, 0.4)
          &.hightlight
            color: #fff
        .desc
          display: inline-block
          vertical-align: top
          margin: 12px 0 0 12px
          line-height: 24px
          color: rgba(255, 255, 255, 0.4)
          font-size: 10px


      .content-right
        flex: 0 0 105px
        width: 105px
        .pay
          height: 48px
          line-height: 48px
          text-align: center
          font-size: 12px
          font-weight: 700
          color: rgba(255, 255, 255, 0.4)
          background: #2B333B
</style>

