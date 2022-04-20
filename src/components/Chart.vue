<template>
  <div class="Echarts">
    <div>
      <div id="main" style="width: 600px; height: 400px"></div>
      <div id="bing" style="width: 600px; height: 400px"></div>
      <div id="line" style="width: 600px; height: 400px"></div>
    </div>
    <div>
      <div id="changeBar" style="width: 600px; height: 400px"></div>
    </div>
    <div>
      <button @click="changeData">changeData</button>
    </div>
  </div>
</template>
<script>
import json_data from './data.json'
export default {
  name: "Echarts",
  data() {
    return {
        barChart:{},
        bingChart:{},
        lineChart:{},
        changeBarChart:{},

        optionBar:json_data.bar,
        optionBing:json_data.bing,
        optionLine:json_data.line,
        optionChangeBar:json_data.changeBar,

        barData:[5, 20, 36, 10, 10, 20],
        barData_new:[10, 10, 5, 20, 36, 20],
        bingData: [{value: 100,name: "直接访问",},{value: 200,name: "广告",},{value: 335,name: "搜索",},],
        bingData_new: [{value: 335,name: "直接访问",},{value: 200,name: "广告",},{value: 100,name: "搜索",},],
        lineData:[10, 22, 28, 23, 19],
        lineData_new:[23,22,10,19,28],
        changeBarData:[],

        isChange:false
    };
  },
  methods: {
    changeData() {
      if(!this.isChange){
        this.newData(1)
        this.isChange=true
      }else{
        this.newData()
        this.isChange=false
      }
    },
    newData(num){
      if(num===1){
        this.optionBar.series[0].data=this.barData_new
        this.optionBing.series[0].data=this.bingData_new
        this.optionLine.series[0].data=this.lineData_new
      }else{
        this.optionBar.series[0].data=this.barData
        this.optionBing.series[0].data=this.bingData
        this.optionLine.series[0].data=this.lineData
      }
      this.barChart.setOption(this.optionBar);
      this.bingChart.setOption(this.optionBing);
      this.lineChart.setOption(this.optionLine);
    },
    EchartsInit() {
      this.barChart = this.$echarts.init(document.getElementById("main"));
      this.bingChart = this.$echarts.init(document.getElementById("bing"));
      this.lineChart = this.$echarts.init(document.getElementById("line"));
      this.changeBarChart = this.$echarts.init(document.getElementById("changeBar"));

      this.optionBar.series[0].data=this.barData
      this.optionBing.series[0].data=this.bingData
      this.optionLine.series[0].data=this.lineData
      this.optionChangeBar.series[0].data=this.changeBarData

      // 使用刚指定的配置项和数据显示图表。
      this.barChart.setOption(this.optionBar);
      this.bingChart.setOption(this.optionBing);
      this.lineChart.setOption(this.optionLine);
      this.changeBarChart.setOption(this.optionChangeBar);
    },
  },
  mounted() {
    this.EchartsInit();
    // this.timer=setInterval(()=>{
    //   this.changeData()
    // },3000)
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