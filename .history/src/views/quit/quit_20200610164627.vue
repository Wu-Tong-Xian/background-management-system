
    
<template>
 <div class="box">
  <div ><img src="../../assets/login3.jpg" alt="" class="bg-img"></div>
  <div class="login-box">
     <div class="textStyle">期待您的下次光临</div>
     <el-row><el-button type="warning">确定退出</el-button></el-row>
  </div>
  
</div>
</template>

<script>
 export default {
   name: '',
   props: {
   },
   components: {

   },
   data () {
 
     return {
       
     
     }
   },
   methods: {
   
   },
   mounted() {

   },
   watch: {

   },
   computed: {

   }
 }
</script>

<style scoped lang='scss'>
  .login-box {
    position: absolute;
    top:180px;
    left: 420px;
    margin: 0 auto;
    width: 400px;
    height: 300px;
    background: rgb(147, 202, 147);
    box-shadow: 0 0 10px rgb(204, 216, 203);
    opacity: 0.5;
  }
  .textStyle {
    font-size: 30px;
    border: 1px solid rgb(180, 197, 178);
    text-align: center;
  }

  .box {
    width: 100%;
    height: 100%;
    position: relative;
  }
  .bg-img {
     width: 100%;
     height: 710px;
  }
  .loginbox {
    margin-left: 160px;
  }
</style>