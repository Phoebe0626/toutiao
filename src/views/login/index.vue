<template>
  <div class="login_container">
    <!-- 导航栏 -->
    <van-nav-bar title="明日头条-登录"></van-nav-bar>
    <!-- 表单 -->
    <van-form>
      <van-field
        v-model="mobile"
        label="手机号"
        placeholder="请输入手机号"
      />
      <van-field
        v-model="code"
        label="密码"
        placeholder="请输入密码号"
      />
    </van-form>
    <!-- 按钮 -->
    <div class="btn-wrap">
      <van-button type="info" class="btn">登录</van-button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
      mobile: '',
      code: ''
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
