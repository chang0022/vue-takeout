<template>
  <div class="cartControl">
    <div class="cart-decrease icon-remove_circle_outline" v-show="food.count > 0"></div>
    <div class="cart-count" v-show="food.count > 0">{{food.count}}</div>
    <div class="cart-add icon-add_circle" @click="addGoods"></div>
  </div>
</template>

<script>
  import Vue from 'vue';

  export default {
    props: {
      food: {
        type: Object
      }
    },
    methods: {
      addGoods(event) {
        if (!event._constructed) {
          return false;
        }
        if (!this.food.count) {
          Vue.set(this.food, 'count', 1);
        } else {
          this.food.count++;
        }
      }
    }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
  .cartControl
    font-size 0
    .cart-decrease, .cart-add
      display inline-block
      padding 6px
      font-size 24px
      line-height 24px
      color rgb(0, 160, 220)
    .cart-count
      display inline-block
      vertical-align top
      width 12px
      padding-top 6px
      font-size 10px
      line-height 24px
      text-align center
      color rgb(147, 153, 159)
</style>
