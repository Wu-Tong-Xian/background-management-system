<template>
 <div class="layout">
    <div>
      <el-row class="fl j-around">
     <div> <el-button type="danger" size="mini" @click="published">返回</el-button></div>  
        <div><el-button type="primary" size="mini" @click="submitForm(ruleForm)">发布</el-button></div>
      </el-row>
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
       edit:[]
     }
   },
   methods: {
     published(){
       this.$router.push(go(-1))
     }
   },
   mounted() {
    this.edit = this.$route.query.edit
    console.log(this.edit);
   },
   watch: {

   },
   computed: {

   }
 }
</script>

<style scoped lang='scss'>

</style>