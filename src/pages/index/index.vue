<template>
  <div class="container">
    <div class="wrap">
      <mpvue-echarts v-if="canvasCreated" :echarts="echarts" :onInit="onInit"/>
      <img class="canvas-img" :src="canvassrc" alt="">
    </div>
  </div>
</template>

<script>
import * as echarts from "echarts";
import mpvueEcharts from "mpvue-echarts";

export default {
  data() {
    return {
      echarts,
      onInit: this.initChart
    };
  },
  components: {
    mpvueEcharts
  },
  methods: {
    // 初始化图表组件
    initChart(canvas, width, height) {
      const chart = echarts.init(canvas, null, {
        width: width,
        height: height
      });
      canvas.setChart(chart);
      var option = {
        backgroundColor: "#fff",
        color: [],
        tooltip: {
          trigger: "axis",
          show: false // 取消鼠标经过的提示信息
        },
        legend: {
          data: []
        },
        grid: {
          containLabel: true
        },
        xAxis: {
          type: "category",
          boundaryGap: false,
          axisLine: {
            lineStyle: {
              color: "#ccc"
            }
          },
          data: ["0:00", "4:00", "8:00", "12:00", "16:00", "20:00", "24:00"]
        },
        yAxis: {
          x: "center",
          type: "value",
          min: 4000, // 坐标轴最小值
          max: 20000,
          scale: true,
          interval: 4000, // 每个坐标差值
          splitNumber: 5, // 分为多少段
          axisLine: {
            lineStyle: {
              color: "#ccc"
            }
          }
        },
        series: [
          {
            name: "",
            type: "line",
            smooth: false, // true是曲线，false是直线
            data: this.resdata,
            // 设置折线区域颜色
            areaStyle: { normal: {} },
            itemStyle: {
              normal: {
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                  { offset: 0, color: "skyblue" }
                ]),
                lineStyle: {
                  color: "#1890ff"
                }
              }
            }
          }
        ]
      };
      chart.setOption(option);
      return chart;
    }
  },
  onPullDownRefresh() {},

  onReachBottom() {
    console.log("触底了, 触发触底事件, ajax咯");
  },

  created() {}
};
</script>

<style scoped>
.wrap {
  width: 120%;
  height: 260px;
  margin-left: -40px;
}
</style>
