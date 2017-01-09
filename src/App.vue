<template>
  <div id="app">
    <v-header></v-header>
    <div class="tab">I am Tab</div>
    <div class="content">I am Content</div>
  </div>
</template>

<script>
  import header from './components/header';

  export default {
    components: {
      'v-header': header
    }
  };
</script>

<style>
</style>
