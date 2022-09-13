<template>
  <div id="content">
    <div class="works">
      <h2 class="title">
          <span>Works</span>
      </h2>
      <ul class="list">
        <li v-for="(img, index) in imgs" :key="img" :style="{ '--index': index }">
          <a href="#link"><img :src="img.url" alt="" @click="openModal"></a>
        </li>
      </ul>

      <modalTransition>
        <div class="modalbox" v-if="showModal">
          <Modal :imgSrc="imgSrc" @close="closeModal" />
        </div>
      </modalTransition>

      <div class="text">
        <span>Since swup removes the page reloads from site, it also removes a standard lifecycle of scripts. By default, scripts get enabled when the page is loaded. Often we would find ourselves waiting for whole page to load before executing the script.</span>
      </div>

    </div>
  </div>
</template>

<script>
import modalTransition from '../components/modalTransition.vue'
import Modal from '../components/Modal.vue'
export default {
  components: {Modal, modalTransition},
  data() {
    return {
      imgs: [
        {url: require('../assets/images/album1.jpg')},
        {url: require('../assets/images/album2.jpg')},
        {url: require('../assets/images/album3.jpg')},
        {url: require('../assets/images/album4.jpg')},
        {url: require('../assets/images/album5.jpg')},
        {url: require('../assets/images/album6.jpg')},
        {url: require('../assets/images/album7.jpg')},
        {url: require('../assets/images/album8.jpg')}
      ],
      showModal: false,
      imgSrc: ''
    }
  },
  methods: {
    openModal(event) {
      this.showModal = true
      this.imgSrc = event.target.src
    },
    closeModal() {
      this.showModal = false
    }
  }
}
</script>

<style scoped>
.works {width:880px;margin:0 auto 80px}
.works .title {overflow:hidden;padding-top:4em;}
.works .title span {display:block;font-size:min(4vw, 50px);font-weight:700;}
.works .list:after {content:'';clear:both;display:block;}
.works .list li {float:left;width:25%;padding:20px;min-height:224px}
.works .list {font-size:20px;padding:1em 0}
.works .text {overflow:hidden}
.works .text span {display:block}
.works .modalbox {position:relative;z-index:100}

.router-enter-from .works .title span {opacity:0;transform:translateY(100%);}
.router-enter-active .works .title span {transition:all 3s var(--ease2);}
.router-leave-to .works .title span {opacity:0;transform:translateY(100%);}
.router-leave-active .works .title span {transition:all 3s .5s var(--ease2);}

.router-enter-from .works li {opacity:0;transform:translateY(30%);filter:blur(4px);}
.router-enter-active .works li {transition:all 1s ease;transition-delay:calc(.1s * var(--index));}
.router-leave-to .works li {opacity:0;transform:scale(.7);filter:blur(4px);}
.router-leave-active .works li {transition:all 1s .5s ease;}

.router-enter-from .works .text span {opacity:0;transform:translateY(100%);}
.router-enter-active .works .text span {transition:all 3s .5s var(--ease2);}
.router-leave-to .works .text span {opacity:0;transform:translateY(100%);}
.router-leave-active .works .text span {transition:all 3s .5s var(--ease2);}
</style>