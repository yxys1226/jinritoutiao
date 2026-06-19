<template>
  <view class="page">
    <view class="header">
      <text class="title">体育新闻</text>
      <text class="subtitle">关注赛场焦点、球员动态与赛事快讯</text>
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
          tag: '足球',
          time: '8分钟前',
          title: '本轮联赛再现爆发式进球大战，争冠格局更加激烈',
          summary: '多场比赛都出现高质量对攻，球迷们对接下来的比赛期待值持续上升。'
        },
        {
          id: 2,
          tag: '篮球',
          time: '25分钟前',
          title: '主力球员回归后球队连胜，整体战术更加顺畅',
          summary: '球队在防守端做出调整，近期状态明显提升。'
        },
        {
          id: 3,
          tag: '综合',
          time: '1小时前',
          title: '国际比赛日迎来多项高水平赛事，观赛热度持续走高',
          summary: '世界各地赛事同步开打，体育内容消费持续增长。'
        },
        {
          id: 4,
          tag: '赛事',
          time: '2小时前',
          title: '新赛季联赛日程公布，球迷抢先预订观赛套餐',
          summary: '各大平台同步推出赛事直播和精彩集锦内容。'
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
  color: #ff6a00;
  background: #fff2e8;
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