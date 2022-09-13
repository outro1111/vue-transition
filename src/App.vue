<template>
  <Nav />
  <!-- <router-view /> -->
  <router-view v-slot="{ Component }">
    <transition name="router" mode="out-in" :duration="{ enter:3000, leave:1500 }">
      <component :is="Component"></component>
    </transition>
  </router-view>
</template>

<script>
import Nav from './components/Nav.vue'
export default {
  components: { Nav }
}
</script>

<style scoped>
/* .router-enter-from  {opacity:0;transform:translateY(3em)}
.router-enter-to {opacity:1;transform:translateY(0)}
.router-enter-active {transition:all 3s var(--ease1);}
.router-leave-from  {opacity:1;transform:translateY(0)}
.router-leave-to {opacity:0;transform:translateY(-5em)}
.router-leave-active {transition:all 1.5s .5s var(--ease1);} */
</style>