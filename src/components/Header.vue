<template lang="pug">
  div
    header
      button(@click="openHelp").helpBtn ヘルプ
      
</template>

<script>
export default {
  name: 'Header',
  methods: {
    openHelp(){
      this.$emit('modalOpen')
    }
  },
}
</script>

<style lang="scss" scoped>
  header {
    background: #51B9A1;
    display: flex;
    justify-content: flex-end;
    position: relative;
    padding-top: 15px;
    padding-bottom: 7px;
    &::before {
      position: absolute;
      content: '';
      width: 100%;
      height: 15px;
      background:url('../assets/img/wave.svg');
      bottom: -10px;
      left: 0;
    }
    .helpBtn {
      align-self: center;
      text-align: right;
      position: relative;
      color: #ffffff;
      font-size: 13px;
      padding: 0 15px 0 20px;
      line-height: 1;
      display: inline-block;
      background-color: transparent;
      appearance: none;
      outline: none;
      border: none;
      cursor: pointer;
      &::before {
        position: absolute;
        content: '';
        width: 14px;
        height: 14px;
        top: 0;
        bottom: 0;
        left: 0;
        background: url('../assets/img/hatena.svg') no-repeat;
        background-size: contain;
      }
    }
  }
</style>
