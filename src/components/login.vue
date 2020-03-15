<template>
  <div id="login" class="login">
    <div class="login-info">
      <div class="login-img">
        <img src="../assets/logo.png" alt srcset />
      </div>
      <!-- 表单 -->
      <el-form :rules="loginformrouter" ref="logininfoForm" :model="loginform" class="user-form">
        <el-form-item prop="username">
          <el-input prefix-icon="iconfont icon-user" v-model="loginform.username"></el-input>
        </el-form-item>
        <el-form-item prop="userpasw">
          <el-input
            type="password"
            prefix-icon="iconfont icon-3702mima"
            v-model="loginform.password"
          ></el-input>
        </el-form-item>
      </el-form>
      <div class="footer-btn">
        <el-button @click="login">登录</el-button>
        <el-button type="primary" @click="resetloginform">重置</el-button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      // 登录表单
      loginform: {
        username: 'admin',
        password: '123456'
      },
      //   验证
      loginformrouter: {
        username: [
          { required: true, message: '请输入用户名', trigger: 'blur' },
          { min: 3, max: 8, message: '长度在 3 到 10 个字符', trigger: 'blur' }
        ],
        password: [
          { required: true, message: '请输入密码', trigger: 'blur' },
          { min: 6, max: 15, message: '长度在 8 到 15 个字符', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    //   重置
    resetloginform () {
      this.$refs.logininfoForm.resetFields()
    },
    // 登录
    login () {
      this.$refs.logininfoForm.validate(async valueid => {
        console.log(valueid)
        if (!valueid) return
        const { data: res } = await this.$http.post('login', this.loginform)
        if (res.meta.status !== 200) return this.$message.error('登录失败')
        this.$message({
          message: '登录成功',
          type: 'success'
        })
        // 将用户信息保存到本地存储
        window.localStorage.setItem('token', res.data.token)
        console.log(res)
        this.$router.push({
          path: '/home'
        })
      })
    }
  }

}
</script>

<style  lang="less" scoped >
.login {
  background-color: #ccc;
  height: 100%;
  .login-info {
    width: 28.125rem;
    height: 18.75rem;
    border-radius: 0.3125rem;
    background-color: white;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    .login-img {
      background-color: white;
      width: 8.125rem;
      height: 8.125rem;
      border: 0.0625rem solid #ccc;
      border-radius: 50%;
      padding: 0.625rem;
      box-shadow: 0 0 0.625rem #dddddd;
      position: absolute;
      left: 50%;
      transform: translate(-50%, -50%);
      img {
        width: 100%;
        height: 100%;
        border-radius: 50%;
        background-color: #eee;
      }
    }
  }
}
.user-form {
  position: absolute;
  bottom: 1.25rem;
  width: 100%;
  padding: 20px;
  box-sizing: border-box;
}
.footer-btn {
  position: absolute;
  bottom: 0;
  left: 50%;
}
</style>
