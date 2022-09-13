<template>
  <div id="content">
    <div class="about">
        <h2 class="title"><span>About Transition</span></h2>
        <div class="text"><span>Since swup removes the page reloads from site, it also removes a standard lifecycle of scripts. By default, scripts get enabled when the page is loaded. Often we would find ourselves waiting for whole page to load before executing the script.</span></div>
        <div class="visual"><img :src="img.url" alt=""></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      img: {
        url: require('../assets/images/img1.png')
      }
    }
  },
}
</script>

<style scoped>
.about {position:relative;overflow:hidden}
.about .title {position:relative;width:55%;height:260px;margin-top:15%;overflow:hidden;mix-blend-mode: multiply;background:var(--gradient-color2)}
.about .title span {position:absolute;bottom:-26px;right:-8px;width:500px;text-align:right;line-height:0.9;font-size:115px;color:#fff;font-family:'El Messiri', sans-serif}
.about .text {position:relative;width:55%;margin:2% 0 6%;padding-left:12%;overflow:hidden}
.about .text span {display:block;text-align:right;line-height:1.5}
.about .visual {position:absolute;top:0;right:0;width:45%;padding-left:5%;margin-top:15%;}

.router-enter-from .about .title {opacity:0;transform:translateX(-100%);filter:blur(4px);}
.router-enter-to .about .title {opacity:1;transform:translateX(0);filter:blur(0);}
.router-enter-active .about .title {transition:all 3s var(--ease2);}
.router-leave-from .about .title {opacity:1;transform:translateX(0);filter:blur(0);}
.router-leave-to .about .title {opacity:0;transform:translateX(-100%);}
.router-leave-active .about .title {transition:all 1.5s 1s var(--ease2);}

.router-enter-from .about .title span {transform:translateY(100%)}
.router-enter-to .about .title span {transform:translateY(0)}
.router-enter-active .about .title span {transition:transform 3s .8s var(--ease2);}
.router-leave-from .about .title span {transform:translateY(0)}
.router-leave-to .about .title span {transform:translateY(100%)}
.router-leave-active .about .title span {transition:transform 2.2s .6s var(--ease2);}

.router-enter-from .about .text span {opacity:0;transform:translateY(-100%);filter:blur(4px);}
.router-enter-to .about .text span {opacity:1;transform:translateY(0);filter:blur(0);}
.router-enter-active .about .text span {transition:all 3s 1s var(--ease2);}
.router-leave-from .about .text span {opacity:1;transform:translateY(0);filter:blur(0);}
.router-leave-to .about .text span {opacity:0;transform:translateY(-100%);}
.router-leave-active .about .text span {transition:all 1.4s .6s var(--ease2);}

.router-enter-from .about .visual {opacity:0;transform:perspective(20em) rotateY(-60deg) translateX(100%);filter:blur(4px);}
.router-enter-to .about .visual {opacity:1;transform:perspective(20em) rotateY(0) translateX(0);filter:blur(0);}
.router-enter-active .about .visual {transition:all 3s var(--ease2);}
.router-leave-from .about .visual {opacity:1;transform:perspective(20em) rotateY(0) translateX(0);filter:blur(0);}
.router-leave-to .about .visual {opacity:0;transform:perspective(20em) rotateY(-30deg) translateX(100%);filter:blur(4px);}
.router-leave-active .about .visual {transition:all 3s 1s var(--ease2);}
</style>