<template>
 <div >

    <div class="fl j-between">
      <div class="content fl">
        <img src="../../assets/人头像02.png" alt="" class="img ">
        <div class="mg-t20">
          <div>New visits</div>
          <div> {{obj.visits}}</div>
        </div>
      </div>

      <div class="content fl">
        <img src="../../assets/信息.png" alt="" class="img">
        <div class="mg-t20">
          <div>messages</div>
          <div >{{obj.messages}}</div>
        </div>
      </div>
     
      <div class="content fl ">
        <img src="../../assets/钱.png" alt="" class="img">
        <div class="mg-t20">
          <div>purchases</div>
          <div>{{obj.purchases}}</div>
        </div>
      </div>
      <div class="content fl">
        <img src="../../assets/购物车.png" alt="" class="img">
        <div class="mg-t20">
          <div>shopping</div>
          <div> {{obj.shopping}}</div>
        </div>
      </div>
    </div>
    <!-- 曲线图 -->
    <div>
      <ve-line :data="chartData1" ></ve-line>
    </div>
    <!-- 雷达图 -->
    <div>
      <ve-line :data="chartData2" ></ve-line>
    </div>
 </div>
</template>

<script>
import axios from 'axios'
 export default {
   name: '',
   props: {
   },
   components: {

   },
   data () {
     return {
       obj:{},
      //  上面是计数器定义的4个数据
      // 曲线图
       chartData1: {
        //  columns 第一个数据时在下面的日期  后两个时显示在上面也是途中的数据信息 都是数据拿到的所以要跟rows里的数据名一样
          columns: ["date", "expected", "actual"],
          rows: [         ]
        },
        // 雷达图
        chartData2: {
        //  columns 第一个数据时下面的日期   后两个时显示
          columns: ["Allocated Budget", "expected", "actual"],
          rows: [         ]
        }
     }
   },
   methods: {
    //  计数器: /homeData (get请求)
     gethomeData(){
       axios.get('/api/homeData').then(res =>{
        //  console.log(res.data);
         this.obj =res.data.data
       }).catch(err =>{
         console.log(err);
       })
     },
    //  - 折线图: /homeChat (get请求)
    gethomeChat(){
      axios.get('/api/homeChat').then(res =>{
        // console.log(res.data.data);
         this.chartData1.rows = res.data.data
      }).catch(err =>{
        console.log(err);
      })
    },
     //  - 雷达图: /radarChat (get请求)
    getradarChat(){
      axios.get('/api/radarChat').then(res =>{
        console.log(res.data.data);
         this.chartData2.rows = res.data.data
      }).catch(err =>{
        console.log(err);
      })
    }
     
   },
   mounted() {
     this.gethomeData()  //计数器
     this.gethomeChat()  //折线图
     this.getradarChat() //雷达图
   },
   watch: {

   },
   computed: {

   }
 }
</script>

<style scoped lang='scss'>
   .img {
     width: 40px;
     height: 40px;
     margin-top: 20px;
   }
   .content {
     width: 22%;
     height: 80px;
     background: rgb(160, 147, 147);
     justify-content: space-around;
     margin: 40px 20px 40px 20px;
   }
</style>