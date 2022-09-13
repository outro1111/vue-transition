<template>
  <div class="backdrop"  @click.self="closeModal">
    <div class="modal">
      <button class="btn-close" @click="closeModal"><span>닫기</span></button>
      <span class="poster"><img :src="imgSrc" alt=""></span>
    </div>
  </div>
</template>

<script>
export default {
  props: ['imgSrc'],
  methods: {
    closeModal() {
      this.$emit('close')
    }
  }
}
</script>

<style scoped>
.modal {position:relative;width:300px;margin:250px auto;}
.modal .poster img {width:300px;border-radius:300px;transform: scale(.5, .5);}
.backdrop {position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.8);z-index:200}
.btn-close {position:absolute;right:-20px;top:-20px;display:block;width:70px;height:70px;padding:0;background:linear-gradient(-45deg, transparent 0%, transparent 47%, white 47%,  white 55%,transparent 55%, transparent 100%), linear-gradient(45deg, transparent 0%, transparent 47%, white 47%,  white 55%,transparent 55%, transparent 100%);border-radius:100%}
.btn-close span {display:none}
</style>