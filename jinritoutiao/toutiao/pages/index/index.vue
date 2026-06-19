<template>
  <view>
    <!-- 分类导航栏 -->
    <view class="category-bar">
      <view @click="goToPage('sports')">体育</view>
      <view @click="goToPage('tech')">科技</view>
      <view @click="goToPage('finance')">财经</view>
    </view>

    <!-- 新闻列表 -->
    <scroll-view 
      scroll-y 
      class="scroll-container" 
      @scroll="onScroll"
      :scroll-top="scrollTopValue"
      :scroll-with-animation="true"
    >
      <view class="news-list">
        <view 
          id="first-news"
          class="news-item"
          v-for="(news, index) in newsList" 
          :key="index"
          @click="goToNewsDetail(news)"
        >
          <!-- 每条新闻都带图片 -->
          <view class="news-with-image">
            <view class="news-content">
              <!-- 第一条新闻使用大标题样式 -->
              <text v-if="index === 0" class="news-title-large">{{ news.title }}</text>
              <text v-else class="news-title">{{ news.title }}</text>
              <text class="news-summary">{{ news.summary }}</text>
              <view class="news-footer">
                <text class="news-source">{{ news.source }}</text>
                <text class="news-date">{{ news.date }}</text>
                <text v-if="news.comments" class="news-comments">{{ news.comments }}条评论</text>
              </view>
            </view>
            <image class="news-image" :src="news.thumbnail" mode="aspectFill"></image>
          </view>
        </view>
      </view>
    </scroll-view>

    <!-- 返回顶部按钮 -->
    <view 
      class="back-to-top" 
      @click="scrollToTop"
      v-show="showBackTop"
    >
      <view class="arrow-circle">
        <text class="arrow-up">↑</text>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      scrollTopValue: 0,
      showBackTop: false,
      navBarHeight: 0,
      newsList: [
        {
          id: 1,
          title: '党的七大记（伟大征程）',
          summary: '陕西延安，杨家岭革命旧址，中央大礼堂巍峨挺立。1945年4月23日，中国共产党第七次全国代表大会在此隆重召开...',
          content: `党的七大记（伟大征程）
2026-06-13 09:15·人民网

青年们在杨家岭中央大礼堂参加研学活动。（加向前 摄）

陕西延安，杨家岭革命旧址，中央大礼堂巍峨挺立。1945年4月23日，中国共产党第七次全国代表大会在此隆重召开。

习近平总书记指出："党的七大在党的历史上具有重要里程碑意义，标志着我们党在政治上思想上组织上走向了成熟。""党的七大在党的历史上具有极其重要的地位，为党后来不断从胜利走向胜利指明了正确方向、开辟了正确道路。"

条桌、木椅、红旗……走进中央大礼堂，陈设简朴而庄重，高悬主席台上方的一行红色标语格外醒目："在毛泽东的旗帜下胜利前进"。

在炮火与硝烟里，755名代表从革命根据地、从国统区、从沦陷区，冲破重重封锁、跋山涉水而来。

会上，毛泽东致开幕词，向大会提交《论联合政府》政治报告并作口头报告。朱德作《论解放区战场》的军事报告，刘少奇作《关于修改党章的报告》，周恩来作《论统一战线》的发言。

会议一直开到了当年的6月11日。一次"团结的大会，胜利的大会"，载入党的史册。

党的七大把党在长期奋斗中形成的优良作风概括为三大作风，即理论和实践相结合的作风，和人民群众紧密地联系在一起的作风，自我批评的作风；立足实际，确定"放手发动群众，壮大人民力量，在我党的领导下，打败日本侵略者，解放全国人民，建立一个新民主主义的中国"的政治路线；制定了新民主主义国家在政治、经济、文化方面的纲领，提出了实现中国工业化的宏伟任务。

在政治上，党通过延安整风，使全党团结在毛泽东的旗帜下，实现了党的空前统一和团结。在思想上，党确立了毛泽东思想在全党的指导地位，把毛泽东思想写入了党章。在组织上，党形成了一支高举毛泽东旗帜的久经考验的政治家集团。

从杨家岭发出的时代号角，迅速传遍敌后各个抗日战场，广大军民统一思想、鼓足干劲，成为夺取抗战最后胜利的强大精神动力。

岁月流转，烽火远去，中央大礼堂里红色的旗、红色的字，历经岁月洗礼愈加夺目。

党的二十大闭幕不到一周，习近平总书记来到延安革命纪念馆，满怀深情地说："我在延安地区生活劳动了7年，我的父辈也是从这里走出去的，我对这里十分熟悉。当年在陕北插队的时候，每次路过延安，我都要来七大会址、杨家岭、枣园、凤凰山等革命旧址看一看。""这次和中央政治局常委同志一起来，就是要宣示新一届中央领导集体将继承和发扬延安时期党形成的优良革命传统和作风，弘扬延安精神。"

近年来，常态化红色研学让更多人走进历史现场、感受精神脉动。全国各地党政机关、大中小学、企事业单位人员络绎奔赴杨家岭，在杨家岭开展现场党课；不少老党员、党史专家担任志愿宣讲员，结合史料考证，讲述党的七大胜利召开的重大意义；研学队伍认真参观聆听，重温峥嵘岁月，感悟赤诚初心。

2025年12月，西安至延安高铁正式开通，陕北革命老区从此迈入"高铁时代"。越来越多的人走进延安革命纪念地，走进杨家岭中央大礼堂。

"我们将进一步讲好党的七大故事，面向广大干部群众弘扬延安精神，把历史沉淀的精神财富转化为干事创业的实际行动。"杨家岭革命旧址管理处主任侯振龙说。

延安精神，代代传承。

本报记者 贾丰丰`,
          source: '人民网',
          date: '2026-06-13 09:15',
          thumbnail: 'https://picsum.photos/id/104/200/140',  // 风景占位图
          detailImage: 'https://picsum.photos/id/104/750/400'
        },
        {
          id: 2,
          title: '活力中国调研行丨"人造太阳"能发电吗？"中关村两院"企业用AI挑战能源终极之问',
          summary: '6月11日，记者跟随2026年"活力中国调研行"北京主题采访活动来到北京中关村学院与中关村人工智能研究院，AI在这里正在被赋予更强的能力...',
          content: `活力中国调研行丨"人造太阳"能发电吗？"中关村两院"企业用AI挑战能源终极之问
2026-06-14 14:57·环球网
来源：科技日报

科技日报记者 张佳星 陈瑜

6月11日，记者跟随2026年"活力中国调研行"北京主题采访活动来到北京中关村学院与中关村人工智能研究院（简称"中关村两院"），AI在这里正在被赋予更强的能力。中关村两院能源科学方向负责人，新烛时代联合创始人兼CTO汪跃介绍，团队构建了"物理+数据"双轮驱动的技术内核，依托强化学习、生成式模型、自进化智能体等前沿能力，试图通过AI对可控核聚变的快速诊断、等离子体预测、不稳定性控制等问题的破解实现加速和赋能。

据了解，中国EAST"人造太阳"实现了1亿摄氏度1066秒高约束模式等离子体运行。"人造太阳"即可控核聚变装置，等离子体在其中以极端条件长时间稳定"燃烧"。为了获得足够的聚变功率，需要同时提高温度、密度和约束时间，但这些要求会把等离子体推向不稳定状态。

汪跃解释，AI与能源是当下相辅相成共同驱动时代发展的动力，AI的发展竞争，本质上比拼的是能源供给；而可控核聚变这类终极能源的技术突破，同样离不开AI技术的赋能。在聚变这种高度复杂的工业场景里，过往的工程突破大多依赖行业专家依靠人工经验反复试错，不仅效率低下，也越来越难以应对日渐复杂多变的聚变工况。

团队通过拆解聚变应用场景与AI底层技术要素，提炼出可复用的通用技术模块，再依托智能体技术，融合生成式AI代理模型、强化学习、物理信息神经网络等前沿AI能力，结合仿真数据与实地实测数据，训练基础基座模型以及行业专用模型，能够快速实现等离子体诊断、状态预判、破裂预警、实时调控以及实验规划设计等落地应用。

团队最终目标是搭建面向聚变领域的专属智能操作系统与通用智能体，推动聚变控制模式从依靠人工经验试错，转变为智能预测、主动干预调控，以此加快可控核聚变稳定商业化运行的落地进程。未来，一旦可控核聚变的运行稳定性能够对标化石能源与现有新能源，就可以常态化向社会输送清洁电力。

不久前，由北京中关村学院与中关村人工智能研究院联合孵化的企业新烛时代凭借专业实力和先锋探索获得了由中科创星、鼎峰科创联合领投，水木清华校友基金跟投的天使轮融资。

（受访者供图）

【采访同期】
京能数产技术负责人 田鹏伟："你看这条线我们的算力峰值利用率现在快冲到100%了"`,
          source: '环球网/科技日报',
          date: '2026-06-14 14:57',
          thumbnail: 'https://picsum.photos/id/0/200/140',   // 科技占位图
          detailImage: 'https://picsum.photos/id/0/750/400',
         
        },
        {
          id: 3,
          title: '以军密集行动，24小时打击70多个真主党军事目标；伊朗外长早前表态：绝不会让黎巴嫩孤立无援',
          summary: '以色列国防军13日在多份声明中表示，以军持续在黎巴嫩南部展开军事行动，对黎真主党军事基础设施和武装人员实施打击...',
          content: `以军密集行动，24小时打击70多个真主党军事目标；伊朗外长早前表态：绝不会让黎巴嫩孤立无援
2026-06-14 16:00·环球时报

以色列国防军13日在多份声明中表示，以军持续在黎巴嫩南部展开军事行动，对黎真主党军事基础设施和武装人员实施打击。

声明说，过去一周，以军在黎南部发现一条真主党使用的地下通道。以军打死7名在这条地下通道活动的真主党武装人员。

以军在另一份声明中称，过去24小时，以军在黎南部打击了70多个真主党军事目标，其中包括用于对以方发动袭击的发射装置和建筑物。同时，以军在黎南部打死多名真主党人员。

当日早些时候，以方在社交媒体上发布撤离令，警告对黎巴嫩发动空袭，要求黎巴嫩20个地区的居民立即撤离。

以色列国防部长卡茨12日发表声明称，以色列不会从其在黎巴嫩、叙利亚和加沙地带占领的所谓"安全区"撤军。

据伊朗媒体12日报道，伊朗外长阿拉格齐当天表示，磋商中的伊美谅解备忘录规定在所有战线止战，包括黎巴嫩境内战线。他表示，"我们绝不会让黎巴嫩孤立无援"。

来源：新华社`,
          source: '环球时报/新华社',
          date: '2026-06-14 16:00',
          thumbnail: 'https://picsum.photos/id/96/200/140',  // 军事占位图
          detailImage: 'https://picsum.photos/id/96/750/400'
        },
        {
          id: 4,
          title: '主场胜平潭队，积分一马当先 厦门队七连胜',
          summary: '13日，"闽超"常规赛第七轮赛事火热开赛，厦门队坐镇主场迎战平潭队，本场比赛吸引25018名球迷现场助威...',
          content: `主场胜平潭队，积分一马当先 厦门队七连胜
2026-06-14 12:35·闽南网

厦门队与平潭队激烈交战。

13日，"闽超"常规赛第七轮赛事火热开赛，厦门队坐镇主场迎战平潭队，本场比赛吸引25018名球迷现场助威。最终，厦门队凭借全员出色发挥，以7∶0战胜对手，斩获联赛七连胜，同时创下本赛季"闽超"开赛以来最大分差纪录。

比赛伊始，厦门队迅速进入状态，掌控赛场节奏，在进攻端频频制造威胁。第15分钟，其右路突破传中打乱对方防线，7号周祺左路接球后冷静兜射破门，率先打破僵局，以1∶0领先。第25分钟，35号孙景濠接队友传中，晃开防守后左脚劲射得分，将比分扩大为2∶0。第41分钟，球队禁区外远射折射后，孙景濠抓住机会单刀破门完成梅开二度，比分改写为3∶0。上半场补时阶段，孙景濠再接后场长传突入禁区推射得分，以4∶0的大比分结束上半场争夺。

易边再战，厦门队进攻火力依旧凶猛。第56分钟，替补登场的36号吕家晟门前包抄推射破门。第66分钟，首次代表厦门队登场的2号林天赐扣过防守球员推射得分。第75分钟，23号薛凯文头球破门，将比分定格为7∶0。

（福建日报记者 黄星榕 林梓健 文／图）

来源：福建日报`,
          source: '闽南网/福建日报',
          date: '2026-06-14 12:35',
          thumbnail: 'https://picsum.photos/id/26/200/140',  // 体育占位图
          detailImage: 'https://picsum.photos/id/26/750/400'
        },
        {
          id: 5,
          title: '日本多地发布疫情警报',
          summary: '据新华社，日本卫生机构最新发布的数据显示，日本手足口病患者最近数周持续增加，今年以来已有超过1万人确诊...',
          content: `日本多地发布疫情警报
2026-06-14 14:58·世界闽南人

据新华社，日本卫生机构最新发布的数据显示，日本手足口病患者最近数周持续增加，今年以来已有超过1万人确诊。鹿儿岛县、宫崎县、福冈县等6个县已就本轮疫情发出警报，较往年有所提前。

日本媒体援引国立健康危机管理研究机构的数据报道，5月25日至31日一周内，全国47个都道府县中，有6个县的定点医疗机构收治的手足口病患者数量超过警戒值。

今年以来，日本全国手足口病确诊病例累计达1.16万。其中，福冈县情况最为严重，患者数量为1295人，宫崎县、鹿儿岛县的病例数均超过1000人。

来源：中国新闻网`,
          source: '世界闽南人/中国新闻网',
          date: '2026-06-14 14:58',
          thumbnail: 'https://picsum.photos/id/180/200/140',  // 健康占位图
          detailImage: 'https://picsum.photos/id/180/750/400'
        }
      ]
    }
  },
  mounted() {
    this.getNavBarHeight()
  },
  methods: {
    goToPage(type) {
      if (type === 'sports') {
        uni.navigateTo({ url: '/pages/sports/sports' })
      } else if (type === 'tech') {
        uni.navigateTo({ url: '/pages/tech/tech' })
      } else if (type === 'finance') {
        uni.navigateTo({ url: '/pages/finance/finance' })
      }
    },
    goToNewsDetail(news) {
      uni.setStorageSync('currentNews', news)
      uni.navigateTo({
        url: `/pages/news-detail/news-detail?id=${news.id}`
      })
    },
    getNavBarHeight() {
      const query = uni.createSelectorQuery().in(this)
      query.select('.category-bar').boundingClientRect(data => {
        if (data) {
          this.navBarHeight = data.height
        }
      }).exec()
    },
    onScroll(e) {
      const query = uni.createSelectorQuery().in(this)
      query.select('#first-news').boundingClientRect(data => {
        if (data) {
          const isFirstNewsOut = data.bottom <= this.navBarHeight
          this.showBackTop = isFirstNewsOut
        }
      }).exec()
    },
    scrollToTop() {
      this.scrollTopValue = -1
      this.$nextTick(() => {
        this.scrollTopValue = 0
      })
      setTimeout(() => {
        uni.pageScrollTo({
          scrollTop: 0,
          duration: 300
        })
      }, 10)
    }
  }
}
</script>

<style>
.category-bar {
  display: flex;
  justify-content: space-around;
  padding: 20rpx;
  background: #fff;
  border-bottom: 1px solid #f0f0f0;
  position: sticky;
  top: 0;
  z-index: 99;
}
.category-bar view {
  font-size: 32rpx;
  color: #333;
}

.scroll-container {
  height: calc(100vh - 90rpx);
}

.news-list {
  background: #fff;
  padding: 0 30rpx;
}

.news-item {
  padding: 30rpx 0;
  border-bottom: 1px solid #f0f0f0;
}

/* 第一条新闻大标题样式 */
.news-title-large {
  font-size: 44rpx;
  font-weight: bold;
  color: #222;
  display: block;
  margin-bottom: 12rpx;
  line-height: 1.3;
}

/* 普通标题 */
.news-title {
  font-size: 34rpx;
  font-weight: bold;
  color: #333;
  display: block;
  margin-bottom: 16rpx;
  line-height: 1.4;
}

.news-summary {
  font-size: 28rpx;
  color: #666;
  display: block;
  margin-bottom: 16rpx;
  line-height: 1.5;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
}

/* 带图片的新闻布局 */
.news-with-image {
  display: flex;
  justify-content: space-between;
  gap: 20rpx;
}

.news-content {
  flex: 1;
}

.news-image {
  width: 200rpx;
  height: 140rpx;
  border-radius: 12rpx;
  background-color: #f0f0f0;
  flex-shrink: 0;
}

.news-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 12rpx;
}

.news-source {
  font-size: 24rpx;
  color: #999;
}

.news-date {
  font-size: 24rpx;
  color: #999;
}

.news-comments {
  font-size: 24rpx;
  color: #ff5a5f;
}

/* 返回顶部按钮 */
.back-to-top {
  position: fixed;
  bottom: 120rpx;
  right: 30rpx;
  width: 88rpx;
  height: 88rpx;
  background-color: transparent;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 999;
}

.back-to-top:active {
  transform: scale(0.95);
}

.arrow-circle {
  width: 80rpx;
  height: 80rpx;
  border-radius: 50%;
  background-color: #ffffff;
  border: 4rpx solid #ff5a5f;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4rpx 12rpx rgba(0, 0, 0, 0.1);
}

.arrow-up {
  font-size: 44rpx;
  font-weight: bold;
  color: #ff5a5f;
  line-height: 1;
}
</style>