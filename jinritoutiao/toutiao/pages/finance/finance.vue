<template>
  <view class="page">
    <view class="header">
      <text class="title">财经新闻</text>
      <text class="subtitle">聚焦市场热点、政策变化与行业动态</text>
    </view>

    <view class="news-list">
      <view v-for="item in newsList" :key="item.id" class="news-card">
        <view class="news-top">
          <text class="tag">{{ item.tag }}</text>
          <text class="time">{{ item.time }}</text>
        </view>
        <text class="news-title">{{ item.title }}</text>
        <text class="news-summary">{{ item.summary }}</text>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      newsList: [
        {
          id: 1,
          tag: '宏观',
          time: '10分钟前',
          title: '央行释放流动性，资本市场整体回暖',
          summary: '政策预期升温后，市场情绪明显改善，多家机构看好后续资金面表现。'
        },
        {
          id: 2,
          tag: '产业',
          time: '32分钟前',
          title: '新能源车企加码海外布局，产业链迎来新机遇',
          summary: '多家头部企业宣布扩大海外销售和产能布局，相关产业链公司受到关注。'
        },
        {
          id: 3,
          tag: '公司',
          time: '1小时前',
          title: '科技公司发布新一代智能终端，AI应用持续升温',
          summary: '行业巨头发布新品后，AI设备与相关技术板块获得资金追捧。'
        },
        {
          id: 4,
          tag: '金融',
          time: '2小时前',
          title: '银行理财产品收益率小幅回落，存款利率仍保持稳定',
          summary: '市场资金环境趋稳，理财产品结构持续优化。'
        }
      ]
    }
  }
}
</script>

<style scoped>
.page {
  min-height: 100vh;
  background: #f5f7fb;
  padding: 16px;
}

.header {
  margin-bottom: 16px;
}

.title {
  display: block;
  font-size: 22px;
  font-weight: 700;
  color: #121212;
  margin-bottom: 4px;
}

.subtitle {
  font-size: 13px;
  color: #7a7a7a;
}

.news-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.news-card {
  background: #ffffff;
  border-radius: 12px;
  padding: 14px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
}

.news-top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 8px;
}

.tag {
  font-size: 12px;
  color: #0f7ae5;
  background: #eaf4ff;
  padding: 2px 8px;
  border-radius: 999px;
}

.time {
  font-size: 12px;
  color: #999999;
}

.news-title {
  display: block;
  font-size: 16px;
  font-weight: 600;
  color: #222222;
  margin-bottom: 6px;
}

.news-summary {
  font-size: 13px;
  color: #666666;
  line-height: 1.5;
}
</style>