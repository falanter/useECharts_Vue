<template>
    <div class="Echarts">
        <button @click="change">change</button>
        <div id="main" style="width:600px;height:400px"></div>
        <div id="bing" style="width:600px;height:400px"></div>
    </div>
</template>
<script>
export default {
   name:'Echarts',
   methods:{
       change(){
           let myChart2=this.$echarts.init(document.getElementById('bing'));
            let optionBing={
                series:[
                    {
                        type:'pie',
                        data:[
                            {
                                value:200,
                                name:'直接访问'
                            },{
                                value:335,
                                name:'广告'
                            },{
                                value:100,
                                name:'搜索'
                            }
                        ]
                    }
                ]
            }
            myChart2.setOption(optionBing)
       },
       myEcharts(){
           let myChart=this.$echarts.init(document.getElementById('main'));
           let option={
               title:{
                   text:'ECharts 入门示例'
               },
               tooltip:{},
               legend:{
                   data:['销量']
               },
               xAxis:{
                   data: ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"]
               },
               yAxis:{},
               series: [{
                    name: '销量',
                    type: 'bar',
                    data: [5, 20, 36, 10, 10, 20]
			  }]
           }
            
            let myChart2=this.$echarts.init(document.getElementById('bing'));
            let optionBing={
                series:[
                    {
                        type:'pie',
                        data:[
                            {
                                value:100,
                                name:'直接访问'
                            },{
                                value:200,
                                name:'广告'
                            },{
                                value:335,
                                name:'搜索'
                            }
                        ]
                    }
                ]
            }
            // 使用刚指定的配置项和数据显示图表。
		    myChart.setOption(option);
            myChart2.setOption(optionBing)
        }
    },
    mounted(){
        this.myEcharts();
    }
}
</script>