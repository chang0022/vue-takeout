<template>
  <div class="star" :class="star-type">
    <span v-for="itemClass in itemClasses" :class="itemClass" class="star-item"></span>
  </div>
</template>

<script>
  export default {
    props: {
      size: {
        type: Number
      },
      score: {
        type: Number
      }
    },
    computed: {
      starType() {
        return 'star-' + this.size;
      }
    }
  };
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  .star
    font-size 0
    .star-item
      display inline-block
      background-repeat no-repeat
    &.star-48
    &.star-36
    &.star-24

</style>
