<!--
 * @Author: daidai
 * @Date: 2022-02-28 16:16:42
 * @LastEditors: Please set LastEditors
 * @LastEditTime: 2022-10-25 09:18:22
 * @FilePath: \web-pc\src\pages\big-screen\view\indexs\left-center.vue
-->
<template>
  <Echart id="leftCenter" :options="options" class="left_center_inner" v-if="pageflag" ref="charts" />
  <Reacquire v-else @onclick="getData" style="line-height:200px">
    重新获取
  </Reacquire>
</template>

<script>
import { currentGET } from 'api/modules'
export default {
  data() {
    return {
      options: {},
      countUserNumData: {
        lockNum: 0,
        onlineNum: 0,
        offlineNum: 0,
        totalNum: 0
      },
      pageflag: true,
      timer: null
    };
  },
  created() {
    this.getData()
  },
  mounted() {
  },
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
    getData() {
      this.pageflag = true
      // this.pageflag =false

      currentGET('big1').then(res => {
        //只打印一次
        if (!this.timer) {
          console.log("设备总览", res);
        }
        if (res.success) {
          this.countUserNumData = res.data
          this.$nextTick(() => {
            this.init()
          })

        } else {
          this.pageflag = false
          this.$Message({
            text: res.msg,
            type: 'warning'
          })
        }
      })
    },
    //轮询
    switper() {
      if (this.timer) {
        return
      }
      let looper = (a) => {
        this.getData()
      };
      this.timer = setInterval(looper, this.$store.state.setting.echartsAutoTime);
      let myChart = this.$refs.charts.chart
      myChart.on('mouseover', params => {
        this.clearData()
      });
      myChart.on('mouseout', params => {
        this.timer = setInterval(looper, this.$store.state.setting.echartsAutoTime);
      });
    },
    init() {
      // 总数220
      let total = 220;
      let colors = ["#06F9AA","#EDE046"];
      let piedata = {
        name: "用户总览",
        type: "pie",
        radius: ["50%", "65%"],
        avoidLabelOverlap: false,
        itemStyle: {
          borderRadius: 4,
          borderColor: "rgba(0,0,0,0)",
          borderWidth: 2,
        },

        color: colors,
        data: [
          // {
          //   value: 0,
          //   name: "告警",
          //   label: {
          //     shadowColor: colors[0],
          //   },
          // },
          {
            value: 89,
            name: "Web端注册",
            label: {
              shadowColor: colors[0],
            },
          },
          {
            value: 31,
            name: "小程序注册",
            label: {
              shadowColor: colors[2],
            },
          },



        ],
      };
      this.options = {
        title: {
          // zlevel: 0,
          text: ["{value|" + total + "}", "{name|总数}"].join("\n"),
          top: "center",
          left: "center",
          textStyle: {
            rich: {
              value: {
                color: "#ffffff",
                fontSize: 24,
                fontWeight: "bold",
                lineHeight: 20,
              },
              name: {
                color: "#ffffff",
                lineHeight: 20,
              },
            },
          },
        },
        tooltip: {
          trigger: "item",
          backgroundColor: "rgba(0,0,0,.6)",
          borderColor: "rgba(147, 235, 248, .8)",
          textStyle: {
            color: "#FFF",
          },
        },
        legend: {
          show: false,
          top: "5%",
          left: "center",
        },
        series: [
          //展示圆点
          {
            ...piedata,
            tooltip: { show: true },
            label: {
              formatter: "   {b|{b}}   \n   {c|{c}人}   {per|{d}%}  ",
              //   position: "outside",
              rich: {
                b: {
                  color: "#fff",
                  fontSize: 12,
                  lineHeight: 26,
                },
                c: {
                  color: "#31ABE3",
                  fontSize: 14,
                },
                per: {
                  color: "#31ABE3",
                  fontSize: 14,
                },
              },
            },
            labelLine: {
              length: 20, // 第一段线 长度
              length2: 36, // 第二段线 长度
              show: true,
            
            },
              emphasis: {
                show: true,
              },
          },
          {
            ...piedata,
            tooltip: { show: true },
            itemStyle: {},
            label: {
              backgroundColor: "inherit", //圆点颜色，auto：映射的系列色
              height: 0,
              width: 0,
              lineHeight: 0,
              borderRadius: 2.5,
              shadowBlur: 8,
              shadowColor: "auto",
              padding: [2.5, -2.5, 2.5, -2.5],
            },
            labelLine: {
              length: 20, // 第一段线 长度
              length2: 36, // 第二段线 长度
              show: false,
            },
          },
        ],
      };
    },
  },
};
</script>
<style lang='scss' scoped>
.left_center_inner{
  // background-color: red;
  height: 180px !important;
  margin-top: 5px;
}
</style>