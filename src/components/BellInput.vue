<template lang="pug">
  div.bellInput
    div.trade
      .buyKabu.kabuPrice
        label(for='buyBell') 買値
        div.kabuPriceInput
          input#buyBell(type='number', v-model.number='buyPrice' placeholder="100")
          span ベル
      .sellKabu.kabuPrice
        label(for='sellBell') 売値
        div.kabuPriceInput
          input#sellBell(type='number', v-model.number='sellPrice' placeholder="100")
          span ベル
    .kabuNumber 
      label(for='kabuNumber') 購入数
      .kabuPriceInput
        input#kabuNumber(type='number', v-model.number='kabuNumber' placeholder="100")
        span カブ
    h2.result 購入結果
    table
      tr
        td.first 購入合計
        td 
          span.priceTxt {{buyTotal | numberGrouping}}
          span ベル
      tr
        td.first 買取合計
        td 
          span.priceTxt {{sellTotal | numberGrouping}}
          span ベル
      tr.borderNone
        td.first カブ損益
        td 
          span(:class="{active : kabuTotal < 0}").priceTxt {{kabuTotal | numberGrouping}}
          span ベル
    Tanukichi(:kabuTotal="kabuTotal")
    StrageBtn(:buy="buyPrice" :sell="sellPrice" :total="kabuNumber")
</template>

<script>
import Tanukichi from './Tanukichi.vue'
import StrageBtn from './StrageBtn.vue'
export default {
  name: 'BellInput',
  components: {
    Tanukichi,
    StrageBtn
  },
  data(){
    return {
       buyPrice: '',
       sellPrice: '',
       kabuNumber:'',
    }
  },
  mounted() {
    if(localStorage.length > 0) {
      this.buyPrice = localStorage.getItem('buy')
      this.sellPrice = localStorage.getItem('sell')
      this.kabuNumber = localStorage.getItem('total')
    }
  },

  computed: {
    buyTotal(){
      return this.buyPrice * this.kabuNumber
    },
    sellTotal(){
      return this.sellPrice * this.kabuNumber
    },
    kabuTotal(){
      return this.sellTotal - this.buyTotal
    },
  },
  filters: {
    numberGrouping(price){
      return price = price.toLocaleString()
    }
  }

}
</script>

<style lang="scss" scoped>
  .bellInput {
    padding-left: 15px;
    padding-right: 15px;
    margin-top: 30px;
  }

  .trade {
    display: flex;
    justify-content: space-between;

    .kabuPrice {
      width: 49%;
      label { 
        display: block;
        font-size: 18px;
      }
      .kabuPriceInput {
        display: flex;
        justify-content: space-between;
        input {
          width: calc(100% - 3em);
          padding: 8px;
          border-radius: 3px;
          border: 2px solid #ccc;
          font-size: 18px;
        }
        span {
          font-size: 18px;
          display: inline-block;
          text-align: right;
          align-self: center;
        }
      }
    }
  }

  .kabuNumber {
    margin-top: 10px;

    label { 
      display: block;
      font-size: 18px;
    }

    .kabuPriceInput {
      display: flex;
      justify-content: space-between;
      input {
       width: calc(100% - 3em);
        padding: 8px;
        border-radius: 3px;
        border: 2px solid #ccc; 
        font-size: 18px;
      }
      span {
        font-size: 18px;
        display: inline-block;
        text-align: right;
        align-self: center;
      }
    }

  }

  .result {
    font-size: 28px;
    background: #51B9A1;
    position: relative;
    text-align: center;
    padding: 10px 15px;
    margin-right: 15px;
    margin-left: 15px;
    line-height: 1;
    letter-spacing: 2px;
    color: #FBFBD5;
    border-radius: 30px;
    &::before {
      position: absolute;
      content: '';
      bottom: -15px;
      left: 50%;
      transform: translateX(-50%);
      width: 0;
      height: 0;
      border-style: solid;
      border-width: 15px 10px 0 10px;
      border-color: #51b9a1 transparent transparent transparent;
      line-height: 0px;
    }
  }

  table {
    background: #fff;
    width: calc(100% - 30px);
    margin-left:15px;
    margin-right: 15px;
    border-radius: 7px;
    border: 2px solid #707070;
    border-spacing: 0;
    td {
      padding: 5px 15px;
      border-bottom: 2px solid #707070;
      font-size: 16px;
      .priceTxt {
        font-size: 22px;
        display: inline-block;
        width: 5em;
        padding-right: 1em;
        text-align: center;
        &.active {
          color: #FF1A1A;
        }
      }
    }
    .first {
      width: 40%;
      border-right: 2px solid #707070;
      text-align: center;
    }
    .borderNone td{
      border-bottom: none;
    }
  }
</style>