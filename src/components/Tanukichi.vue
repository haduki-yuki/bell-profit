<template lang="pug">
  div.tanukichi
    p.name たぬきち
    vue-typer(
      :text="tanukichiTalk"
      :repeat='0'
    )
</template>

<script>
/* eslint no-irregular-whitespace: ["error", {"skipTemplates": true}] */
import { VueTyper } from 'vue-typer'
export default {
  name: 'Tanukichi',
  components: {
    VueTyper
  },
  props: {
    kabuTotal: {
      type: Number
    }
  },
  data() {
    return {
      tanukichiTalk:`数値を入力をしてだなも。\n3つの数字をいれると、自動的に金額がでるだなも！`
    }
  },
  watch: {
    kabuTotal(newTotal){
      if(newTotal > 0){
        this.tanukichiTalk = `今 カブを売ると儲けでるだなも！\n売り値が上がるともっと儲けることができるから、もう少し待ってみるだなも。`
      } else if( newTotal < 0) {
        this.tanukichiTalk = `あわわわ！ 損がでちゃただなも！\n明日になったらカブ価が回復するかも…\n今は売らずに待つのがよいだなも！`
      } else {
        this.tanukichiTalk = `プラスマイナス０だなも。\n損をしなくて済むから今売るといいだなも！`
      }
    }
  },
}
</script>

<style lang="scss" scoped>
  .tanukichi {
    position: relative;
    margin-top: 20px;
    padding-top: 30px;
    .name {
      padding: 5px 20px;
      text-align: center;
      background: #df852d;
      color: #4b2323;
      border-radius: 15px;
      font-weight: bold;
      display: inline-block;
      position: relative;
      transform: rotate(-5deg);
      position: absolute;
      top: -22px;
      left: -11px;
    }
  }

  .vue-typer {
    margin-top: -10px;
    display: block;
    padding: 15px 20px 5px;
    border-radius: 8px;
    min-height: 90px;
    line-height: 1.4;
    background: #fff;
    .custom.char.typed {
      color: #333;
    }

    .custom.caret {
      display: none;
    }
  }

</style>