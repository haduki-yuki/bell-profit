<template lang="pug">
  div
    div.btnGroup
      button(@click="localDataSave(); saveDateFlag()") 結果を保存する
      button(@click="localDataClear") 保存データを破棄
    transition(name="saveMove")
      div.saveTxt(v-if="saveFlag") 保存しました！
</template>

<script>
export default {
  name: 'StrageBtn',
  props: ['buy','sell','total'],
  data() {
    return {
      saveFlag: false
    }
  },
  methods: {
    localDataSave(){
      localStorage.setItem('buy',this.buy)
      localStorage.setItem('sell',this.sell)
      localStorage.setItem('total',this.total)
    },
    localDataClear(){
      localStorage.clear()
    },
    saveDateFlag (){
      this.saveFlag = true
      setTimeout(() => {
        this.saveFlag = false
      },3000)
    }
  },
}
</script>

<style lang="scss" scoped>
  .btnGroup {
    display: flex;
    justify-content: space-between;
    margin-top: 20px;
    button {
      display: inline-block;
      background-color: #8A7B66;
      appearance: none;
      outline: none;
      border: none;
      align-self: center;
      text-align: center;
      font-size: 16px;
      position: relative;
      color: #ffffff;
      padding: 10px;
      width: 150px;
      line-height: 1;
      border-radius: 7px;
      cursor: pointer;
    }
  }

  .saveTxt {
    text-align: center;
    margin-top: 15px;
    transform: translateX(0px);
  }

  .saveMove-enter-active,.saveMove-leave-active{
    transition: opacity 1s, transform 1s;
  }

  .saveMove-enter {
    opacity: 0;
    transform: translateX(-10px);
  }

  .saveMove-leave-to {
    opacity: 0;
    transform: translateX(10px);
  }



</style>