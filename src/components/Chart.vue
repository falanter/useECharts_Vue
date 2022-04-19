<template>
  <div class="Echarts">
    <div>
      <div id="main" style="width: 600px; height: 400px"></div>
      <div id="bing" style="width: 600px; height: 400px"></div>
      <div id="line" style="width: 600px; height: 400px"></div>
    </div>
    <div class="down">
      <button @click="change">change</button>
    </div>
  </div>
</template>
<script>
export default {
  name: "Echarts",
  data() {
    return {
        barData:[5, 20, 36, 10, 10, 20],
        barData_new:[],
        optionBing:{
        series: [
          {
            type: "pie",
            data: [],
          },
        ],
      },
      bingData: [{value: 100,name: "直接访问",},{value: 200,name: "广告",},{value: 335,name: "搜索",},],
      bingData_new: [{value: 335,name: "直接访问",},{value: 200,name: "广告",},{value: 100,name: "搜索",},],
    };
  },
  methods: {
    change() {
      let myChart2 = this.$echarts.init(document.getElementById("bing"));
      this.optionBing.series[0].data=this.bingData_new
      myChart2.setOption(this.optionBing);
    },
    myEcharts() {
      let myChart = this.$echarts.init(document.getElementById("main"));
      let option = {
        title: {
          text: "ECharts 入门示例",
        },
        tooltip: {},
        legend: {
          data: ["销量"],
        },
        xAxis: {
          data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"],
        },
        yAxis: {},
        series: [
          {
            name: "销量",
            type: "bar",
            data: this.barData,
          },
        ],
      };

      let myChart2 = this.$echarts.init(document.getElementById("bing"));
      this.optionBing.series[0].data=this.bingData

      let myChart3 = this.$echarts.init(document.getElementById("line"));
      let optionLine = {
        tooltip: {
            trigger: 'axis',
            axisPointer: { type: 'cross' }
        },
        xAxis: {
            data: ['A', 'B', 'C', 'D', 'E']
        },
        yAxis: {},
        series: [
          {
            type: "line",
            data: [10, 22, 28, 23, 19],
            smooth:true
          },
        ],
      };

      // 使用刚指定的配置项和数据显示图表。
      myChart.setOption(option);
      myChart2.setOption(this.optionBing);
      myChart3.setOption(optionLine);
    },
  },
  mounted() {
    this.myEcharts();
  },
};
</script>
<style>
.Echarts {
  display: flex;
  flex-direction: column;
}
.Echarts div {
  display: inherit;
}
</style>