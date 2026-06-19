<template>
  <view class="video-container">
    <!-- 视频卡片列表 -->
    <view class="video-list">
      <view 
        class="video-item" 
        v-for="(item, index) in videoList" 
        :key="index"
        @click="handleVideoClick(item)"
      >
        <!-- 视频封面图 -->
        <image 
          class="video-cover" 
          :src="item.cover" 
          mode="aspectFill"
        ></image>
        <!-- 视频信息 -->
        <view class="video-info">
          <text class="video-title">{{ item.title }}</text>
          <view class="video-meta">
            <text class="video-author">{{ item.author }}</text>
            <text class="video-play-count">{{ item.playCount }}次播放</text>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      // 假数据：视频卡片列表
      videoList: [
        {
          id: 1,
          title: "2024世界杯精彩进球集锦",
          author: "足球解说员",
          playCount: 125000,
          cover: "https://picsum.photos/200/150?random=10"
        },
        {
          id: 2,
          title: "科技新品发布会全程回顾",
          author: "数码测评君",
          playCount: 89200,
          cover: "https://picsum.photos/200/150?random=11"
        },
        {
          id: 3,
          title: "新手理财入门教程",
          author: "财经老司机",
          playCount: 56300,
          cover: "https://picsum.photos/200/150?random=12"
        },
        {
          id: 4,
          title: "夏日穿搭技巧分享",
          author: "时尚博主小A",
          playCount: 34100,
          cover: "https://picsum.photos/200/150?random=13"
        },
        {
          id: 5,
          title: "猫咪的可爱日常合集",
          author: "萌宠日常",
          playCount: 215000,
          cover: "https://picsum.photos/200/150?random=14"
        }
      ]
    };
  },
  methods: {
    // 点击视频卡片的事件（可后续扩展跳转播放页）
    handleVideoClick(item) {
      console.log("点击了视频：", item.title);
      // uni.navigateTo({
      //   url: `/pages/video-detail/video-detail?id=${item.id}`
      // });
    }
  }
};
</script>

<style scoped>
.video-container {
  padding: 10rpx;
  background-color: #f5f5f5;
  min-height: 100vh;
}

.video-list {
  display: flex;
  flex-direction: column;
  gap: 20rpx;
}

.video-item {
  display: flex;
  background-color: #fff;
  border-radius: 12rpx;
  overflow: hidden;
  box-shadow: 0 2rpx 8rpx rgba(0, 0, 0, 0.08);
}

.video-cover {
  width: 220rpx;
  height: 165rpx;
  flex-shrink: 0;
}

.video-info {
  flex: 1;
  padding: 20rpx;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.video-title {
  font-size: 32rpx;
  font-weight: 500;
  color: #333;
  line-height: 1.4;
  margin-bottom: 16rpx;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 2;
  overflow: hidden;
}

.video-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 24rpx;
  color: #999;
}
</style>