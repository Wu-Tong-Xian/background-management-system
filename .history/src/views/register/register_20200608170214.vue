
    
<template>
 <div class="box">
  <div ><img src="../../assets/login3.jpg" alt="" class="bg-img"></div>
  <div class="login-box">
     <div class="textStyle">欢迎来到小艾后台管理系统</div>
     <div style='width:400px'>
        <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm ">
          <el-form-item label="用户名" prop="username">
            <el-input v-model="ruleForm.username"></el-input>
          </el-form-item>
          <el-form-item label="密码" prop="password">
            <el-input v-model="ruleForm.password" show-password></el-input>
          </el-form-item>
          <el-form-item label="确认密码" prop="rePwd">
            <el-input v-model="ruleForm.rePwd" show-password></el-input>
          </el-form-item>
          <el-form-item label="邮箱" prop="email">
            <el-input v-model="ruleForm.email" show-password></el-input>
          </el-form-item>
          
            <el-form-item >
              <el-button type="primary" @click="login()">登录</el-button>
              <el-button type="primary" @click="login()" class="register-box">注册</el-button>
            </el-form-item>
            
          
          
        </el-form>
     </div>
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
     //自定义验证规则都是一个函数 里面传入三个参数 
    //  rule: 规则一般不用  value 就是代表输入的值
    // callback 必须调用这个callback才能进入下一把
      let validatePass = (rule, value, callback) => {
        
         if (value !== this.ruleForm.password) {
          callback(new Error('两次输入密码不一致!'));
        } else {
          callback();
        }
      };
     return {
       
      //  ruleForm是一个对象  里面写绑定的
       ruleForm:{
         username:'',
         password:'',
         rePwd:'',
         email:''
       },
      //  验证规则
       rules:{
         //属性就是表单prop对应的值,每一个验证都是一个数组
         //数组里面就放验证规则，验证规则又是一个对象
         //required 是否必填message：错误提示 trigger：触发方式通常都是blur（失去焦点就做验证）
         //最小和最大输入长度 min 和max
         username:[
           {
             required:true ,message:'用户名不能为空',trigger:'blur'
           },
           {
             min:2,max:10,message:'用户名在2-10之间',trigger:'blur'
           }
         ],
         password:[
           {
              required:true ,message:'密码不能为空',trigger:'blur'
           },
           {
             min:6,max:16,message:'用户名在6-16之间',trigger:'blur'
           }
         ],
         rePwd:[
           {
              required:true ,message:'确认密码不能为空',trigger:'blur'
           },
           {
             validator:validatePass,trigger:'blur'
           }
         ],
         email:[
           {
              required:true ,message:'邮箱不能为空',trigger:'blur'
           },
           {
             type:'email',message:'请输入正确的邮箱地址',trigger:'blur'  //这里可以用change实施监听知道输入正确才取消提示
           }
         ]
     }
     }
   },
   methods: {
      login() {   //$refs 获取到dom元素  上面ref绑定了ruleForm  也可以通过传一个实参 这里传形参
        //validate是做验证的，里面又一个valid属性是布尔值 如果为true就代表
        // 表单全部输入正确，如果为false 就代表表单输入不正确
        this.$refs.ruleForm.validate((valid) => {
          if (valid) {
            this.$message.success('登录成功')
             localStorage.setItem('user',JSON.stringify('user'))
            this.$router.push('/home')
          } else {
            // success/warning/info/error 
            this.$message.error('信息填写有误，请重新填写')
            return false;
          }
        });
      },
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
    top:100px;
    left: 470px;
    margin: 0 auto;
    width: 500px;
    height: 400px;
    
    box-shadow: 0 0 10px rgb(120, 172, 113);
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
  .register-box {
    margin-left: 160px;
  }
  .demo-ruleForm {
    color: rgb(230, 215, 215);
  }
</style>