<template>
  <div>
    <div class="heade j-between fl">
      <div class="mg-l20">欢迎来到{{username}}后台管理系统</div>
      <div class="mg-r20">中午好,亲爱的{{username}},上次登录时间是</div>
    </div>
    <div>
      <div class="dh">
        <el-row class="tac">
          <el-col :span="12">
            <el-menu
              default-active="1"
              class="el-menu-vertical-demo"
              @open="handleOpen"
              @close="handleClose"
              background-color="#545c64"
              text-color="#fff"
              active-text-color="#ffd04b"
            >
              <el-menu-item index="1" class="">
                <i class="el-icon-location-outline"></i>
                <span slot="title">首页</span>
              </el-menu-item>
              <el-menu-item index="2">
                <i class="el-icon-check"></i>
                <span slot="title">已发布</span>
              </el-menu-item>
              <el-menu-item index="3" >
                <i class="el-icon-document"></i>
                <span slot="title">统计</span>
              </el-menu-item>
               <el-menu-item index="4" >
                <i class="el-icon-document"></i>
                <span slot="title">发表文章</span>
              </el-menu-item>
              <el-menu-item index="5">
                <i class="el-icon-setting"></i>
                <span slot="title">标签页</span>
              </el-menu-item>
              <el-menu-item index="6">
                <i class="el-icon-setting"></i>
                <span slot="title">导出excel</span>
              </el-menu-item>
              <el-menu-item index="7">
                <i class="el-icon-picture-outline"></i>
                <span slot="title">图片上传</span>
              </el-menu-item>
              <el-menu-item index="8">
                <i class="el-icon-delete"></i>
                <span slot="title">退出登录</span>
              </el-menu-item>
            </el-menu>
          </el-col>
        </el-row>
      </div>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: "",
  props: {},
  components: {},
  data() {
    return {
      username
    };
  },
  methods: {},
  mounted() {
    this.username = sessionStorage.setItem("username");
  },
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
.heade {
  width: 100%;
  background: #2E5E85;
  height: 58px;
  line-height: 58px;
  color: rgb(241, 233, 233);
  letter-spacing:4px;
}
.dh {
  width: 25%; 
}
.el-menu-item {
  margin-top: 40px;
}
</style>