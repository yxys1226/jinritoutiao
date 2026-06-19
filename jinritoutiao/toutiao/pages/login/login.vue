<template>
  <view class="login-container">
    <!-- 今日头条图标 -->
    <view class="icon-area">
      <image src="/static/logo.png" mode="aspectFit" class="icon"></image>
    </view>

    <!-- 标题 -->
    <view class="title-area">
      <text class="title">登录你的头条</text>
      <text class="subtitle">分享精彩内容</text>
    </view>

    <!-- 学号输入框（满足考核） -->
    <view class="form-item">
      <input placeholder="学号" v-model="studentId" />
    </view>

    <!-- 姓名输入框（满足考核） -->
    <view class="form-item">
      <input placeholder="姓名" v-model="userName" />
    </view>

    <!-- 密码输入框 -->
    <view class="form-item">
      <input placeholder="密码" type="password" v-model="password" />
    </view>

    <!-- 找回密码链接 -->
    <view class="forgot-pwd">
      <text @click="forgotPwd">找回密码</text>
    </view>

    <!-- 登录按钮 -->
    <button @click="handleLogin" type="primary" class="login-btn">登录</button>

    <!-- 用户协议 -->
    <view class="agreement">
      <checkbox :checked="agree" @click="toggleAgree" />已阅读并同意
      <text class="link">用户协议</text>和
      <text class="link">账号信息处理规则</text>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      studentId: '',
      userName: '',
      password: '',
      agree: true  // 默认勾选
    }
  },
  methods: {
    toggleAgree() {
      this.agree = !this.agree
    },
    forgotPwd() {
      uni.showToast({ title: '请联系管理员', icon: 'none' })
    },
    handleLogin() {
      if (!this.agree) {
        uni.showToast({ title: '请阅读并同意用户协议', icon: 'none' })
        return
      }
      if (this.studentId === '2312505038' && this.userName === '文俊宇' && this.password === '123456') {
        uni.setStorageSync('userInfo', { studentId: this.studentId, userName: this.userName })
        uni.switchTab({ url: '/pages/index/index' })
      } else {
        uni.showToast({ title: '学号或姓名或密码错误', icon: 'none' })
      }
    }
  }
}
</script>

<style scoped>
.login-container {
  padding: 60rpx 40rpx;
  background-color: #fff;
  min-height: 100vh;
}
.icon-area {
  text-align: center;
  margin-top: 60rpx;
  margin-bottom: 40rpx;
}
.icon {
  width: 120rpx;
  height: 120rpx;
  border-radius: 24rpx;
}
.title-area {
  text-align: center;
  margin-bottom: 60rpx;
}
.title {
  font-size: 48rpx;
  font-weight: bold;
  color: #333;
  display: block;
}
.subtitle {
  font-size: 28rpx;
  color: #999;
  margin-top: 12rpx;
  display: block;
}
.form-item {
  margin-bottom: 36rpx;
  border-bottom: 1px solid #f0f0f0;
}
input {
  padding: 20rpx 0;
  font-size: 32rpx;
  border: none;
}
.forgot-pwd {
  text-align: right;
  margin-bottom: 60rpx;
}
.forgot-pwd text {
  font-size: 28rpx;
  color: #ff5a5f;
}
.login-btn {
  background-color: #ff5a5f;
  color: white;
  border-radius: 48rpx;
  margin-bottom: 40rpx;
}
.agreement {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 24rpx;
  color: #999;
}
.agreement .link {
  color: #ff5a5f;
  margin: 0 4rpx;
}
checkbox {
  transform: scale(0.7);
  margin-right: 8rpx;
}
</style>