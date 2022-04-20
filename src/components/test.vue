<template>
  <div>
    <div id="main" style="width: 600px; height: 400px"></div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      data: [],
      option: {},
      myChart:{}
    };
  },
  methods: {
    initData() {
      for (let i = 0; i < 5; ++i) {
        this.data.push(Math.round(Math.random() * 200));
      }
      this.option = {
        xAxis: {
          max: "dataMax",
        },
        yAxis: {
          type: "category",
          data: ["A", "B", "C", "D", "E"],
          inverse: true,
          animationDuration: 300,
          animationDurationUpdate: 300,
          max: 2, // only the largest 3 bars will be displayed
        },
        series: [
          {
            realtimeSort: true,
            name: "X",
            type: "bar",
            data: this.data,
            label: {
              show: true,
              position: "right",
              valueAnimation: true,
            },
          },
        ],
        legend: {
          show: true,
        },
        animationDuration: 3000,
        animationDurationUpdate: 3000,
        animationEasing: "linear",
        animationEasingUpdate: "linear",
      };
        this.myChart = this.$echarts.init(document.getElementById("main"));
    },
    update() {
      this.data = this.option.series[0].data;
      for (var i = 0; i < this.data.length; ++i) {
        if (Math.random() > 0.9) {
          this.data[i] += Math.round(Math.random() * 2000);
        } else {
          this.data[i] += Math.round(Math.random() * 200);
        }
      }
      this.myChart.setOption(this.option);
    },
    changeWithTime() {
      setInterval(() => {
        this.update();
      }, 3000);
    },
  },
  mounted(){
    this.initData()
    this.changeWithTime()
  },
};
</script>
