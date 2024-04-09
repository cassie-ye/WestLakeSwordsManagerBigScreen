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
          },
          legend: {
            data: [ "热度"],
            textStyle: {
              color: "#B4B4B4",
            },
            top: "0",
            right:'0px'
          },
          grid: {
            left: "50px",
            right: "40px",
            bottom: "30px",
            top: "20px",
          },
          xAxis: {
            data: ['好物商城','积分抽奖','拍照打卡','个性化定制海报','趣味答题','热点话题讨论'],
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
              name: "热度",
              type: "bar",
              barWidth: 30,
              itemStyle: {
                borderRadius: 5,
                color: new graphic.LinearGradient(0, 0, 0, 1, [
                  { offset: 0, color: "#956FD4" },
                  { offset: 1, color: "#3EACE5" },
                ]),
              },
              data:[87970,86798,96879,76800,97088,96879],
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
  