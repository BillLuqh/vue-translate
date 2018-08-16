<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h6 class="text-muted">简单 / 易用 / 便捷</h6>
    <TranslateForm v-on:formSubmit="translateTxt"></TranslateForm>
    <TransLateOutput v-text="translatedText"></TransLateOutput>
  </div>
</template>

<script>
import TranslateForm from "./components/TranslateForm"
import TransLateOutput from "./components/TranslateOutput"

export default {
  name: 'App',
  data:function(){
    return{
      translatedText:""
    }
  },
  components: {
    TranslateForm,TransLateOutput
  },
  methods:{
    translateTxt:function (txt,language) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?' +
        'key=trnsl.1.1.20180816T073342Z.2fb0660ddf660324.a0ed5938d10fad09755da8025cac892aa623a7a0' +
        '&lang='+language+'&text='+txt).then((response)=>{
          // console.log(response.body.text[0])
        this.translatedText = response.body.text[0]
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
