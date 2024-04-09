<!--
 * @Author: daidai
 * @Date: 2022-03-01 15:27:58
 * @LastEditors: Please set LastEditors
 * @LastEditTime: 2022-05-07 11:24:14
 * @FilePath: \web-pc\src\pages\big-screen\view\indexs\right-center.vue
-->
<template>
  <div v-if="pageflag" class="right_center_wrap beautify-scroll-def" :class="{ 'overflow-y-auto': !sbtxSwiperFlag }">
    <component :is="components" :data="list" :class-option="defaultOption">
      <ul class="right_center ">
        <li class="right_center_item" v-for="(item, i) in 8" :key="i">
          <div class="inner_right">
            <div class="dibu"></div>
            <div class="flex">
              <div class="info">
                <span class="labels ">直播名称：</span>
                <span class="contents zhuyao"> 格致论道</span>
              </div>
              <div class="info">
                <span class="labels">观看人数：</span>
                <span class="contents " style="color: greenyellow;"> 328472398</span>
              </div>
              <div class="info">
                <span class="labels">点赞量：</span>
                <span class="contents warning"> 4738434</span>
              </div>
            </div>


            <div class="flex">

              <div class="info">
                <span class="labels">评论数：</span>
                <span class="contents ciyao" style="font-size:12px;color: #7E43F7;">43535</span>
              </div>
              <div class="info time">
                <span class="labels">时间：</span>
                <span class="contents" style="font-size:12px">2024-04-09 9：30-11：30</span>
              </div>

            </div>
            <div class="flex">

              <div class="info">
                <span class="labels">热度：</span>
                <span class="contents ciyao" style="color: red;"> 5438574</span>
              </div>
            </div>
          </div>
        </li>
      </ul>
    </component>
  </div>
  <Reacquire v-else @onclick="getData" style="line-height:200px" />

</template>

<script>
import { currentGET } from 'api/modules'
import vueSeamlessScroll from 'vue-seamless-scroll'  // vue2引入方式
import Kong from '../../components/kong.vue'
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
        step:0,
      }

    };
  },
  computed: {
    sbtxSwiperFlag() {
      let ssyjSwiper = this.$store.state.setting.ssyjSwiper
      if (ssyjSwiper) {
        this.components = vueSeamlessScroll
      } else {
        this.components = Kong
      }
      return ssyjSwiper
    }
  },
  created() {
    this.getData()
  },

  mounted() { },
  methods: {
    getData() {
      this.pageflag = true
      // this.pageflag =false
      currentGET('big5', { limitNum: 50 }).then(res => {
        console.log('实时预警', res);
        if (res.success) {
          this.list = res.data.list
          let timer = setTimeout(() => {
              clearTimeout(timer)
              this.defaultOption.step=this.$store.state.setting.defaultOption.step
          }, this.$store.state.setting.defaultOption.waitTime);
        } else {
          this.pageflag = false
          this.$Message.warning(res.msg)
        }
      })
    },

  },
};
</script>
<style lang='scss' scoped>
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
        color: #E6A23C;
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