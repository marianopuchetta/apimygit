<template>
  <div id="app" >
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
background-image: radial-gradient(circle, #f669b9, #e374cd, #cc7fdd, #b289e8, #9692ee, #7a9ff9, #59abfe, #2fb6ff, #00c9ff, #00daff, #00eaf8, #38f8eb);
  width: 100% !important;
}
html {
  height: 100%;
    width: 100% !important;

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
    width: 100% !important;
}
</style>
