<template>
  <view class="page">
    <!-- 固定红色渐变背景 -->
    <view class="red-bg"></view>

    <!-- 吸顶用户卡片 -->
    <view class="sticky-card">
      <view class="user-card">
        <view class="user-row" @click="goProfile">
          <view class="avatar">
            <text class="avatar-text">{{ avatarText }}</text>
          </view>
          <view class="user-detail">
            <text class="user-name">{{ userInfo.userName || '头条用户' }}</text>
            <text class="user-id">学号：{{ userInfo.studentId || '未绑定' }}</text>
          </view>
        </view>
        <view class="stats">
          <view class="stat-item"><text class="num">0</text><text class="label">关注</text></view>
          <view class="stat-item"><text class="num">0</text><text class="label">粉丝</text></view>
          <view class="stat-item"><text class="num">0</text><text class="label">获赞</text></view>
          <view class="stat-item cert"><text class="cert-text">申请认证 ></text></view>
        </view>
      </view>
    </view>

    <!-- 下方内容 -->
    <view class="content">
      <view class="grid">
        <view class="grid-item" @click="handleTap('order')">
          <text class="grid-icon">🛒</text>
          <text>购物/订单</text>
        </view>
        <view class="grid-item" @click="handleTap('message')">
          <text class="grid-icon">💬</text>
          <text>消息私信</text>
        </view>
        <view class="grid-item" @click="handleTap('creator')">
          <text class="grid-icon">✍️</text>
          <text>创作中心</text>
        </view>
        <view class="grid-item" @click="handleTap('task')">
          <text class="grid-icon">🎁</text>
          <text>任务</text>
        </view>
      </view>

      <view class="list-block">
        <view class="list-title">常用功能</view>
        <view class="list-item" @click="handleTap('history')"><text>浏览历史</text><text class="arrow">></text></view>
        <view class="list-item" @click="handleTap('bookshelf')"><text>书架</text><text class="arrow">></text></view>
        <view class="list-item" @click="handleTap('shortplay')"><text>在看短剧</text><text class="arrow">></text></view>
        <view class="list-item" @click="handleTap('all')"><text>全部功能</text><text class="arrow">></text></view>
      </view>

      <!-- 已移除：6月幸运签 和 完成挑战 卡片 -->

      <view class="tabs">
        <view v-for="(tab, idx) in tabs" :key="idx" class="tab" :class="{ active: activeTab === tab.key }" @click="activeTab = tab.key">{{ tab.name }}</view>
      </view>
      <view class="tab-content">
        <text class="empty-tip">{{ tabContent[activeTab] }}</text>
      </view>

      <view class="logout-wrapper">
        <button class="logout-btn" @click="logout">退出登录</button>
      </view>
      <view class="bottom-safe"></view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      userInfo: { studentId: '', userName: '' },
      activeTab: 'works',
      tabs: [
        { key: 'works', name: '作品' },
        { key: 'favorites', name: '收藏' },
        { key: 'liked', name: '赞过' },
        { key: 'shortplay', name: '短剧' },
        { key: 'draft', name: '草稿' },
        { key: 'recommend', name: '推荐' }
      ],
      tabContent: {
        works: '暂无作品，去发布吧~',
        favorites: '暂无收藏',
        liked: '暂无赞过',
        shortplay: '暂无短剧记录',
        draft: '暂无草稿',
        recommend: '推荐内容将在这里展示'
      }
    };
  },
  computed: {
    avatarText() {
      const name = this.userInfo.userName;
      if (name && name.length) return name.charAt(0).toUpperCase();
      return '👤';
    }
  },
  onLoad() {
    this.loadUserInfo();
  },
  onShow() {
    this.loadUserInfo();
  },
  methods: {
    loadUserInfo() {
      const stored = uni.getStorageSync('userInfo');
      if (stored && stored.studentId) {
        this.userInfo = {
          studentId: stored.studentId,
          userName: stored.userName || stored.name || ''
        };
      } else {
        uni.reLaunch({ url: '/pages/login/login' });
      }
    },
    goProfile() {
      uni.showToast({ title: '个人资料', icon: 'none' });
    },
    handleTap(type) {
      uni.showToast({ title: `功能开发中: ${type}`, icon: 'none' });
    },
    logout() {
      uni.removeStorageSync('userInfo');
      uni.reLaunch({ url: '/pages/login/login' });
    }
  }
};
</script>

<style scoped>
.page {
  min-height: 100vh;
  background-color: #f5f5f5;
  position: relative;
}

.red-bg {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 360rpx;
  background: linear-gradient(135deg, #ff5a5f, #f03e3e);
  z-index: 0;
}

.sticky-card {
  position: sticky;
  top: 0;
  z-index: 10;
  padding-top: 20rpx;
  background-color: transparent;
}

.user-card {
  background: #fff;
  margin: 24rpx;
  border-radius: 32rpx;
  padding: 32rpx;
  box-shadow: 0 4rpx 16rpx rgba(0,0,0,0.08);
}

.user-row {
  display: flex;
  align-items: center;
  margin-bottom: 24rpx;
}
.avatar {
  width: 112rpx;
  height: 112rpx;
  background: linear-gradient(145deg, #ff5a5f, #e84a4f);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 24rpx;
}
.avatar-text {
  font-size: 52rpx;
  color: #fff;
  font-weight: 500;
}
.user-detail {
  flex: 1;
}
.user-name {
  font-size: 36rpx;
  font-weight: 600;
  color: #333;
  display: block;
  margin-bottom: 8rpx;
}
.user-id {
  font-size: 24rpx;
  color: #999;
}
.stats {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-top: 16rpx;
  border-top: 1rpx solid #eee;
}
.stat-item {
  flex: 1;
  text-align: center;
}
.stat-item .num {
  font-size: 32rpx;
  font-weight: 600;
  color: #333;
  display: block;
}
.stat-item .label {
  font-size: 24rpx;
  color: #999;
}
.cert .cert-text {
  font-size: 26rpx;
  color: #ff5a5f;
  font-weight: 500;
}

.content {
  position: relative;
  z-index: 1;
  padding-bottom: 40rpx;
}

.grid {
  display: flex;
  flex-wrap: wrap;
  background: #fff;
  margin: 0 24rpx 24rpx;
  border-radius: 24rpx;
  padding: 20rpx 0;
}
.grid-item {
  width: 25%;
  text-align: center;
  padding: 20rpx 0;
  position: relative;
}
.grid-icon {
  font-size: 48rpx;
  display: block;
  margin-bottom: 12rpx;
}
.grid-item text:first-of-type {
  font-size: 24rpx;
  color: #333;
}

.list-block {
  background: #fff;
  margin: 0 24rpx 24rpx;
  border-radius: 24rpx;
  padding: 0 24rpx;
}
.list-title {
  font-size: 32rpx;
  font-weight: 500;
  padding: 24rpx 0 12rpx;
  color: #333;
}
.list-item {
  display: flex;
  justify-content: space-between;
  padding: 28rpx 0;
  border-bottom: 1rpx solid #f5f5f5;
  font-size: 28rpx;
  color: #444;
}
.list-item .arrow {
  color: #ccc;
  font-size: 32rpx;
}
.list-item:last-child {
  border-bottom: none;
}

.tabs {
  display: flex;
  background: #fff;
  margin: 0 24rpx;
  border-radius: 24rpx 24rpx 0 0;
  overflow-x: auto;
}
.tab {
  flex: 1;
  text-align: center;
  padding: 24rpx 0;
  font-size: 28rpx;
  color: #666;
  position: relative;
  white-space: nowrap;
}
.tab.active {
  color: #ff5a5f;
  font-weight: 500;
}
.tab.active::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 25%;
  width: 50%;
  height: 4rpx;
  background: #ff5a5f;
  border-radius: 2rpx;
}
.tab-content {
  background: #fff;
  margin: 0 24rpx 24rpx;
  border-radius: 0 0 24rpx 24rpx;
  padding: 60rpx 0;
  text-align: center;
}
.empty-tip {
  font-size: 26rpx;
  color: #bbb;
}

.logout-wrapper {
  padding: 30rpx 24rpx 60rpx;
}
.logout-btn {
  background: #fff;
  border: 1rpx solid #ff5a5f;
  color: #ff5a5f;
  border-radius: 60rpx;
  font-size: 30rpx;
  padding: 24rpx 0;
}
.bottom-safe {
  height: 60rpx;
}
</style>