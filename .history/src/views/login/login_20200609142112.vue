
    
<template>
 <div class="box">
  <div ><img src="../../assets/login3.jpg" alt="" class="bg-img"></div>
  <div class="login-box">
     <div class="textStyle">欢迎来到小艾后台管理系统</div>
     <div style='width:400px'>
        <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
          <el-form-item label="用户名" prop="username">
            <el-input v-model="ruleForm.username"></el-input>
          </el-form-item>
          <el-form-item label="密码" prop="password">
            <el-input v-model="ruleForm.password" show-password></el-input>
          </el-form-item>
          <el-form-item label="确认密码" prop="rePwd">
            <el-input v-model="ruleForm.rePwd" show-password></el-input>
          </el-form-item>

          <div class="el-input-w fl">
            <el-form-item label="验证码"  prop="captcha" maxlength="20" >
              <el-input v-model="ruleForm.code"  ></el-input>
            </el-form-item>
            <!-- 用v-html 取解析我拿到的所有验证码 并且绑定一个方法点击依此就重新拿一个 -->
            <div @click='getCodes' v-html="codes" class="mg-l20 c-pointer"> </div>
          </div>
     
          <!-- <el-form-item label="邮箱" prop="email">
            <el-input v-model="ruleForm.email" show-password></el-input>
          </el-form-item> -->
          
            <el-form-item >
              <el-button type="primary" @click="register()"  >注册</el-button>
              <el-button type="primary" @click="login()" class="loginbox">登录</el-button>
            </el-form-item>
            
          
          
        </el-form>
     </div>
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
     //自定义验证规则都是一个函数 里面传入三个参数 
    //  rule: 规则一般不用  value 就是代表输入的值
    // callback 必须调用这个callback才能进入下一把
      let validatePass = (rule, value, callback) => {
         if (value !== this.ruleForm.password) {
          callback(new Error('两次输入密码不一致!'));
        } else {
          // callback();
        }
      };
     return {
       codes:'' ,
      //  ruleForm是一个对象  里面写绑定的
       ruleForm:{
         username:'',  //用户名
         password:'',  //密码
         rePwd:'',   //确认密码
        //  email:'', //邮箱
         code:'' //验证码
         
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
             min:2,max:10,message:'用户名在2-16之间',trigger:'blur'
           }
         ],
         password:[
           {
              required:true ,message:'密码不能为空',trigger:'blur'
           },
           {
             min:6,max:16,message:'密码在6-16之间',trigger:'blur'
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
        //  email:[
        //    {
        //       required:true ,message:'邮箱不能为空',trigger:'blur'
        //    },
        //    {
        //      type:'email',message:'请输入正确的邮箱地址',trigger:'blur'  //这里可以用change实施监听知道输入正确才取消提示
        //    }
        //  ],
          code:[
           {
              required:true ,message:'验证码不能为空',trigger:'blur'
           },
           {
             trigger:'blur'  //这里可以用change实施监听知道输入正确才取消提示
           }
         ]
     }
     }
   },
   methods: {
    //  获取验证码 点击一次就重新获取一个新的验证码
     getCodes(){
       axios.get('/api/captcha').then(res =>{
        //  console.log(res.data);
         this.codes=res.data
       }).catch(err =>{
         console.log(err);
       })
     },
   // /user/login: /user/register  - post请求: - 参数: - username: 用户名 - password: 密码 验证码 ：code
    login() {   //$refs 获取到dom元素  上面ref绑定了ruleForm  也可以通过传一个实参 这里传形参
      //validate是做验证的，里面又一个valid属性是布尔值 如果为true就代表
      // 表单全部输入正确，如果为false 就代表表单输入不正确
      axios.post('/api/user/login',{
        username:this.ruleForm.username,
        password:this.ruleForm.password,
        code:this.ruleForm.code
      }).then(res =>{
        if(res.data.code===200){
        //  this.$message({
        //     message: res.data.message,
        //     type:'success'
        //    })
        this.$message.success(res.data.message)
        localStorage.setItem('username',this.ruleForm.username)  //存储用户名
        this.$router.push('/')
        sessionStorage.setItem('data',this.dayjs(new Date()))         //登录时间存储
        }  else{
           this.$message({
            message: res.data.message,
            type:'error'
           })
        }
        
      }).catch(err =>{
        console.log(err);
      })


      
    },
    register(){
      this.$router.push('/register')
    }
   },
   mounted() {
     this.getCodes()
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
    left: 490px;
    margin: 0 auto;
    width: 500px;
    height: 360px;
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