<template>
  <div id="centerLeft1">
    <div class="bg-color-black">
      <div class="d-flex pt-2 pl-2">
        <span>
          <data-icon name="chart-pie" class="text-icon"></data-icon>
        </span>
        <div class="d-flex">
          <span class="fs-xl text mx-2">用户地区分布</span>
          <dv-decoration-1 class="dv-dec-1" />
        </div>
      </div>
      <div class="d-flex jc-center">
        <CenterLeft2Chart />
      </div>
    </div>
  </div>
</template>

<script>
import CenterLeft2Chart from "@/components/echart/centerLeft/centerLeft2Chart";
export default {
  components: {
    CenterLeft2Chart
  },
};
</script>

<style lang="scss" scoped>
#centerLeft1 {
  $box-width: 300px;
  $box-height: 410px;
  padding: 16px;
  height: $box-height;
  min-width: $box-width;
  border-radius: 5px;
  .bg-color-black {
    height: $box-height - 30px;
    border-radius: 10px;
  }
  .text {
    color: #c3cbde;
  }
  .dv-dec-1 {
    position: relative;
    width: 100px;
    height: 20px;
    top: -3px;
  }
  .chart-box {
    margin-top: 16px;
    width: 170px;
    height: 170px;
    .active-ring-name {
      padding-top: 10px;
    }
  }
}
.d-flex {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
}
.pl-2 {
  padding-left: 0.5rem;
}
.pt-2 {
  padding-top: 0.5rem;
}
.mx-2 {
  margin-left: 0.5rem;
  margin-right: 0.5rem;
}
.fs-xl {
  font-size: 0.04rem;
}
.jc-center {
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
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
