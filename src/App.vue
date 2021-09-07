<template>
  <div id="app">
    <home-view msg="Welcome to Your Vue.js App" :home-view1="abc" />
  </div>
</template>

<script>
import HomeView from './views/HomeView.vue'

export default {
  name: 'App',
  
  components: {
    HomeView
  }
}
</script>

<style lang="scss">
@import '@/styles/styles.scss';
</style>
