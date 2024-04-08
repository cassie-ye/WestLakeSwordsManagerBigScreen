<!--
 * @Author: daidai
 * @Date: 2022-03-01 15:51:43
 * @LastEditors: Please set LastEditors
 * @LastEditTime: 2022-09-29 15:12:46
 * @FilePath: \web-pc\src\pages\big-screen\view\indexs\right-bottom.vue
-->
<template>
  <div class="right_bottom">
    <dv-capsule-chart :config="config" style="width:100%;height:260px" />
  </div>
</template>

<script>
import { currentGET } from 'api/modules'
export default {
  data() {
    return {
      gatewayno: '',
      config: {
        showValue: true,
        unit: "次",
        data: []
      },

    };
  },
  created() {
    this.getData()

  },
  computed: {
  },
  mounted() { },
  beforeDestroy() {
    this.clearData()
  },
  methods: {
    clearData() {
      if (this.timer) {
        clearInterval(this.timer)
        this.timer = null
      }
    },
    // //轮询
    // switper() {
    //   if (this.timer) {
    //     return
    //   }
    //   let looper = (a) => {
    //     this.getData()
    //   };
    //   this.timer = setInterval(looper, this.$store.state.setting.echartsAutoTime);
    // },
    getData() {
      this.pageflag = true
      // this.pageflag =false
      currentGET('big7', { gatewayno: this.gatewayno }).then(res => {

        if (!this.timer) {
          console.log('报警排名', res);
        }
        if (res.success) {
          this.config = {
            ...this.config,
            data: [
              {
                name:"格致论道",
                value:8878
              },
              {
                name:"新·见未来",
                value:7898
              },
              {
                name:"十周年精华特刊",
                value:6780
              },
              {
                name:"安全特训营",
                value:6455
              },

              {
                name:"新品发布日",
                value:4576
              },

              {
                name:"第二直播间-1",
                value:4567
              },
              {
                name:"AI主播精彩专访",
                value:3323
              },
              {
                name:"小强实验室",
                value:2345
              },
            ]
          }
          this.switper()
        } else {
          this.pageflag = false
          this.srcList = []
          this.$Message({
            text: res.msg,
            type: 'warning'
          })
        }
      })
    },
  },
};
</script>
<style lang='scss' scoped>
.list_Wrap {
  height: 100%;
  overflow: hidden;
  :deep(.kong)   {
    width: auto;
  }
}

.sbtxSwiperclass {
  .img_wrap {
    overflow-x: auto;
  }

}

.right_bottom {
  box-sizing: border-box;
  padding: 0 16px;

  .searchform {
    height: 80px;
    display: flex;
    align-items: center;
    justify-content: center;

    .searchform_item {
      display: flex;
      justify-content: center;
      align-items: center;

      label {
        margin-right: 10px;
        color: rgba(255, 255, 255, 0.8);
      }

      button {
        margin-left: 30px;
      }

      input {}
    }
  }

  .img_wrap {
    display: flex;
    // justify-content: space-around;
    box-sizing: border-box;
    padding: 0 0 20px;
    // overflow-x: auto;

    li {
      width: 105px;
      height: 137px;
      border-radius: 6px;
      overflow: hidden;
      cursor: pointer;
      // background: #84ccc9;
      // border: 1px solid #ffffff;
      overflow: hidden;
      flex-shrink: 0;
      margin: 0 10px;

      img {
        flex-shrink: 0;
      }
    }




  }

  .noData {
    width: 100%;
    line-height: 100px;
    text-align: center;
    color: rgb(129, 128, 128);

  }
}
</style>