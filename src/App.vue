<template>
  
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <p></p>
  <IpPage/>
</template>

<script>
  
  import IpPage from '@/components/IpPage.vue'

export default {
  name: 'App',
  components: {
    IpPage
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
