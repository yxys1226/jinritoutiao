<template>
  <view class="hot-page">
    <!-- 分类导航栏 -->
    <view class="category-bar">
      <view class="nav-item" @click="goToPage('sports')">体育</view>
      <view class="nav-item" @click="goToPage('tech')">科技</view>
      <view class="nav-item" @click="goToPage('finance')">财经</view>
    </view>

    <view class="page-header">
      <h1>热点新闻</h1>
      <text class="subtle">今日最受关注的实时热点</text>
    </view>

    <view class="hot-list">
      <view
        v-for="item in hotList"
        :key="item.id"
        class="hot-card"
        @click="openNews(item)"
      >
        <view class="rank-tag">#{{ item.id }}</view>
        <view class="hot-card__content">
          <text class="hot-title">{{ item.title }}</text>
          <text class="hot-summary">{{ item.summary }}</text>
          <view class="hot-footer">
            <text class="hot-time">{{ item.time }}</text>
            <text class="hot-source">{{ item.source }}</text>
          </view>
        </view>
      </view>
    </view>

    <view class="footer-space"></view>
  </view>
</template>

<script setup>
import { ref } from 'vue'

const hotList = ref([
  {
    id: 1,
    title: '城市新地标开工，未来三年将带动周边消费增长',
    summary: '新片区建设加速推进，多项交通和商业配套同步落地。',
    time: '10:30',
    source: '热点速递'
  },
  {
    id: 2,
    title: 'AI工具助力企业降本增效，行业应用加速落地',
    summary: '一批智能办公与客服方案在企业中快速推广。',
    time: '10:45',
    source: '科技日报'
  },
  {
    id: 3,
    title: '财经政策发布新信号，市场预期继续稳定向好',
    summary: '投资者关注产业链和消费升级带来的长期机会。',
    time: '11:00',
    source: '财经观察'
  },
  {
    id: 4,
    title: '本地体育赛事周末密集开赛，球迷关注度持续走高',
    summary: '多项联赛和友谊赛将于本周末集中进行。',
    time: '11:15',
    source: '体坛新闻'
  },
  {
    id: 5,
    title: '智能制造项目落地，机器人协作能力持续提升',
    summary: '自动化生产线的效率和安全性获得明显改善。',
    time: '11:30',
    source: '产业链视角'
  },
  {
    id: 6,
    title: '绿色金融产品创新增多，支持低碳产业融资需求',
    summary: '金融机构推出更多贴近绿色转型目标的产品。',
    time: '11:45',
    source: '金融时报'
  }
])

const goToPage = (type) => {
  const map = {
    sports: '/pages/sports/sports',
    tech: '/pages/tech/tech',
    finance: '/pages/finance/finance'
  }

  if (map[type]) {
    uni.navigateTo({ url: map[type] })
  }
}

const openNews = (item) => {
  console.log('打开热点新闻', item.id, item.title)
}
</script>

<style scoped>
.hot-page {
  min-height: 100vh;
  background: linear-gradient(180deg, #f8fafc 0%, #eef4ff 100%);
  padding-bottom: 24px;
}

.category-bar {
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 12px 16px;
  background: #fff;
  border-bottom: 1px solid #edf2f7;
  position: sticky;
  top: 0;
  z-index: 10;
}

.nav-item {
  padding: 8px 12px;
  border-radius: 999px;
  font-size: 14px;
  color: #5b6472;
  font-weight: 500;
}

.page-header {
  padding: 18px 16px 8px;
}

.page-header h1 {
  margin: 0;
  font-size: 28px;
  line-height: 1.2;
  color: #111827;
}

.subtle {
  display: block;
  margin-top: 6px;
  color: #6b7280;
  font-size: 13px;
}

.hot-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
  padding: 0 16px;
}

.hot-card {
  display: flex;
  background: #fff;
  border-radius: 16px;
  padding: 12px;
  box-shadow: 0 8px 18px rgba(15, 23, 42, 0.08);
}

.rank-tag {
  width: 42px;
  height: 42px;
  border-radius: 12px;
  background: linear-gradient(135deg, #1677ff, #6aa8ff);
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 13px;
  font-weight: 700;
  flex-shrink: 0;
}

.hot-card__content {
  flex: 1;
  margin-left: 10px;
}

.hot-title {
  display: block;
  font-size: 15px;
  font-weight: 700;
  color: #111827;
  line-height: 1.35;
  margin-bottom: 4px;
}

.hot-summary {
  display: block;
  font-size: 13px;
  color: #4b5563;
  line-height: 1.45;
  margin-bottom: 8px;
}

.hot-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 12px;
  color: #6b7280;
}

.hot-source {
  color: #1677ff;
  font-weight: 600;
}

.footer-space {
  height: 24px;
}
</style>