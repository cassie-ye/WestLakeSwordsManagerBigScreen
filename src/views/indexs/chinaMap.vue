<!--
 * @Author: daidai
 * @Date: 2022-03-01 11:17:39
 * @LastEditors: Please set LastEditors
 * @LastEditTime: 2022-09-29 15:50:18
 * @FilePath: \web-pc\src\pages\big-screen\view\indexs\center-map.vue
-->
<template>
  <!-- <div class="centermap"> -->
  <!-- <div class="maptitle">
      <div class="zuo"></div>
      <span class="titletext">{{ maptitle }}</span>
      <div class="you"></div>
    </div> -->
  <div class="mapwrap">
    <!-- <dv-border-box-13> -->
    <div class="quanguo" @click="getData('china')" v-if="code !== 'china'">
      中国
    </div>
    <p class="zhanshang">展商分布图</p>

    <Echart id="CenterMap" :options="options" ref="CenterMap" />
    <!-- </dv-border-box-13> -->
  </div>
  <!-- </div> -->
</template>

<script>
// 提供中国行政区的代码（adcode）信息
// import xzqCode from "../../utils/map/xzqCode";
// GET请求 currentGET 传入两个参数 路径和params
import { currentGET } from "api/modules";
// 引入echarts
import * as echarts from "echarts";
// 没有基地址的GET请求
import { GETNOBASE } from "api";
export default {
  data() {
    return {
      maptitle: "设备分布图",
      options: {},
      code: "china", //china 代表中国 其他地市是行政编码
      echartBindClick: false,
      isSouthChinaSea: false, //是否要展示南海群岛  修改此值请刷新页面
    };
  },
  created() { },

  mounted() {
    this.getData("china");
  },
  methods: {
    getData(code) {
      currentGET("big8", { regionCode: code }).then((res) => {
        if (res.success) {
          console.log("设备分布", res);
          this.getGeojson(res.data.regionCode, res.data.dataList);
          // this.mapclick();
        } else {
          this.$Message.warning(res.msg);
        }
      });
    },
    /**
     * @description: 获取地图的 GeoJSON 数据，并根据这些数据进行一些处理和初始化
     * @param {*} name china 表示中国 其他省份行政区编码
     * @param {*} mydata 接口返回列表数据
     * @return {*}
     */
    async getGeojson(name, mydata) {
      // 设置地图名称
      this.code = name;
      console.log('this.code',this.code)
      // 处理南海的特殊情况
      let geoname = name;
      if (this.isSouthChinaSea && name == "china") {
        geoname = "chinaNanhai";
      }
      // 获取或加载地图 JSON 数据
      let mapjson = echarts.getMap(name);
      if (mapjson) {
        mapjson = mapjson.geoJSON;
      } else {
        mapjson = await GETNOBASE(`./map-geojson/${geoname}.json`).then(
          (res) => {
            return res;
          }
        );
        echarts.registerMap(name, mapjson);
      }
      let cityCenter = {};
      let arr = mapjson.features;
      console.log('arrrrr',arr)
      arr.map((item) => {
        cityCenter[item.properties.name] =
          item.properties.centroid || item.properties.center;
      });
      console.log('arr',arr)
      let newData = [];
      mydata.map((item) => {
        if (cityCenter[item.name]) {
          newData.push({
            name: item.name,
            value: cityCenter[item.name].concat(item.value),
          });
        }
      });
      console.log('newData',newData)
      mydata = [
        { name: "江苏省", value: 2 },
        { name: "广东省", value: 277 },
        { name: "浙江省", value: 888 },
        { name: "北京市", value: 87 },
      ]
      newData = [
        {
          name: "江苏省",
          value: [119.486506, 32.983991, 2],
        },
        {
          name: "广东省",
          value: [113.429919, 23.334643, 277],
        },
        {
          name: "浙江省",
          value: [120.109913, 29.181466, 8],
        },
        {
          name: "北京市",
          value: [116.41995, 40.18994, 88]
        }
      ];
      this.init(name, mydata, newData);
    },
    init(name, data, data2) {
      // console.log(data2);
      let top = 40;
      let zoom = 1.2;
      let option = {
        backgroundColor: "rgba(0,0,0,0)",
        tooltip: {
          show: false,
        },
        legend: {
          show: false,
        },
        visualMap: {
          left: 0,
          bottom: 20,
          pieces: [
            { gte: 10, label: "10个以上" }, // 不指定 max，表示 max 为无限大（Infinity）。
            { gte: 6, lte: 10, label: "6-10个" },
            { gte: 2, lte: 5, label: "2-5个" },
            { lte: 1, label: "1个" }, // 不指定 min，表示 min 为无限大（-Infinity）。
          ],
          inRange: {
            // 渐变颜色，从小到大
            color: [
              "#c3d7df",
              "#5cb3cc",
              "#8abcd1",
              "#66a9c9",
              "#2f90b9",
              "#1781b5",
            ],
          },
          textStyle: {
            color: "#fff",
          },
        },
        geo: {
          map: name,
          roam: false,
          selectedMode: false, //是否允许选中多个区域
          zoom: zoom,
          top: top,
          // aspectScale: 0.78,
          show: false,
        },
        series: [
          {
            name: "MAP",
            type: "map",
            map: name,
            // aspectScale: 0.78,
            data: data,
            // data: [1,100],
            selectedMode: false, //是否允许选中多个区域
            zoom: zoom,
            geoIndex: 1,
            top: top,
            tooltip: {
              show: true,
              formatter: function (params) {
                if (params.data) {
                  return params.name + "：" + params.data["value"];
                } else {
                  return params.name;
                }
              },
              backgroundColor: "rgba(0,0,0,.6)",
              borderColor: "rgba(147, 235, 248, .8)",
              textStyle: {
                color: "#FFF",
              },
            },
            label: {
              show: false,
              color: "#000",
              // position: [-10, 0],
              formatter: function (val) {
                // console.log(val)
                if (val.data !== undefined) {
                  return val.name.slice(0, 2);
                } else {
                  return "";
                }
              },
              rich: {},
            },
            emphasis: {
              label: {
                show: false,
              },
              itemStyle: {
                areaColor: "#389BB7",
                borderWidth: 1,
              },
            },
            itemStyle: {
              borderColor: "rgba(147, 235, 248, .8)",
              borderWidth: 1,
              areaColor: {
                type: "radial",
                x: 0.5,
                y: 0.5,
                r: 0.8,
                colorStops: [
                  {
                    offset: 0,
                    color: "rgba(147, 235, 248, 0)", // 0% 处的颜色
                  },
                  {
                    offset: 1,
                    color: "rgba(147, 235, 248, .2)", // 100% 处的颜色
                  },
                ],
                globalCoord: false, // 缺为 false
              },
              shadowColor: "rgba(128, 217, 248, .3)",
              shadowOffsetX: -2,
              shadowOffsetY: 2,
              shadowBlur: 10,
            },
          },
          {
            data: data2,
            type: "effectScatter",
            coordinateSystem: "geo",
            symbolSize: function (val) {
              return 4;
              // return val[2] / 50;
            },
            legendHoverLink: true,
            showEffectOn: "render",
            rippleEffect: {
              // period: 4,
              scale: 6,
              color: "rgba(255,255,255, 1)",
              brushType: "fill",
            },
            tooltip: {
              show: true,
              formatter: function (params) {
                if (params.data) {
                  return params.name + "：" + params.data["value"][2];
                } else {
                  return params.name;
                }
              },
              backgroundColor: "rgba(0,0,0,.6)",
              borderColor: "rgba(147, 235, 248, .8)",
              textStyle: {
                color: "#FFF",
              },
            },
            label: {
              formatter: (param) => {
                return param.name.slice(0, 2);
              },

              fontSize: 11,
              offset: [0, 2],
              position: "bottom",
              textBorderColor: "#fff",
              textShadowColor: "#000",
              textShadowBlur: 10,
              textBorderWidth: 0,
              color: "#FFF",
              show: true,
            },
            // colorBy: "data",
            itemStyle: {
              color: "rgba(255,255,255,1)",
              borderColor: "rgba(2255,255,255,2)",
              borderWidth: 4,
              shadowColor: "#000",
              shadowBlur: 10,
            },
          },
        ],
        //动画效果
        // animationDuration: 1000,
        // animationEasing: 'linear',
        // animationDurationUpdate: 1000
      };
      this.options = option;
    },
    // message(text) {
    //   this.$Message({
    //     text: text,
    //     type: "warning",
    //   });
    // },
    // mapclick() {
    //   if (this.echartBindClick) return;
    //   //单击切换到级地图，当mapCode有值,说明可以切换到下级地图
    //   this.$refs.CenterMap.chart.on("click", (params) => {
    //     // console.log(params);
    //     let xzqData = xzqCode[params.name];
    //     if (xzqData) {
    //       this.getData(xzqData.adcode);
    //     } else {
    //       this.message("暂无下级地市!");
    //     }
    //   });
    //   this.echartBindClick = true;
    // },
  },
};
</script>
<style lang="scss" scoped>
.centermap {
  // margin-bottom: 30px;
  height: 250px;
}

.zhanshang {
  position: absolute;
  left: 10px;
  top: 25px;
  color: #00eded;
  font-size: 16px;
}

.mapwrap {
  padding-top: -30px;
  position: relative;
  height: 330px;
  width: 100%;
  // padding: 0 0 10px 0;
  box-sizing: border-box;
  position: relative;

  .quanguo {
    position: absolute;
    right: 20px;
    top: 0px;
    width: 80px;
    height: 28px;
    border: 1px solid #00eded;
    border-radius: 10px;
    color: #00f7f6;
    text-align: center;
    line-height: 26px;
    letter-spacing: 6px;
    cursor: pointer;
    box-shadow: 0 2px 4px rgba(0, 237, 237, 0.5), 0 0 6px rgba(0, 237, 237, 0.4);
  }
}
</style>
