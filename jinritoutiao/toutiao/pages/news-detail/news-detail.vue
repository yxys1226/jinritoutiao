<template>
  <view class="detail-container">
    <!-- 标题区域 -->
    <view class="detail-header">
      <text class="detail-title">{{ news.title }}</text>
      <view class="detail-meta">
        <text class="detail-source">{{ news.source }}</text>
        <text class="detail-date">{{ news.date }}</text>
        <text v-if="news.comments" class="detail-comments">{{ news.comments }}条评论</text>
      </view>
    </view>

    <!-- 详情页大图 -->
    <image 
      v-if="news.detailImage" 
      class="detail-image" 
      :src="news.detailImage" 
      mode="widthFix"
    ></image>

    <!-- 正文内容 -->
    <view class="detail-content">
      <text class="content-text">{{ news.content }}</text>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      news: {
        id: '',
        title: '',
        source: '',
        date: '',
        comments: '',
        content: '',
        detailImage: ''
      }
    }
  },
  onLoad(options) {
    // 从本地存储获取新闻数据
    const newsData = uni.getStorageSync('currentNews')
    if (newsData && newsData.id == options.id) {
      this.news = newsData
      // 设置页面标题
      uni.setNavigationBarTitle({
        title: newsData.title.length > 20 ? newsData.title.slice(0, 20) + '...' : newsData.title
      })
    } else {
      uni.showToast({
        title: '内容加载失败',
        icon: 'none'
      })
      setTimeout(() => {
        uni.navigateBack()
      }, 1500)
    }
  }
}
</script>

<style scoped>
.detail-container {
  min-height: 100vh;
  background: #fff;
  padding: 30rpx;
}

.detail-header {
  padding-bottom: 30rpx;
  border-bottom: 1px solid #f0f0f0;
  margin-bottom: 30rpx;
}

.detail-title {
  font-size: 48rpx;
  font-weight: bold;
  color: #222;
  line-height: 1.4;
  display: block;
  margin-bottom: 20rpx;
}

.detail-meta {
  display: flex;
  align-items: center;
  gap: 24rpx;
  flex-wrap: wrap;
}

.detail-source, .detail-date, .detail-comments {
  font-size: 26rpx;
  color: #999;
}

.detail-image {
  width: 100%;
  border-radius: 16rpx;
  margin-bottom: 30rpx;
  background-color: #f5f5f5;
}

.detail-content {
  line-height: 1.8;
  margin-bottom: 40rpx;
}

.content-text {
  font-size: 34rpx;
  color: #333;
  white-space: pre-wrap;
  word-break: break-all;
}
</style>