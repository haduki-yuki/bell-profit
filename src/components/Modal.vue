<template lang="pug">
  transition(name="modal")
    div
      div.modalOverlay
        span.modalCloseBtn
        div.modalContents
          div.useHead 使い方
          ul.howToUse
            li 買値・売値・購入数の3つを入力すると、購入結果に自動で計算結果が出力されます。購入結果がマイナスになると、損益が赤く表示されます。
            li 【結果を保存する】のボタンを押すと、ブラウザに買値・売値・購入数の入力値が保存され、次回アクセス時に自動で挿入されます。
            li 【保存データを破棄】を押すとブラウザに保存されたデータは破棄されます。入力結果はそのまま残りますので、日曜日のタイミングなどに使うといいかもです。
          p 開発の要望などは<a href="https://twitter.com/peridot_snow08" target="_blank">葉月ゆき</a>のTwitterにてお寄せください。
          button(@click="modalClose") ヘルプを閉じる
</template>

<script>
export default {
  name:'Modal',
  methods: {
    modalClose(){
      this.$emit('modalClose')
    }
  },
}


</script>

<style lang="scss">
  .modalOverlay {
    position: fixed;
    width: 100vw;
    height: 100vh;
    background: #ffffff;
    top: 0;
    left: 0;
    .modalContents {
      max-width: 1000px;
      margin: 30px auto 0;
      padding: 0 10px;
      .useHead {
        text-align: center;
        font-size: 24px;
      }
      button {
        display: block;
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
        margin: 0 auto;
      }
    }
  }

  .modal-enter-active,.modal-leave-active{
    transition: opacity 1s;
  }
  .modal-enter,
  .modal-leave-to {
    opacity: 0;
  }
</style>