<template>
  <div class="likeBody">
    <div class="wrapper">
      <div class="container">
        <div class="topfold"></div>
        <div class="letter">
          <div class="upper">
            <div class="front">
              <p>
                定下一个目标吧，今年为母亲做一件事情。
                <br>在明年询问完成情况
              </p>
            </div>
            <div class="back"></div>
          </div>
          <form v-show="show" id="email">
            <textarea name="text" v-model="message" placeholder="写下目标吧"></textarea>
            <input name="email" v-model="email" placeholder="你的邮箱" type="text">
            <span class="submitwrap">
              <input type="submit" value="DO IT">
            </span>
          </form>
        </div>
      </div>
      <svg
        version="1.1"
        id="Capa_1"
        x="0px"
        y="0px"
        viewBox="0 0 58 32"
        style="enable-background:new 0 0 58 32;"
        xml:space="preserve"
      >
        <g class="bottom">
          <polygon class="st0" points="0,32 0,0 21,16 	"></polygon>
          <polygon class="st0" points="58,32 58,0 37,16 	"></polygon>
          <path
            class="st1"
            d="M57,31.2L37,16H21L1,31.2c-0.4,0.3-1,0-1-0.5V32h58v-1.3C58,31.2,57.4,31.5,57,31.2z"
          ></path>
        </g>
      </svg>
    </div>
  </div>
</template>

<script>
import { TimelineMax, Circ, Expo } from "gsap/TweenMax";
import $ from "jquery";
export default {
  name: "email",
  data() {
    return {
      email: "",
      message: "",
      show: false
    };
  },
  methods: {
    click() {}
  },
  mounted() {
    var tl = new TimelineMax({
      repeat: 0,
      delay: 0
    });
    setTimeout(() => {
      this.show = true;
    }, 1000);
    tl.to(".topfold", 0.5, {
      transformOrigin: "50% 0%",
      x: 0,
      y: 0,
      fill: "#d5d3bb",
      scaleY: -1,
      delay: 0,
      ease: Circ.easeIn
    });
    tl.to(".letter", 0.5, {
      x: 0,
      y: -200,
      delay: 0,
      height: 200,
      ease: Circ.easeOut
    });
    tl.to(".upper", 1.2, {
      x: 0,
      transformOrigin: "50% 100%",
      rotationX: -180,
      delay: 0.3,
      height: 200,
      ease: Circ.easeOut
    });
    tl.to(".letter", 0.5, {
      x: 0,
      y: -200,
      rotationX: 0,
      delay: 0,
      ease: Circ.easeInOut
    });

    $("#email").submit(event => {
      event.preventDefault();
      $.ajax({
        type: "POST",
        url: "https://leancloud.cn:443/1.1/classes/MainData",
        data: JSON.stringify({ message: this.message, email: this.email }),
        beforeSend: function(request) {
          request.setRequestHeader("X-LC-Id", "4JIJoRMRUllBiyJCT6BUB3jl-gzGzoHsz");
          request.setRequestHeader("X-LC-Key", "CQacJfeCpPPgPpMm54Pj5Qbw");
          request.setRequestHeader("content-type", "application/json");
        },
        success: () => {
          alert("提交成功，谢谢参与")
        },
        error: () => {
          alert("提交失败，请稍后再试")
        }
      });
      var tl2 = new TimelineMax({
        repeat: 0,
        delay: 0
      });

      tl2.to(".upper", 1, {
        x: 0,
        transformOrigin: "50% 100%",
        rotationX: 0,
        delay: 0,
        height: 200,
        ease: Circ.easeIn
      });
      tl2.to(".letter", 1, {
        x: 0,
        y: 0,
        rotationX: 0,
        scaleY: 0.5,
        delay: 0,
        ease: Expo.easeOut
      });
      tl2.to(".topfold", 0.6, {
        transformOrigin: "50% 0%",
        scaleY: 1,
        delay: 0,
        ease: Circ.easeIn
      });
      tl2.to(".wrapper", 0.7, {
        transformOrigin: "50% 0%",
        x: 5000,
        y: 0,
        delay: 0,
        ease: Circ.easeIn
      });
    });
  }
};
</script>

<style>
@charset "UTF-8";
.st0 {
  fill: #d1d0bf;
}
.st1 {
  fill: #e5e5da;
}
.likeBody {
  padding-top: 32vh;
  width: 100vw;
  height: 68vh;
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
  -webkit-justify-content: center;
  -ms-flex-pack: center;
  justify-content: center;
  -webkit-box-align: center;
  -webkit-align-items: center;
  -ms-flex-align: center;
  align-items: center;
  font-family: "Quicksand", sans-serif;
  color: #666;
}
.wrapper {
  width: 100%;
  max-width: 400px;
  height: auto;
  position: relative;
  margin-top: 20%;
  -webkit-perspective: 800px;
  perspective: 800px;
}
.wrapper .container {
  display: block;
  width: 100%;
  height: 218px;
  background: #c4c2a5;
  position: absolute;
  bottom: 5px;
  z-index: 0;
  border-radius: 10px;
}
.wrapper .container .topfold {
  width: 0;
  height: 0;
  position: relative;
  z-index: 2;
  margin-top: -2px;
  border-style: solid;
  border-width: 160px 200px 0 200px;
  border-color: #e7e7de transparent transparent transparent;
}
.wrapper .container .letter {
  position: absolute;
  width: calc(100% - 10px);
  height: 100px;
  bottom: 5px;
  left: 5px;
  z-index: 3;
  background: #faf5f3;
  border-top: 1px solid #faf5f3;
  box-shadow: 0px 10px 15px -5px rgba(0, 0, 0, 0.25);
  -webkit-transition: 0.2s ease-in-out;
  transition: 0.2s ease-in-out;
}
.wrapper .container .letter form {
  position: absolute;
  width: auto;
  bottom: 20px;
  left: 50%;
  -webkit-transform: translateX(-50%);
  transform: translateX(-50%);
  z-index: 1;
}
.wrapper .container .letter form input[type="text"] {
  font-size: 1.2em;
  padding: 5px;
  border: 0px solid;
  background: transparent;
  border-bottom: 2px solid #ce0010;
}
.wrapper .container .letter form textarea {
  font-size: 1.2em;
  padding: 5px;
  border: 0px solid;
  background: transparent;
  width: 100%;
  border-bottom: 2px solid #ce0010;
}
.wrapper .container .letter form textarea:focus {
  font-size: 1.2em;
  padding: 5px;
  border: 0px solid;
  background: transparent;
  width: 100%;
  border-bottom: 2px solid #0000ff;
}
.wrapper .container .letter form input[type="text"]:focus {
  -webkit-outline: none;
  outline: none;
  border-bottom: 2px solid #0000ff;
}
.wrapper .container .letter form .submitwrap {
  display: table;
  padding: 5px;
  margin: 15px auto 0px;
  background: #0000ff;
}
.wrapper .container .letter form .submitwrap:hover {
  background: -webkit-repeating-linear-gradient(
    45deg,
    #ce0010,
    #ce0010 5px,
    #ffffff 5px,
    #ffffff 10px,
    #0000ff 10px,
    #0000ff 15px,
    #ffffff 15px,
    #ffffff 15px
  );
  background: repeating-linear-gradient(
    45deg,
    #ce0010,
    #ce0010 5px,
    #ffffff 5px,
    #ffffff 10px,
    #0000ff 10px,
    #0000ff 15px,
    #ffffff 15px,
    #ffffff 15px
  );
  -webkit-animation: animatedBackground 40s linear infinite;
  animation: animatedBackground 40s linear infinite;
}
.wrapper .container .letter form .submitwrap:hover input {
  color: #ce0010;
}
@-webkit-keyframes animatedBackground {
  from {
    background-position: 0 0;
  }
  to {
    background-position: 500px 0;
  }
}
@keyframes animatedBackground {
  from {
    background-position: 0 0;
  }
  to {
    background-position: 500px 0;
  }
}
.wrapper .container .letter form input[type="submit"] {
  color: #0000ff;
  background: #fff;
  border: 0px solid;
  padding: 5px 10px;
  font-size: 1.2em;
  display: block;
  margin: 0px auto 0;
}
.wrapper .container .letter:before {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 5px;
  background: -webkit-repeating-linear-gradient(
    45deg,
    #ce0010,
    #ce0010 5px,
    #ffffff 5px,
    #ffffff 10px,
    #0000ff 10px,
    #0000ff 15px,
    #ffffff 15px,
    #ffffff 15px
  );
  background: repeating-linear-gradient(
    45deg,
    #ce0010,
    #ce0010 5px,
    #ffffff 5px,
    #ffffff 10px,
    #0000ff 10px,
    #0000ff 15px,
    #ffffff 15px,
    #ffffff 15px
  );
}
.wrapper .container .letter .upper {
  position: absolute;
  display: block;
  height: 100%;
  width: 100%;
  top: -100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  -webkit-transform-style: preserve-3d;
  transform-style: preserve-3d;
  left: 0;
  border-bottom: 1px solid #faf5f3;
  -webkit-backface-visibility: hidden;
  z-index: 2;
}
.wrapper .container .letter .upper .back {
  position: absolute;
  width: 100%;
  height: 100%;
  background: #f8f8f8;
  top: 100%;
  -webkit-transform-origin: 50% 0%;
  transform-origin: 50% 0%;
  -webkit-transform: rotateX(0deg);
  transform: rotateX(0deg);
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}
.wrapper .container .letter .upper .front {
  position: absolute;
  display: block;
  box-shadow: 0px 10px 50px rgba(0, 0, 0, 0.05),
    inset 0px -25px 50px -25px rgba(0, 0, 0, 0.16);
  background: #fff;
  width: 100%;
  height: 100%;
  top: 100%;
  -webkit-transform: rotateX(-180deg);
  transform: rotateX(-180deg);
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}
.wrapper .container .letter .upper .front:before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 5px;
  background: -webkit-repeating-linear-gradient(
    45deg,
    #ce0010,
    #ce0010 5px,
    #ffffff 5px,
    #ffffff 10px,
    #0000ff 10px,
    #0000ff 15px,
    #ffffff 15px,
    #ffffff 15px
  );
  background: repeating-linear-gradient(
    45deg,
    #ce0010,
    #ce0010 5px,
    #ffffff 5px,
    #ffffff 10px,
    #0000ff 10px,
    #0000ff 15px,
    #ffffff 15px,
    #ffffff 15px
  );
}
.wrapper .container .letter .upper h1 {
  color: #ce0010;
  font-family: head;
  padding: 0px 20px;
  margin-bottom: 0px;
  line-height: 1;
}
.wrapper .container .letter .upper p {
  padding: 35px 35px;
  margin-top: 0px;
  font-weight: 800;
  font-size: 1.2em;
}
.wrapper svg {
  max-width: 100%;
  position: relative;
  z-index: 0;
  bottom: 0;
  box-shadow: 0px 10px 20px -5px rgba(0, 0, 0, 0.25);
}
</style>
