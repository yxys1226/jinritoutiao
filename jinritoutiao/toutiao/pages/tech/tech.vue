<template>
  <view class="tech-page">
    <!-- 分类导航栏 -->
    <view class="category-bar">
      <view class="nav-item" @click="goToPage('sports')">体育</view>
      <view class="nav-item active" @click="goToPage('tech')">科技</view>
      <view class="nav-item" @click="goToPage('finance')">财经</view>
    </view>

    <view class="page-header">
      <h1>科技新闻</h1>
      <text class="subtle">聚焦 AI、芯片与数字创新</text>
    </view>

    <view class="news-grid">
      <view
        v-for="item in newsList"
        :key="item.id"
        class="news-card"
        @click="openDetail(item)"
      >
        <image class="news-image" :src="item.image" mode="aspectFill" />
        <view class="news-content">
          <view class="news-meta">
            <text class="source">{{ item.source }}</text>
            <text class="date">{{ item.date }}</text>
          </view>
          <text class="news-title">{{ item.title }}</text>
          <text class="news-summary">{{ item.summary }}</text>
        </view>
      </view>
    </view>

    <view class="footer-space"></view>
  </view>
</template>

<script setup>
import { ref } from 'vue'

const newsList = ref([
  {
    id: 1,
    title: '全球AI芯片大战再升级，未来三年或迎来新一轮产能扩张',
    summary: '多家科技巨头同步加码AI芯片布局，推动算力基础设施和边缘智能应用加速落地。',
    date: '2026-06-14',
    source: 'TechCrunch',
    image: 'https://picsum.photos/200/150?random=1'
  },
  {
    id: 2,
    title: '新型折叠屏手机亮相，续航和影像体验同步提升',
    summary: '新一代折叠屏设备在轻薄结构、续航和AI拍照方面实现多项突破。',
    date: '2026-06-13',
    source: 'Wired',
    image: 'https://picsum.photos/200/150?random=2'
  },
  {
    id: 3,
    title: '自动驾驶公司完成大规模城市测试，商业化路径更清晰',
    summary: '在城市开放道路测试中，自动驾驶系统的安全性和路径决策表现持续优化。',
    date: '2026-06-12',
    source: 'The Verge',
    image: 'https://picsum.photos/200/150?random=3'
  },
  {
    id: 4,
    title: '量子计算实验室发布新型纠错架构，误差率显著下降',
    summary: '研究团队提出新的量子比特纠错方案，有望提升量子计算稳定性与实用性。',
    date: '2026-06-11',
    source: 'MIT Tech Review',
    image: 'https://picsum.photos/200/150?random=4'
  },
  {
    id: 5,
    title: '头部电商平台推出本地AI助手，服务更贴近用户需求',
    summary: 'AI助手将整合商品推荐、售后支持和个性化购物建议，提升消费体验。',
    date: '2026-06-10',
    source: 'Engadget',
    image: 'https://picsum.photos/200/150?random=5'
  },
  {
    id: 6,
    title: '新能源车厂商发布更快充电方案，补能时间大幅缩短',
    summary: '新一代超快充电技术可将充电时间缩短至传统方案的一半左右。',
    date: '2026-06-09',
    source: 'TechRadar',
    image: 'https://picsum.photos/200/150?random=6'
  }
])

const goToPage = (type) => {
  const routes = {
    sports: '/pages/sports/sports',
    tech: '/pages/tech/tech',
    finance: '/pages/finance/finance'
  }

  if (routes[type]) {
    uni.navigateTo({ url: routes[type] })
  }
}

const openDetail = (item) => {
  console.log('跳转到科技新闻', item.id, item.title)
}
</script>

<style scoped>
.tech-page {
  min-height: 100vh;
  background: linear-gradient(180deg, #f5f7fb 0%, #edf3ff 100%);
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

.nav-item.active {
  background: #1677ff;
  color: #fff;
}

.page-header {
  padding: 18px 16px 8px;
}

.page-header h1 {
  margin: 0;
  font-size: 28px;
  line-height: 1.2;
  color: #1f2937;
}

.subtle {
  display: block;
  margin-top: 6px;
  color: #6b7280;
  font-size: 13px;
}

.news-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 14px;
  padding: 0 16px;
}

.news-card {
  background: #fff;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 8px 18px rgba(15, 23, 42, 0.08);
}

.news-image {
  width: 100%;
  height: 130px;
}

.news-content {
  padding: 10px 12px 12px;
}

.news-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 6px;
  color: #6b7280;
  font-size: 12px;
}

.source {
  color: #1677ff;
  font-weight: 600;
}

.news-title {
  display: block;
  font-size: 15px;
  font-weight: 700;
  color: #111827;
  line-height: 1.35;
  margin-bottom: 6px;
}

.news-summary {
  display: block;
  color: #4b5563;
  font-size: 13px;
  line-height: 1.45;
}

.footer-space {
  height: 24px;
}

@media (max-width: 900px) {
  .news-grid {
    grid-template-columns: 1fr;
  }
}
</style>