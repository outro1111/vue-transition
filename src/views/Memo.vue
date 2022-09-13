<template>
  <div id="content">
    <div class="memos">
      <transition name="alert">
        <div class="alert" v-if="showAlert">You must enter a value for the Memo</div>
      </transition>
      <input type="text" placeholder="Add a new memo" v-model="memoInput" @keypress.enter="addMemo">
      <transition name="switch" mode="out-in">
        <div v-if="memos.length">
          <transition-group tag="ul" name="memo" appear>
            <li v-for="(memo, index) in memos" :key="memo" @click="deleteMemo(index)">
              {{ memo.text }}
            </li>
          </transition-group>
        </div>
        <div v-else class="nodata">Woohoo, nothing left memo!</div>
      </transition>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      memoInput: "",
      showAlert: false,
      memos: [
        { text: 'first memo'},
        { text: 'second memo'}
      ]
    }
  },
  methods: {
    addMemo() {
      if(this.memoInput) {
        this.memos.push({ text: this.memoInput })
        this.memoInput = ""
      } else {
        this.showAlert = true
        setTimeout(() => this.showAlert = false, 3000)
      }
    },
    deleteMemo(index) {
      this.memos.splice(index, 1)
    }
  }
}
</script>

<style scoped>
.memos {position:relative;max-width:600px;margin:0 auto 80px;padding-top:110px}
.memos input {width:100%;padding:12px 22px;border:1px solid #d0c5b9;border-radius:50px;box-sizing:border-box;margin-bottom:20px;}
.memos ul {position:relative;padding:0;}
.memos li {display:block;width:100%;margin-bottom:10px;padding:10px 22px;text-align:center;background:white;box-shadow:1px 3px 5px rgba(0,0,0,0.1);border-radius:50px;box-sizing:border-box;}
.memos li:hover {cursor:pointer;}
.memos .nodata {text-align:center;padding:10px 0;}
.memos .alert {position:absolute;width:100%;top:20px;margin:0 auto;padding:20px;text-align:center;color:#fff;background:#ff0062;border-radius:20px;box-shadow:1px 3px 5px rgba(0,0,0,.2)}

.router-enter-from .memos {opacity:0;transform:translateY(50%);}
.router-enter-active .memos {transition:all 3s var(--ease2);}
.router-leave-to .memos {opacity:0;transform:translateY(-50%);}
.router-leave-active .memos {transition:all 2s .6s var(--ease2);}

.memo-enter-from {opacity:0;transform:scale(0.6);}
.memo-enter-active {transition:all .5s ease;}
.memo-leave-to {opacity:0;transform:scale(0.6);}
.memo-leave-active {transition:all .5s ease;position:absolute}
.memo-move {transition:all .5s ease;}

.alert-enter-active {animation:wobble .8s ease}
.alert-leave-to {opacity:0;transform:translateY(-60px);}
.alert-leave-active {transition:all .5s ease;}
@keyframes wobble {
  0% {opacity:0;transform:translateY(-100px);}
  50% {opacity:1;transform:translateY(0px);}
  60% {opacity:1;transform:translateX(8px);}
  70% {opacity:1;transform:translateX(-8px);}
  80% {opacity:1;transform:translateX(4px);}
  90% {opacity:1;transform:translateX(-4px);}
  100% {opacity:1;transform:translateX(0px);}
}

.switch-enter-from, .switch-leave-to {opacity:0;transform:translateY(-20px);}
.switch-enter-active, .switch-leave-active {transition:all .5s ease;}
</style>