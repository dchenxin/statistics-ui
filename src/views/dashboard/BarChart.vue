<template>
  <div :class="className" :style="{height:height,width:width}"/>
</template>

<script>
  import echarts from 'echarts'

  require('echarts/theme/macarons') // echarts theme
  import resize from './mixins/resize'
  import {barCount} from "@/api/module/index";

  const animationDuration = 6000

  export default {
    mixins: [resize],
    props: {
      className: {
        type: String,
        default: 'chart'
      },
      width: {
        type: String,
        default: '100%'
      },
      height: {
        type: String,
        default: '300px'
      },
      barChartData: {
        type: Object,
        required: true
      },
      series: {
        type: Array,
        required: true
      },
    },
    data() {
      return {
        chart: null
      }
    },
    watch: {
      barChartData: {
        deep: true,
        handler() {
          this.initChart()
        }
      },
      series: {
        deep: true,
        handler() {
          this.initChart()
        }
      }
    },
    mounted() {
      this.$nextTick(() => {
        this.initChart(this.barChartData)
      })
    },
    beforeDestroy() {
      if (!this.chart) {
        return
      }
      this.chart.dispose()
      this.chart = null
    },
    methods: {
      initChart() {
        this.chart = echarts.init(this.$el, 'macarons')
        this.chart.setOption({
          legend: {},
          grid: {
            left: '3%',
            right: '4%',
            bottom: '3%',
            containLabel: true
          },
          tooltip: {
            trigger: 'axis',
            axisPointer: {
              type: 'shadow'
            }
          },
          toolbox: {
            show: true,
            orient: 'vertical',
            left: 'right',
            top: 'center',
            feature: {
              mark: {show: true},
              dataView: {show: true, readOnly: false},
              magicType: {show: true, type: ['line', 'bar', 'stack']},
              restore: {show: true},
              saveAsImage: {show: true}
            }
          },
          dataset: this.barChartData,
          xAxis: {type: 'category'},
          yAxis: {},
          series: this.series
        },true)
      }
    }
  }
</script>
