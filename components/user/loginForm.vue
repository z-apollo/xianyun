<template>
  <el-form :model="form" ref="form" :rules="rules" class="form">
    <el-form-item class="form-item" prop="username">
      <el-input v-model="form.username" placeholder="用户名/手机"></el-input>
    </el-form-item>

    <el-form-item class="form-item" prop="password">
      <el-input v-model="form.password" placeholder="密码" type="password"></el-input>
    </el-form-item>

    <p class="form-text">
      <nuxt-link to="#">忘记密码</nuxt-link>
    </p>

    <el-button class="submit" type="primary" @click="handleLoginSubmit">登录</el-button>
  </el-form>
</template>

<script>
export default {
  data() {
    return {
      //表单数据
      form: {
        username: "",
        password: ""
      },
      //表单规则
      rules: {
        username: [
          { required: true, message: "请输入用户名", trigger: "blur" }
        ],
        password: [
            { required: true, message: "请输入密码", trigger: "blur" }
        ]
      }
    }
  },

  methods: {
    //提交登录
    handleLoginSubmit() {
      this.$refs.form.validate(async valid => {
        //valid是表单验证的结果
        if (valid) {
          //提交登录接口
          // this.$axios({
          //   url: "/accounts/login",
          //   data: this.form,
          //   method: "POST"
          // }).then(res => {
          //   console.log(res);
          //   if (res.status == 200) {
          //     this.$message.success("登录成功")
          //     //跳转到首页
          //     //this.$router.push("/")

          //     const data = res.data
          //     //把用户信息token保存到本地，在头部组件中显示用户数据

          //     //vuex不能通过直接赋值方式来修改state的值
          //     //this.$store.state.user.username = data.user.nickname;

          //     //通过调用mutation下的方法掉修改state的值,commit方法调用mutation的方法
          //      this.$store.commit("user/setUserInfo", data)
          //   }
          // })
          
          //this.$store.dispatch用于调用actions的方法
          const res = await this.$store.dispatch("user/login", this.form)

          if(res.status === 200){
            this.$message.success("登录成功")
            this.$router.back("/")
          }
        }
      })
    }
  }
};
</script>

<style scoped lang="less">
.form {
  padding: 25px;
}
.form-item {
  margin-bottom: 20px;
}
.form-text {
  font-size: 12px;
  color: #409eff;
  text-align: right;
  line-height: 1;
}
.submit {
  width: 100%;
  margin-top: 10px;
}
</style>