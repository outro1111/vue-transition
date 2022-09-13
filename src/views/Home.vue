<template>
  <div id="content">

    <!-- <div class="test">
      <button @click="show = !show">Toggle</button>
      <transition
        @before-enter="onBeforeEnter"
        @enter="onEnter"
        @before-leave="onBeforeLeave"
        @leave="onLeave"
        :css="false"
      >
        <p v-if="show">hello</p>
      </transition>
    </div> -->

    <div class="home">
      <div class="visual">
        <img :src="img.url" alt="">
      </div>
      <h1 class="title">
        The Progressive <br> JavaScript Framework <strong>WHY VUE.JS?</strong>
      </h1>
    </div>
    
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: false,
      img: {
        url: require('../assets/images/home1.jpg')
      }
    }
  },
  // methods: {
  //   onBeforeEnter(el) {
  //     el.style.transition = "opacity 2s ease"
  //     el.style.opacity = 0
  //     console.log('before enter', el);
  //   },
  //   onEnter(el, done) {
  //     setTimeout(()=>{
  //       el.style.opacity = 1
  //       console.log('enter', el);
  //     }, 0)
  //   },
  //   onBeforeLeave(el) {
  //     el.style.transition = "opacity 2s ease"
  //     el.style.opacity = 1
  //     console.log('before leave', el);
  //   },
  //   onLeave(el, done) {
  //     el.style.opacity = 0
  //     console.log('leave', el);
  //   }
  // }
}
</script>

<style scoped>
/* .test {text-align:center;padding:100px;}
.test button, .test p {line-height:2;font-size:50px} */

.home .title {position:absolute;top:38%;left:10%;font-size:min(3vw, 50px);font-weight:700}
.home .title strong {display:block;font-size:min(5vw, 60px);font-weight:800;background-image:var(--gradient-color1);background-clip:text;-webkit-text-fill-color:transparent;}
.home .visual {position:relative;mix-blend-mode:multiply;}
.home .visual img {float:right;width:55%;min-width:550px;}

.router-enter-from .home .visual {opacity:0;transform:translate3d(0px, 10em, 0px);filter:blur(4px);}
.router-enter-active .home .visual {transition:all 3s var(--ease2);}
.router-leave-to .home .visual {opacity:0;transform:translate3d(0px, -10em, 0px);filter:blur(4px);}
.router-leave-active .home .visual {transition:all 2s .5s var(--ease2);}

.router-enter-from .home .title {opacity:0;transform:translate3d(0px, 3em, 0px) skew(0deg, 8deg);filter:blur(4px);}
.router-enter-active .home .title {transition:all 3s var(--ease1);}
.router-leave-to .home .title {opacity:0;transform:translate3d(0px, -3em, 0px);filter:blur(4px);}
.router-leave-active .home .title {transition:all 2s .5s var(--ease1);}
</style>
