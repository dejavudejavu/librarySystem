<template>
    <!--登录表单-->
    <body id="poster" class="back-image">
    <el-form class="login-container" label-position="left" label-width="0px">
        <!--标题-->
        <h3 class="login_title">图书管理系统</h3>
        <!--用户名输入框-->
        <el-form-item class="login_title">
            <el-input type="text" v-model="loginForm.username"
                      auto-complete="off" placeholder="用户名"></el-input>
        </el-form-item>
        <!--密码输入框-->
        <el-form-item>
            <el-input type="password" v-model="loginForm.password"
                      @keyup.enter.native="login"
                      auto-complete="off" placeholder="密码"></el-input>
        </el-form-item>
        <!--登录注册按钮-->
        <el-form-item style="text-align: center">
            <el-button type="primary" round v-on:click="login">登录</el-button>
            <el-button type="primary" plain round v-on:click="register">注册</el-button>
        </el-form-item>
    </el-form>
    </body>
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
      loginForm: {
        username: '',
        password: ''
      },
      responseResult: []
    }
  },
  methods: {
    login () {
      this.$axios
        .post('/user/login', {
          // 携带参数
          username: this.loginForm.username,
          password: this.loginForm.password
        }).then((response) => {
          if (response.code === '200') {
            // message是后端传回的登录失败的信息
            this.$message(response.msg)
            this.$store.commit('login', response.data)
            // 页面跳转到首页
            var path = this.$route.query.redirect
            this.$router.push({path: path === '/' || path === undefined ? '/index' : path})
          } else {
            // 登录成功页面跳转，并把后端传回的登录信息，储存在store中
            this.$message(response.data.msg)
          }
        })
        .catch(() => {
          var path = this.$route.query.redirect
          this.$router.push({path: path === '/' || path === undefined ? '/index' : path})
          this.$message('登录失败')
        })
    },
    register () {
      this.$router.push({path: '/register'})
    }
  }
}
</script>

<style scoped>
    .login-container {
        border-radius: 15px;
        background-clip: padding-box;
        margin: 90px auto;
        width: 350px;
        padding: 35px 35px 15px 35px;
        background: #fff;
        border: 1px solid #eaeaea;
        box-shadow: 0 0 25px #cac6c6;
    }
    .login_title {
        margin: 0px auto 40px auto;
        text-align: center;
        color: #505458;
    }
    #poster {
        /*background: #409EFF;*/
        height: 100%;
        width: 100%;
        background-size: cover;
        position: fixed;
    }
    body,html{
        margin: 0;
        padding: 0;
    }
</style>
