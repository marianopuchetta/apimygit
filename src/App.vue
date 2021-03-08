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
background: #16A085;  /* fallback for old browsers */
background: -webkit-linear-gradient(to bottom, rgba(244, 208, 63, 0.7), #16A085);  /* Chrome 10-25, Safari 5.1-6 */
background: linear-gradient(to bottom, rgba(244, 208, 63, 0.9), #16A085); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
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
