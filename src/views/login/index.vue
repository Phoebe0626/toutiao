<template>
  <div class="login_container">
    <!-- 导航栏 -->
    <van-nav-bar title="明日头条-登录"></van-nav-bar>
    <!-- 表单 -->
    <van-form ref="form" :show-error-message="false">
      <van-field
        v-model="mobile"
        label="手机号"
        placeholder="请输入手机号"
        required
        :rules="[{required: true, validatorForMobile, message: '请输入手机号',trigger:'onBlur'}]"
      />
      <van-field
        v-model="code"
        label="密码"
        placeholder="请输入密码号"
        required
        :rules="[{ required: true, validatorForCode, message: '请输入验证码', trigger: 'onBlur' }]"
      />
    </van-form>
    <!-- 按钮 -->
    <div class="btn-wrap">
      <van-button type="info" class="btn" @click="hLogin">登录</van-button>
    </div>
  </div>
</template>

<script>
import { login } from '@/api/user.js'

export default {
  name: 'Login',
  data () {
    return {
      mobile: '',
      code: ''
    }
  },
  methods: {
    // 验证码校验规则
    validatorForCode (val) {
      return val !== ''
    },
    // 手机号校验规则
    validatorForMobile (val) {
      return val !== ''
    },
    // 登录
    hLogin () {
      this.$refs.form.validate().then(async () => {
        const { mobile, code } = this
        const res = await login(mobile, code)
        console.log(res)
      }).catch(error => {
        console.log(error)
        this.$toast('手机号或密码格式有误')
      })
    }
  }
}
</script>

<style lang="less" scoped>
.login_container {
  .btn-wrap {
    padding: 20px;
    .btn {
      width: 100%;
      background-color: #6db4fb;
      color: #fff;
    }
  }
}
</style>
