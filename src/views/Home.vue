<template>
  <div class="home">
    <transition @after-leave="form=true" @after-enter="mzShow=true" name="title">
      <img v-if="show" class="titleImg" src="../assets/img/title.png">
    </transition>
    <transition @after-enter="botshow=true" name="mz">
      <img v-if="mzShow" class="mzImg" src="../assets/img/mz.png">
    </transition>
    <transition @before-leave="mzShow=false,show=false" name="bot">
      <div v-if="botshow" class="bot">
        <div class="buttonStar">
          <button @click="click()">点击留言</button>
        </div>
        <img class="botImg" src="../assets/img/bot.png" alt>
        <div class="pick"></div>
      </div>
    </transition>
    <transition name="form">
      <div v-if="form" class="form">
        <mail/>
      </div>
    </transition>
  </div>
</template>

<script>
import mail from '@/components/mail.vue'
export default {
  name: "home",
  data() {
    return {
      show: false,
      mzShow: false,
      botshow: false,
      form: false
    };
  },
  components: {mail},
  mounted() {
    this.show = true;
  },
  methods: {
    click(){
      this.botshow = false;
    }
  }
};
</script>
<style>
.titleImg {
  display: block;
  margin: auto;
  padding-top: 7vh;
  width: 80vw;
  max-width: 500px;
}
.mzImg {
  display: block;
  margin: auto;
  padding-top: 3vh;
  width: 35vw;
  max-width: 200px;
}
.bot {
  margin-top: -3vh;
  position: relative;
}
.botImg {
  width: 100vw;
}
.pick {
  width: 100vw;
  background-color: #d7486e;
  height: 100vh;
  margin-top: -5vh;
}
.buttonStar {
  position: absolute;
  display: flex;
  top: 15vh;
  justify-content: center;
  flex-direction: column;
  width: 100vw;
}
.buttonStar button {
  background-color: #d7486e;
  color: #ffc5d4;
  box-shadow: 5px 5px 5px rgba(10, 10, 10, 0.2);

  display: inline-block;
  position: relative;
  margin: 0 30px;
  padding: 10px 20px;
  font-size: 2em;
  text-align: center;
  text-decoration: none;
  border: #f0124b;

  -webkit-border-radius: 30px;
  -moz-border-radius: 30px;
  border-radius: 30px;

  -webkit-transition: all 0.15s ease;
  -moz-transition: all 0.15s ease;
  -o-transition: all 0.15s ease;
  -ms-transition: all 0.15s ease;
  transition: all 0.15s ease;
}
.title-enter-active {
  transition: all 0.8s ease-out;
}
.title-leave-active {
  transition: all 0.8s ease-out;
}
.title-enter, .title-leave-to
/* .title-leave-active for below version 2.1.8 */ {
  transform: translateY(-100px);
  opacity: 0;
}
.mz-enter-active {
  transition: all 0.8s cubic-bezier(0, 0, 0.21, 0.96);
}
.mz-leave-active {
  transition: all 0.8s cubic-bezier(0, 0, 0.21, 0.96);
}
.mz-enter,.mz-leave-to
/* .title-leave-active for below version 2.1.8 */ {
  transform: translateY(300px);
  opacity: 0;
}
.bot-enter-active {
  transition: all 0.8s cubic-bezier(0, 0, 0.21, 0.96);
}
.bot-leave-active {
  transition: all 0.8s cubic-bezier(0, 0, 0.21, 0.96);
}
.bot-enter,.bot-leave-to
/* .title-leave-active for below version 2.1.8 */ {
  transform: translateY(300px);
  opacity: 0;
}
.form-enter-active {
  transition: all 0.8s cubic-bezier(0, 0, 0.21, 0.96);
}
.form-leave-active {
  transition: all 0.8s cubic-bezier(0, 0, 0.21, 0.96);
}
.form-enter,.form-leave-to
/* .title-leave-active for below version 2.1.8 */ {
  transform:scale(0);
  opacity: 0;
}
</style>

