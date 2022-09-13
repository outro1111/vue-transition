<template>
  <transition
    @before-enter="modalBeforeEnter"
    @enter="modalEnter"
    @leave="modalLeave"
    :css="false"
  >
    <slot></slot>
  </transition>
</template>

<script>
import gsap from 'gsap'
export default {
  methods: {
    modalBeforeEnter(el) {
      gsap.set(el, {
        opacity: 0
      })
    },
    modalEnter(el, done) {
      gsap.to(el, {
        duration: 1,
        opacity: 1,
        ease: 'easeIn'
      })
      gsap.to(".poster img", {
        duration: 1,
        scaleX: 1.2,
        scaleY: 1.2,
        ease: 'easeIn'
      })
      gsap.to(".modal .btn-close", {
        duration: 1,
        x: 30,
        y: -30,
        ease: 'easeIn',
        onComplete: done
      })
    },
    modalLeave(el, done) {
      gsap.to(el, {
        duration: 0.7,
        delay: 0.3,
        opacity: 0
      })
      gsap.to(".poster img", {
        duration: 1,
        scaleX: .5,
        scaleY: .5,
        ease: 'easeIn'
      })
      gsap.to(".modal .btn-close", {
        duration: 1,
        x: 0,
        y: 0,
        ease: 'easeIn',
        onComplete: done
      })
    }
  }
}
</script>

<style scoped>

</style>