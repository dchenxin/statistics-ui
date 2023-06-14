<template>
  <div style="margin-top: 60px">
    <Chart :cdata="cdata" />
  </div>
</template>

<script>
import Chart from './chart.vue';
export default {
  data () {
    return {
      cdata: {
        xData: ["17岁以下", "18~24岁", "25~29岁", "30~39岁", "40~49岁", "50岁以上"],
        seriesData: [
          { value: 10, name: "17岁以下" },
          { value: 5, name: "18~24岁" },
          { value: 15, name: "25~29岁" },
          { value: 25, name: "30~39岁" },
          { value: 20, name: "40~49岁" },
          { value: 35, name: "50岁以上" }
        ]
      }
    }
  },
  components: {
    Chart,
  },
  mounted () {
  },
  methods: {
  }
}
</script>

<style lang="scss" scoped>
</style>
