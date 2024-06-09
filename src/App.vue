<template>
  <h1>CRYPTO</h1>
  <Input :changeAmount="changeAmount" :convert="convert"/>
  <p className="error" v-if="error != ''"> {{ error }}</p>
  <div className="selectors">
    <Selector :setCrypto="setCryptoFirst"  />
    <Selector :setCrypto="setCryptoSecond" />
  </div>

</template>

<script>
import Input from './components/Input.vue'
import Selector from './components/Selector.vue'

export default{
  components: { Input, Selector },
  data(){
    return{
      amount: 0,
      cryptoFirst: '',
      cryptoSecond: '',
      error: ''
    }
  },
  methods:{
    changeAmount(val){
      this.amount = val
    },
    setCryptoFirst(val){
      this.cryptoFirst = val
    },
    
    setCryptoSecond(val){
      this.cryptoSecond = val
    },
    convert(){
      if(this.amount <= 0 ){
        this.error = 'Введите число больше нуля'
        return
      }
      else if(this.cryptoFirst == '' || this.cryptoSecond == ''){
        this.error = 'Выберите валюту'
        return
      }
      else if(this.cryptoFirst == this.cryptoSecond){
        this.error = 'Выберите другую валюту'
        return
      }

      this.error = ''
    }
  }
}
</script>

<style scoped>
.selectors{
  display: flex;
  justify-content: space-around;
  width: 700px;
  margin: 0 auto;
}
.error{
  color: #f67070;

}
</style>
