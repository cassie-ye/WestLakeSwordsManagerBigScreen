<template>
  <div class="hello">
    <div>
      <wordcloud
        :data="defaultWords"
        nameKey="name"
        valueKey="value"
        :color="myColors"
        :showTooltip="false"
        :wordClick="wordClickHandler"
        :fontSize="fontSize"
        style="height: 250px"
      >
      </wordcloud>
    </div>
  </div>
</template>
<script>
import wordcloud from "vue-wordcloud";
export default {
  components: {
    wordcloud,
  },
  methods: {
    wordClickHandler(name, value, vm) {
      console.log("wordClickHandler", name, value, vm);
    },
  },
  data() {
    return {
      myColors: [
        "#03EDFC",
        "#F9369B",
        "#EDE046",
        "#06F9AA",
        "#9D76FF",
        "#FEFEFE",
        "#FF003E",
        "#0040FF",
        "#B72597",
        "#29FC29",
        "#00DBFF",
        "#03EDFC",
        "#F9369B",
        "#EDE046",
        "#06F9AA",
        "#9D76FF",
        "#FEFEFE",
        "#FF003E",
        "#0040FF",
        "#B72597",
        "#29FC29",
        "#00DBFF",
      ],
      fontSize: [10, 50],
      defaultWords: [
        {
          name: "网络安全",
          value: 100,
        },
        {
          name: "大数据",
          value: 90,
        },
        {
          name: "人工智能",
          value: 80,
        },
        {
          name: "信息安全",
          value: 86,
        },
        {
          name: "工业互联网",
          value: 77,
        },
        {
          name: "金融安全",
          value: 78,
        },
        {
          name: "智慧城市",
          value: 65,
        },
        {
          name: "物联网安全",
          value: 61,
        },
        {
          name: "云计算",
          value: 59,
        },
        {
          name: "Web应用防护",
          value: 55,
        },
        {
          name: "防火墙",
          value: 78,
        },
        {
          name: "加密",
          value: 78,
        },
        {
          name: "杭州西湖",
          value: 78,
        },
        {
          name: "西湖论剑",
          value: 78,
        },
        {
          name: "网络攻击",
          value: 78,
        },
        {
          name: "奋进十年",
          value: 78,
        },
        {
          name: "数智时代",
          value: 78,
        },
        {
          name: "安恒信息",
          value: 78,
        },
        {
          name: "格致论道",
          value: 78,
        },
        {
          name: "安恒小龙人",
          value: 78,
        },
        {
          name: "中国杭州",
          value: 78,
        },
      ],
    };
  },
};
</script>
<style scoped>
.hello {
  height: 250px;
}
</style>
