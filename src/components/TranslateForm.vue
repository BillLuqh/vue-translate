<template>
  <div class="row" id="translateForm">
    <div class="form-group row">
    <form class="form-inline" v-on:submit="formSubmit">
       <input class="form-control" type="text" placeholder="请输入要翻译的内容" v-model="textToTranslate">
       <select class="custom-select" v-model="language">
         <option value="en" selected>English</option>
         <option value="ru">Russian</option>
         <option value="ko">Korean</option>
         <option value="ja">Japanese</option>
       </select>
       <button type="submit" class="btn btn-primary">翻译</button>
     </form>
    </div>
  </div>
</template>

<script>


  export default {
    name: 'translateForm',
    data:function(){
      return{
        textToTranslate:"",
        language:""
      }
    },
    methods:{
      formSubmit:function (e) {
        // alert(this.textToTranslate)
        this.$emit("formSubmit",this.textToTranslate,this.language)
        e.preventDefault();
      }
    }
  }
</script>

<style>
  .form-inline{
    margin-left: 520px;
  }
  .form-control{
    width: 200px !important;
  }
  .custom-select{
    width: 150px;
  }
</style>
