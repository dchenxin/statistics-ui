<template>
  <div class="dashboard-editor-container">
    <el-row style="background:#fff;padding:16px 16px 0;margin-bottom:32px;">
      <el-col style="height: 500px">
        <div class="chart-wrapper">
          <div style="margin-bottom: 50px">
            <span class="title-text">安全统计分析</span>
            <el-radio-group v-model="defaultValue02" @change="buyEarlyBtnClick" size="small" style="float: right" fill="#63aff5">
              <el-radio-button label="昨日"></el-radio-button>
              <el-radio-button label="近七日"></el-radio-button>
              <el-radio-button label="本月"></el-radio-button>
              <el-radio-button label="本年"></el-radio-button>
            </el-radio-group>
          </div>
          <total-table v-on:table-select-change="tableChange" :table-data="tableData"></total-table>
          <!--          <line-chart :chart-data="lineChartData03"/>-->
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  import {getBuyEarlyStatistics} from "@/api/module/index";
  import TotalTable from '@/views/dashboard/TotalTable'
  import ModelDropDown from '@/views/dashboard/ModelDropDown'

  export default {
    name: 'BuyEarlyStatistics',
    components: {
      TotalTable,
      ModelDropDown
    },
    watch: {
      clickStatus: {
        deep: true,
        handler() {
          this.getOperation();
        }
      }
    },
    data() {
      return {
        defaultValue02: '昨日',
        tableData: [],
        tableSelectValue:1,
      }
    },
    mounted() {
      this.$nextTick(() => {
        this.getBuyEarly();
      })
    },
    created() {
    },
    methods: {
      //---------提前购票统计----------
      getBuyEarly(){
        getBuyEarlyStatistics({type:this.defaultValue02,selectType:this.tableSelectValue}).then(response => {
          this.tableData = response.data
        })
      },
      buyEarlyBtnClick() {
        this.getBuyEarly();
      },
      tableChange(val) {
        this.tableSelectValue = val;
        this.getBuyEarly();
      },
    }
  }
</script>

<style lang="scss" scoped>
  .dashboard-editor-container {
    padding: 32px;
    background-color: rgb(240, 242, 245);
    position: relative;

    .chart-wrapper {
      background: #fff;
      padding: 16px 16px 0;
      margin-bottom: 32px;
      height: 360px;
    }
  }

  .title-text {
    line-height: 18px;
    color: rgba(0, 0, 0, 0.45);
    font-size: 18px;
    margin-bottom: 12px;
  }

  .title-text-02 {
    line-height: 18px;
    color: rgba(0, 0, 0, 0.45);
    font-size: 14px;
    margin-bottom: 12px;
  }

  .number-span {
    font-weight: bolder;
    font-size: 16px;
  }

  @media (max-width: 1024px) {
    .chart-wrapper {
      padding: 8px;
    }
  }
</style>
