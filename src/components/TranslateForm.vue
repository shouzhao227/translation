<template>
  <div class="row" id="translateForm">
    <div class="col-md-6 col-md-offset-3">
      <form id="tran" class="well form-inline" v-on:submit="formSubmit">

        <input class="form-control" type="text" v-model="textToTranslate" placeholder="输入需要翻译的内容" />
        <select class="form-control" v-model="language">
          <option value="en">English</option>
          <option value="ru">Russian</option>
          <option value="ko">Korean</option>
          <option value="ja">Japanese</option>
        </select>
        <input class="btn btn-primary" type="submit" value="翻译">

      </form>

    </div>

  </div>
</template>

<script>

export default {
  name: 'translateForm',
  data:function(){
    return {
      textToTranslate:"",
      language:""
    }
  },
  methods: {
    formSubmit:function(e){
      this.$emit("formSubmit",this.textToTranslate,this.language);
      e.preventDefault();
    }
  },
  created:function(){
    this.language="en";
  }
}
</script>

<style>
#tran{
  border:1px solid #ccc;
  border-radius: 10px
}
</style>
