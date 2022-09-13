<template>
  <header :class="{ active: navOpen }">
    <h1 class="logo"><router-link to="/" @click="this.navOpen = false">HOME</router-link></h1>
    <button class="btn_nav" @click="toggleNav">
      <span></span>
      <strong>{{ navOpen ? 'CLOSE' : 'MENU' }}</strong>
    </button>
  </header>
  <transition name="nav">
    <nav id="nav" v-show="navOpen">
      <div class="nav_dim"></div>
      <transition-group tag="ul" name="list">
        <li v-for="(navMenu, index) in navMenus" :key="navMenu" v-show="navOpen" :style="{ '--index': index }">
          <router-link class="nav_link" :to="navMenu.url" @click="toggleNav">{{ navMenu.title }}</router-link>
        </li>
      </transition-group>
    </nav>
  </transition>
</template>

<script>
export default {
  data() {
    return {
      navMenus: [
        {title: 'Home', url: '/'},
        {title: 'About', url: '/About'},
        {title: 'Works', url: '/Works'},
        {title: 'Memo', url: '/Memo'}
      ],
      navOpen: false
    }
  },
  methods: {
    toggleNav() {
      this.navOpen = !this.navOpen
    }
  }
}
</script>

<style scoped>
header {position:fixed;top:0;left:0;width:100%;mix-blend-mode:difference;z-index:100;}
h1.logo {position:absolute;top:85px;left:-72px;transform:rotate(90deg) translateY(0);transition:transform 1s;}
h1.logo a {font-size:60px;font-family:'El Messiri', sans-serif;font-weight:500;color:#fff}
.btn_nav {position:absolute;top:4vw;right:3vw;display:inline-block;width:36px;height:44px;text-align:center}
.btn_nav span, .btn_nav span:before, .btn_nav span:after {position:relative;top:0;display:block;width:100%;height:2px;background:#fff;transition:transform .3s var(--ease1)}
.btn_nav span:before, .btn_nav span:after {content:"";position:absolute;left:0}
.btn_nav span:before {top:-8px}
.btn_nav span:after {top:8px}
.btn_nav strong {position:relative;top:.5vw;display:block;font-size:12px;font-weight:200;color:#fff;margin-top:7px;}
header.active h1.logo {transform:rotate(90deg) translateX(20%)}
header.active .btn_nav span {transform:rotate3d(0,0,1,-45deg);}
header.active .btn_nav span:before {top:0;transform:rotate3d(0,0,1,90deg);}
header.active .btn_nav span:after {top:0;transform:rotate3d(0,0,1,90deg);opacity:0}

#nav {position:fixed;top:0;right:0;bottom:0;left:0;z-index:90}
#nav .nav_dim {position:absolute;top:0;right:0;bottom:0;left:0;background:#20063c;opacity:.88;transform-origin:0% 0%;}
#nav ul {position:absolute;top:50%;left:50%;transform:translate(-50%, -50%)}
#nav li {overflow:hidden;text-align:center}
#nav li a {display:inline-block;font-size:min(8vw, 100px);font-weight:200;color:#fff;}
#nav li a:hover {letter-spacing:.2rem;}
#nav li a.router-link-active {font-weight:400;background-image:var(--gradient-color1);background-clip:text;-webkit-text-fill-color:transparent;}

.nav-enter-active, .nav-leave-active {transition:transform .8s}
.nav-enter-from .nav_dim {transform:scaleY(0)}
.nav-enter-to .nav_dim {transform:scaleY(1)}
.nav-enter-active .nav_dim {transition:transform .6s var(--ease3)}
.nav-leave-from .nav_dim {transform:scaleY(1)}
.nav-leave-to .nav_dim {transform:scaleY(0)}
.nav-leave-active .nav_dim {transition:transform .6s var(--ease3);transition-delay:.2s;}

.list-enter-active, .list-leave-active {transition:transform 1.5s}
.list-enter-from .nav_link {transform:translateY(-90%);opacity:0}
.list-enter-to .nav_link {transform:translateY(0%);opacity:1}
.nav_link {transition:transform 1.5s calc(.12s * var(--index)) ease, opacity 1.5s calc(.12s * var(--index)) ease, letter-spacing .3s ease;}
.list-leave-from .nav_link {transform:translateY(0%);opacity:1}
.list-leave-to .nav_link {transform:translateY(-90%);opacity:0}
.list-leave-active .nav_link {transition:transform 1.2s ease, opacity 1.2s ease, letter-spacing .3s ease;}
</style>