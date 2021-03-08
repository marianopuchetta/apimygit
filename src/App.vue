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
background: rgb(36,0,6);
background: linear-gradient(90deg, rgba(36,0,6,0.5718662464985995) 0%, 
rgba(9,81,121,1) 27%, rgba(166,0,255,0.8211659663865546) 65%);
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
