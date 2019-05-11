<template>
  <div id="app">
    <div class="botton">© 北邮学生会网络部科技组</div>
    <snowFlake/>
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>-->
    <router-view/>
  </div>
</template>

<style>
#app {
  width: 100vw;
  height: 100vh;
  background: url("./assets/img/bg.png");
  background-size: contain;
  overflow: hidden;
}
html,
body {
  height: 100%;
  width: 100%;
}
body,
ol,
ul,
h1,
h2,
h3,
h4,
h5,
h6,
p,
th,
td,
dl,
dd,
form,
fieldset,
legend,
input,
textarea,
select {
  margin: 0;
  padding: 0;
}
.botton {
  position: absolute;
  top: 100%;
  margin-top: -3rem;
  z-index: 1;
  width: 100%;
  text-align: center;
  color: #555;
  font-size: 0.7rem;
}
</style>

<script>
import snowFlake from "@/components/snowflake.vue";
export default {
  components: {
    snowFlake
  }
};
</script>

