<template>
  <div>
    <!-- 本页面为公共页面只写有头部和侧边栏部分 -->
    <!-- 头部开始 -->
    <div class="head">
      <div>欢迎来到Panda后台管理系统</div>
      <div>亲爱的{{name}}, 本次登录时间为{{time}}</div>
    </div>
    <!-- 侧边栏开始 -->
    <div class="box">
      <div class="box-left">
        <el-row class="tac">
          <el-col>
            <el-menu
              :default-active="$route.path"
              class="el-menu-vertical-demo"
              background-color="#545c64"
              text-color="#fff"
              active-text-color="#ffd04b"
            >
              <el-menu-item index="/">
                <i class="el-icon-menu"></i>
                <span slot="title" @click="jumpHome">首页</span>
              </el-menu-item>

              <el-menu-item index="/published">
                <i class="el-icon-menu"></i>
                <span slot="title" @click="jumpPublished">已发布</span>
              </el-menu-item>

              <el-menu-item index="/census">
                <i class="el-icon-menu"></i>
                <span slot="title" @click="jumpStato">统计</span>
              </el-menu-item>
              <el-menu-item index="/publications">
                <i class="el-icon-menu"></i>
                <span slot="title" @click="jumpWarkdown">发布文章</span>
              </el-menu-item>
              <el-menu-item index="/tabs">
                <i class="el-icon-menu"></i>
                <span slot="title" @click="jumpTag">标签页</span>
              </el-menu-item>
              <el-menu-item index="/export">
                <i class="el-icon-menu"></i>
                <span slot="title" @click="jumpQuery">导出excel</span>
              </el-menu-item>
              <el-menu-item index="/imageUpload">
                <i class="el-icon-menu"></i>
                <span slot="title" @click="jumpUpload">图片上传</span>
              </el-menu-item>
              <el-menu-item index="/quit">
                <i class="el-icon-menu"></i>
                <span slot="title" @click="go()">退出系统</span>
              </el-menu-item>
            </el-menu>
          </el-col>
        </el-row>
      </div>
      <!-- 这是子路由也是主页的内容，写在home中 -->
      <div class="box-right">
        <router-view></router-view>
      </div>
    </div>
  </div>
</template>

<script>
import dayjs from 'dayjs'
export default {
  data() {
    return {
      name: "",
      time: ""
    };
  },
  components: {},
  methods: {
   
    // 把登录时间转换为标准时间
    standardTime() {
      
    }
  },
  mounted() {
    this.name = localStorage.getItem("username");
    this.time = sessionStorage.getItem('time');
    this.standardTime();
  },
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
.head {
  justify-content: space-between;
  display: flex;
  width: 100%;
  height: 50px;
  line-height: 50px;
  font-size: 18px;
  color: aliceblue;
  background: rgb(46, 94, 133);
  overflow: hidden;
}
.head div {
  margin: 0 30px 0 30px;
}
.box-left {
  width: 10%;
  // height:720px;
  background: #545c64;
}
.box {
  display: flex;
}
.box-right {
  width: 88%;
  height: 790px;
  margin: 30px 14px 10px 15px;
  background: #F0F2F5;
}
</style>