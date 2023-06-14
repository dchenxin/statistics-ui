<template>
  <div id="centerRight2">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span>
          <data-icon name="align-left" class="text-icon"></data-icon>
        </span>
        <span class="fs-xl text mx-2">用户提前购票时间分析</span>
      </div>
      <div class="d-flex ai-center flex-column body-box">
        <dv-capsule-chart class="dv-cap-chart" :config="config"/>
<!--        <centerRight2Chart1/>-->
      </div>
    </div>
  </div>
</template>

<script>
  import centerRight2Chart1 from '@/components/echart/centerRight/centerRightChart'

  export default {
    data() {
      return {
        config: {
          showValue:true,
          data: [
            {
              name: '南阳',
              value: 167
            },
            {
              name: '周口',
              value: 67
            },
            {
              name: '漯河',
              value: 123
            },
            {
              name: '郑州',
              value: 55
            },
            {
              name: '西峡',
              value: 98
            },
            {
              name: '西峡',
              value: 98
            },
            {
              name: '西峡',
              value: 78
            },
            {
              name: '西峡',
              value: 68
            },
            {
              name: '西峡',
              value: 58
            },
            {
              name: '西峡',
              value: 81
            }
          ]
        }
      }
    },
    components: {centerRight2Chart1}
  }
</script>

<style lang="scss" scoped>
  #centerRight2 {
    $box-height: 410px;
    $box-width: 340px;
    padding: 5px;
    height: $box-height;
    width: $box-width;
    border-radius: 5px;

    .bg-color-black {
      padding: 5px;
      height: $box-height;
      width: $box-width;
      border-radius: 10px;
    }

    .text {
      color: #c3cbde;
    }

    .body-box {
      border-radius: 10px;
      overflow: hidden;

      .dv-cap-chart {
        width: 100%;
        height: 370px;
      }
    }
  }

  .pl-2 {
    padding-left: 0.5rem;
  }

  .pt-2 {
    padding-top: 0.5rem;
  }

  .d-flex {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
  }
  .mx-2 {
    margin-left: 0.5rem;
    margin-right: 0.5rem;
  }
  .fs-xl {
    font-size: 0.04rem;
  }
  .ai-center {
    -webkit-box-align: center;
    -ms-flex-align: center;
    align-items: center;
  }
  .flex-column {
    -webkit-box-orient: vertical;
    -webkit-box-direction: normal;
    -ms-flex-direction: column;
    flex-direction: column;
  }
  * {
    margin: 0;
    padding: 0;
    list-style-type: none;
    outline: none;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
  }
</style>
