<!--
 * @Author: daidai
 * @Date: 2022-03-01 15:27:58
 * @LastEditors: Please set LastEditors
 * @LastEditTime: 2022-05-07 11:24:14
 * @FilePath: \web-pc\src\pages\big-screen\view\indexs\right-center.vue
-->
<template>
  <div
    v-if="pageflag"
    class="right_center_wrap beautify-scroll-def"
    :class="{ 'overflow-y-auto': !sbtxSwiperFlag }"
  >
    <component :is="components" :data="list" :class-option="defaultOption">
      <ul class="right_center">
        <li class="right_center_item" v-for="(item, i) in 8" :key="i">
          <div class="inner_right">
            <div class="dibu"></div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">格致论道@西湖论剑</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  26533</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">19</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >23</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-05 18:00-21:00</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">24752</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">95后极客青年Talk</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  4699</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">5</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >7</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-06 10:00-10:30</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">4288</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">当科幻照进现实我们会更安全吗？</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  3666</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">2</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >10</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-06 13:00-13:30</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">3409</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">人工智能会颠覆安全行业吗？</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  3210</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">4</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >28</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-06 15:00-15:30</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">3157</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">反诈直播间@西湖论剑</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  3714</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">2</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >3</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-06 15:30-16:30</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">3498</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">数字中国&安全治理论坛</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  14153</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">10</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >34</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-07 13:30-18:00</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">13471</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">信创软件供应链安全论坛</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  8989</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">7</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >13</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-07 13:30-17:10</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">8734</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">车联网安全论坛</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  8553</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">2</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >17</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-07 13:30-17:00</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">8389</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">主论坛</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  82409</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">34</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >67</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-07 09:00-12:00</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">81389</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">工业领域网络和数据安全论坛</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  9683</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">3</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >8</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-07 13:30-17:30</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">9536</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">网络安全创新发展高端论坛</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  7821</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">2</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >9</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-07 13:30-17:40</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">7475</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">企业数据安全治理论坛</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  1278</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">1</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >3</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-07 13:30-17:30</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">1157</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">独家探营.数字安全创新成果发展</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  1439</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">2</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >6</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-07 12:30-14:00</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">1187</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">生态合作伙伴分论坛</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  9256</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">4</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >12</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-07 09:00-22:00</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">9149</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">教育技术产业融合创新发展论坛</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  7471</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">12</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >26</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-08 08:30-12:10</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">7182</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">商用密码应用</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  9998</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">10</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >22</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-08 09:00-12:00</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">9339</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">MSS安全托管运营服务论坛</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  6887</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">9</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >13</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-08 13:00-18:00</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">6694</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">直播名称：</span>
                <span class="contents zhuyao">金融行业网络安全论坛</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents" style="color: greenyellow">
                  5473</span
                >
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning">7</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">评论数：</span>
                <span
                  class="contents ciyao"
                  style="font-size: 12px; color: #7e43f7"
                  >14</span
                >
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size: 12px"
                  >2023-05-08 13:30-18:00</span>
              </div>
            </div>
            <div class="flex">
              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red">5144</span>
              </div>
            </div>
          </div>
        </li>
      </ul>
    </component>
  </div>
  <Reacquire v-else @onclick="getData" style="line-height: 200px" />
</template>

<script>
import { currentGET } from "api/modules";
import vueSeamlessScroll from "vue-seamless-scroll"; // vue2引入方式
import Kong from "../../components/kong.vue";
export default {
  components: { vueSeamlessScroll, Kong },

  data() {
    return {
      list: [],
      pageflag: true,
      defaultOption: {
        ...this.$store.state.setting.defaultOption,
        limitMoveNum: 3,
        singleHeight: 250,
        step: 0,
      },
    };
  },
  computed: {
    sbtxSwiperFlag() {
      let ssyjSwiper = this.$store.state.setting.ssyjSwiper;
      if (ssyjSwiper) {
        this.components = vueSeamlessScroll;
      } else {
        this.components = Kong;
      }
      return ssyjSwiper;
    },
  },
  created() {
    this.getData();
  },

  mounted() {},
  methods: {
    getData() {
      this.pageflag = true;
      // this.pageflag =false
      currentGET("big5", { limitNum: 50 }).then((res) => {
        console.log("实时预警", res);
        if (res.success) {
          this.list = res.data.list;
          let timer = setTimeout(() => {
            clearTimeout(timer);
            this.defaultOption.step =
              this.$store.state.setting.defaultOption.step;
          }, this.$store.state.setting.defaultOption.waitTime);
        } else {
          this.pageflag = false;
          this.$Message.warning(res.msg);
        }
      });
    },
  },
};
</script>
<style lang="scss" scoped>
.right_center {
  width: 100%;
  height: 100%;

  .right_center_item {
    display: flex;
    align-items: center;
    justify-content: center;
    height: auto;
    padding: 10px;
    font-size: 14px;
    color: #fff;

    .orderNum {
      margin: 0 20px 0 -20px;
    }

    .inner_right {
      position: relative;
      height: 100%;
      width: 400px;
      flex-shrink: 0;
      line-height: 1.5;

      .dibu {
        position: absolute;
        height: 2px;
        width: 104%;
        background-image: url("../../assets/img/zuo_xuxian.png");
        bottom: -12px;
        left: -2%;
        background-size: cover;
      }
    }

    .info {
      margin-right: 10px;
      display: flex;
      align-items: center;

      .labels {
        flex-shrink: 0;
        font-size: 12px;
        color: rgba(255, 255, 255, 0.6);
      }

      .zhuyao {
        color: $primary-color;
        font-size: 15px;
      }

      .ciyao {
        color: rgba(255, 255, 255, 0.8);
      }

      .warning {
        color: #e6a23c;
        font-size: 15px;
      }
    }
  }
}

.right_center_wrap {
  overflow: hidden;
  width: 100%;
  height: 250px;
}

.overflow-y-auto {
  overflow-y: auto;
}
</style>
