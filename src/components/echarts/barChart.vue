<template>
    <div :id="id" class="orderArea orderbarArea"></div>
</template>

<script>
    import echarts from 'echarts'
    import echartsTheme from "cps/echarts/theme/westeros.json";
    import ColorThemeVue from '../../../../coreui-free-vue-admin-template-main/src/views/theme/ColorTheme.vue';
    export default {
        name:'barChat',
        data(){
            return {
                 id:'barChart',
                 myChart:null,
            }
        },
        mounted(){
            this.loadChart();
        },
        beforeDestroy() {
			if (!this.myChart) {
				return
			}
			this.myChart.dispose();
			this.myChart = null;
        },
        methods: {
            loadChart(){
                this.$nextTick(() => {
                    echarts.registerTheme('westeros', echartsTheme)
                    this.myChart = echarts.init(document.getElementById(this.id),'westeros');
                    this.myChart.setOption(this.initOption());
                })
            },
         	initOption(){
                let option = {
                    title: {
                        text: ' Tribe OPEN/ClOSED PRONTO',
                        subtext: 'OPEN PR:14',
                        left: 'center'
                    },
                    tooltip : {
                        trigger: 'axis'
                    },
                    legend: {
                        data:['open','closed'],
                        right: 'right'
                    },
                    xAxis : [
                        {
                            type : 'category',
                            data : ['COAM','RCP','FHGW','L1','L2','CP','DEP','TRS','RF','SPEC']
                        }
                    ],
                    yAxis : [
                        {
                            type : 'value'
                        }
                    ],
                    
                    series : [
                        {
                            name:'open',
                            type:'bar',
                            data:[2.0, 4.9, 7.0, 23.2, 25.6, 76.7, 135.6, 162.2, 32.6, 20.0],
                            markPoint : {
                                data : [
                                    {type : 'max', name: '最大值'},
                                    {type : 'min', name: '最小值'}
                                ]
                            }
                        },
                        {
                            name:'closed',
                            type:'bar',
                            data:[2.6, 5.9, 9.0, 26.4, 28.7, 70.7, 175.6, 182.2, 48.7, 18.8],
                            markPoint : {
                                data : [
                                    {name : '年最高', value : 182.2, xAxis: 7, yAxis: 183},
                                    {name : '年最低', value : 2.0, xAxis: 0, yAxis: 2}
                                ]
                            }
                        }
                    ]
                };
				return option;
			},
        },
        watch: {
        }
    }
</script>

<style lang="less">

</style>
