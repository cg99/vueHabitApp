<template>
  <div id="app">
    <Header />
    <router-view/>
  </div>
</template>

<script>
  import Header from './components/layout/Header.vue';
  export default {
    name: "app",
    components: {Header}
  }
</script>

<style lang="scss" scoped>
   @import './assets/scss/main.scss';
</style>
