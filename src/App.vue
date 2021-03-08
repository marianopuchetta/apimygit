<template>
  <div id="app" class="container">
    <Home/>
  </div>
</template>

<script>
import Home from './components/home.vue'
export default {
  name: 'App',
  components: {
    Home
  }
}
</script>

<style scoped>
body {
  display: flex;
  flex-flow: column wrap;
  align-items: center;
background: #FC5C7D;  /* fallback for old browsers */
background: -webkit-linear-gradient(to right, #6A82FB, #FC5C7D);  /* Chrome 10-25, Safari 5.1-6 */
background: linear-gradient(to right, #6A82FB, #FC5C7D); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
}
html {
  height: 100%;
}
#app {
  margin:0;
  padding: 0;
  box-sizing: border-box;
  display: flex;
  flex-flow: column wrap;
  text-align: center;
  justify-content: center;
  height: 100%;
}
</style>
