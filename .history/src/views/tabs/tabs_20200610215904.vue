<template>
 <div>
  <el-badge :value="3" class="item" type="primary">
    <el-button size="small">未读</el-button>
  </el-badge>
  <el-badge :value="1" class="item" type="warning">
    <el-button size="small">已读</el-button>
  </el-badge>
  <el-badge :value="2" class="item" type="warning">
    <el-button size="small">回收站</el-button>
  </el-badge>
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
  .item {
  margin-top: 10px;
  margin-right: 40px;
}
</style>