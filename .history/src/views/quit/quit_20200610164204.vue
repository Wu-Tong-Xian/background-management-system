
    
<template>
 <div class="box">
  <div ><img src="../../assets/login3.jpg" alt="" class="bg-img"></div>
  <div class="login-box">
     <div class="textStyle">期待您的下次光临</div>
     
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
    left: 390px;
    margin: 0 auto;
    width: 500px;
    height: 300px;
    background: rgb(147, 202, 147);
    box-shadow: 0 0 10px rgb(174, 211, 170);
    opacity: 0.8;
  }
  .textStyle {
    font-size: 30px;
    border: 1px solid rgb(120, 172, 113);
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