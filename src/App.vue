<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单  /  易用 /  便捷</h5>
      <translateForm v-on:formSubmit="translateText"></translateForm>
       <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'App',
  data:function(){
    return{
      translatedText:""
    }
  },
  components:{
    TranslateForm,
    TranslateOutput
 },
  methods:{
    translateText:function(text,language){
      this.$http.get("https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180404T093626Z.18e1952b2c188968.6c5454559f60471fc28c435ea3903b02cfe81308&lang="+language+"&text="+text)
      .then((response)=>{
        this.translatedText=response.body.text[0];
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
