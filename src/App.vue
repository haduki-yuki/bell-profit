<template lang="pug">
  div#app
    Header(@modalOpen = 'toggleModalFlag')
    BellInput
    Modal(v-if="modalFlag" @modalClose = 'toggleModalFlag')
</template>

<script>
import Header from './components/Header.vue'
import BellInput from './components/BellInput.vue'
import Modal from './components/Modal.vue'
export default {
  name: 'App',
  components: {
    Header,
    BellInput,
    Modal
  },
  data(){
    return {
      modalFlag: false
    }
  },
  methods: {
    toggleModalFlag(){
      this.modalFlag = !this.modalFlag
    }
  },
}
</script>

<style>
  * {
    box-sizing: border-box;
  }
  body {
    margin: 0;
    padding: 0;
    background: #F5F3DC;
    color: #333333;
    font-family: 'Noto Sans JP', sans-serif;
  }

  #app {
    max-width: 1000px;
    margin: 0 auto;
  }

  /* numberの矢印を消去 */
  input[type=number]::-webkit-inner-spin-button,
  input[type=number]::-webkit-outer-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }

  input[type="number"] { 
    -moz-appearance:textfield; 
  } 
</style>
