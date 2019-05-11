<template>
  <div id="app">
    <snowFlake/>
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div> -->
    <router-view/>
  </div>
</template>

<style>
#app {
  width: 100vw;
  height: 100vh;
  background: url("./assets/img/bg.png");
  background-size:contain;
  overflow: hidden;
}
html,body{height: 100%;width: 100%;}
body,ol,ul,h1,h2,h3,h4,h5,h6,p,th,td,dl,dd,form,fieldset,legend,input,textarea,select{margin:0;padding:0} 
</style>

<script>
import snowFlake from "@/components/snowflake.vue"
export default {
  components: {
    snowFlake
  }
}
</script>

