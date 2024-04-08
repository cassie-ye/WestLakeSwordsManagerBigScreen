<template>
  <div class="center_bottom">
    <Echart
      :options="options"
      id="bottomLeftChart"
      class="echarts_bottom"
    ></Echart>
  </div>
</template>

<script>
import { currentGET } from "api";
import { graphic } from "echarts";
export default {
  data() {
    return {
      options: {},
    };
  },
  props: {},
  mounted() {
    this.getData();
  },
  methods: {
    getData() {
      this.pageflag = true;
      currentGET("big6", { companyName: this.companyName }).then((res) => {
        // console.log("安装计划", res);
        if (res.success) {
          this.init(res.data);
        } else {
          this.pageflag = false;
          this.$Message({
            text: res.msg,
            type: "warning",
          });
        }
      });
    },
    init(newData) {
      this.options = {
        tooltip: {
          trigger: "axis",
          backgroundColor: "rgba(0,0,0,.6)",
          borderColor: "rgba(147, 235, 248, .8)",
          textStyle: {
            color: "#FFF",
          },
          // formatter: function (params) {
          //   // 添加单位
          //   var result = params[0].name + "<br>";
          //   params.forEach(function (item) {
          //     if (item.value) {
          //       if (item.seriesName == "安装率") {
          //         result +=
          //           item.marker +
          //           " " +
          //           item.seriesName +
          //           " : " +
          //           item.value +
          //           "%</br>";
          //       } else {
          //         result +=
          //           item.marker +
          //           " " +
          //           item.seriesName +
          //           " : " +
          //           item.value +
          //           "个</br>";
          //       }
          //     } else {
          //       result += item.marker + " " + item.seriesName + " :  - </br>";
          //     }
          //   });
          //   return result;
          // },
        },
        legend: {
          data: ["销售额", "销售量"],
          textStyle: {
            color: "#B4B4B4",
          },
          top: "0",
        },
        grid: {
          left: "50px",
          right: "40px",
          bottom: "30px",
          top: "20px",
        },
        xAxis: {
          data: ['成都大运会门票','杭州亚运会门票','“安恒小龙人”抱枕','2023数据安全能力洞察报告','《数据安全与隐私计算》',
        '睡眠记忆枕头','西湖论剑10周年白皮书',
        '杭州亚运会限量版POLO衫','西湖论剑大会定制背包','2023年故宫宫廷文化日历','“蓉宝”安全卫士','《数智城市》系列专刊全8册',
        '安恒小龙人','亚运会体育赛事网络安全科普套餐'
        ],
          axisLine: {
            lineStyle: {
              color: "#B4B4B4",
            },
          },
          axisTick: {
            show: false,
          },
        },
        yAxis: [
          {
            splitLine: { show: false },
            axisLine: {
              lineStyle: {
                color: "#B4B4B4",
              },
            },

            axisLabel: {
              // formatter: "{value}",
            },
          },
          {
            splitLine: { show: false },
            axisLine: {
              lineStyle: {
                color: "#B4B4B4",
              },
            },
            axisLabel: {
              // formatter: "{value}% ",
            },
          },
        ],
        series: [
          {
            name: "销售额",
            type: "line",
            smooth: true,
            showAllSymbol: true,
            symbol: "emptyCircle",
            symbolSize: 8,
            yAxisIndex: 1,
            itemStyle: {
              color: "#F02FC2",
            },
            data: [18998,18978,19900,19786,6899,14544,35998,18978,7900,8786,30899,29544,11766,6567],
          },
          // {
          //   name: "计划安装",
          //   type: "bar",
          //   barGap: "-100%",
          //   barWidth: 10,
          //   itemStyle: {
          //     borderRadius: 5,
          //     color: new graphic.LinearGradient(0, 0, 0, 1, [
          //       { offset: 0, color: "rgba(156,107,211,0.8)" },
          //       { offset: 0.2, color: "rgba(156,107,211,0.5)" },
          //       { offset: 1, color: "rgba(156,107,211,0.2)" },
          //     ]),
          //   },
          //   z: -12,
          //   data: newData.lineData,
          // },
          {
            name: "销售量",
            type: "bar",
            barWidth: 10,
            itemStyle: {
              borderRadius: 5,
              color: new graphic.LinearGradient(0, 0, 0, 1, [
                { offset: 0, color: "#956FD4" },
                { offset: 1, color: "#3EACE5" },
              ]),
            },
            data:[1257,1287,1268,1286,322,678,2711,701,655,677,1833,1333,656,555],
          },
        ],
      };
    },
  },
};
</script>
<style lang="scss" scoped>
.center_bottom {
  width: 100%;
  height: 100%;

  .echarts_bottom {
    width: 100%;
    height: 100%;
  }
}
</style>
