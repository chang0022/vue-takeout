<template>
  <div class="cartControl">
    <transition name="move">
      <div class="cart-decrease" v-show="food.count > 0" @click="decreaseGoods">
        <transition name="inner">
          <span class="inner icon-remove_circle_outline"></span>
        </transition>
      </div>
    </transition>
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
      },
      decreaseGoods(event) {
        if (!event._constructed) {
          return false;
        }
        if (this.food.count) {
          this.food.count--;
        }
      }
    }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
  .cartControl
    font-size 0
    .cart-decrease
      display inline-block
      padding 6px
      &.move-enter-active, &.move-leave-active
        transition all .4s linear
      &.move-enter, &.move-leave-active
        opacity: 0
        transform translate3d(24px, 0, 0)
      .inner
        display inline-block
        font-size 24px
        line-height 24px
        color rgb(0, 160, 220)
        &.inner-enter-active, &.inner-leave-active
          transition: all .4s linear
          transform rotate(0)
        &.inner-enter, &.inner-leave-active
          transform rotate(180deg)
    .cart-count
      display inline-block
      vertical-align top
      width 12px
      padding-top 6px
      font-size 10px
      line-height 24px
      text-align center
      color rgb(147, 153, 159)
    .cart-add
      display inline-block
      padding 6px
      font-size 24px
      line-height 24px
      color rgb(0, 160, 220)
</style>
