<script>
export default {
  onLaunch: function() {
    // 检查是否已登录
    const userInfo = uni.getStorageSync('userInfo')
    if (!userInfo || !userInfo.studentId) {
      uni.reLaunch({ url: '/pages/login/login' })
    }
  }
}
</script>

<style>
/* 样式可以留空 */
</style>