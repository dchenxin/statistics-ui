<template>
  <div id="index" ref="appRef">
    <div class="bg" :style="{backgroundImage: 'url('+ img.url +')'}">
      <dv-loading v-if="loading">Loading...</dv-loading>
      <div v-else class="host-body">
        <div class="d-flex jc-center">
          <dv-decoration-10 class="dv-dec-10"/>
          <div class="d-flex jc-center">
            <dv-decoration-8 class="dv-dec-8" :color="decorationColor"/>
            <div class="title">
              <span class="title-text">大数据可视化平台</span>
              <dv-decoration-6
                class="dv-dec-6"
                :reverse="true"
                :color="['#50e3c2', '#67a1e5']"
              />
            </div>
            <dv-decoration-8
              class="dv-dec-8"
              :reverse="true"
              :color="decorationColor"
            />
          </div>
          <dv-decoration-10 class="dv-dec-10-s"/>
        </div>

        <!-- 第二行 -->
        <div class="d-flex jc-between px-2">
          <div class="d-flex aside-width">
            <div class="react-left ml-4 react-l-s">
              <span class="react-left"></span>
              <span class="text">数据分析1</span>
            </div>
            <div class="react-left ml-3">
              <span class="text">数据分析2</span>
            </div>
          </div>
          <div class="d-flex aside-width">
            <div class="react-right bg-color-blue mr-3">
              <span class="text fw-b">航班数据统计分析</span>
<!--              <el-dropdown style="color:#cbc3c3;">-->
<!--                <span class="text fw-b" style="font-size: 17px">-->
<!--                  选择分析界面<i class="el-icon-arrow-down el-icon&#45;&#45;right"></i>-->
<!--                </span>-->
<!--                <el-dropdown-menu slot="dropdown">-->
<!--                  <el-dropdown-item>用户数据统计分析</el-dropdown-item>-->
<!--                  <el-dropdown-item>狮子头</el-dropdown-item>-->
<!--                  <el-dropdown-item>螺蛳粉</el-dropdown-item>-->
<!--                  <el-dropdown-item>双皮奶</el-dropdown-item>-->
<!--                  <el-dropdown-item>蚵仔煎</el-dropdown-item>-->
<!--                </el-dropdown-menu>-->
<!--              </el-dropdown>-->
            </div>
            <div class="react-right mr-4 react-l-s">
              <span class="react-after"></span>
              <span class="text"
              >{{ dateYear }} {{ dateWeek }} {{ dateDay }}</span
              >
            </div>
          </div>
        </div>

        <div class="body-box">
          <!-- 第三行数据 -->
          <div class="content-box">
            <div>
              <dv-border-box-12>
                <centerLeft1/>
              </dv-border-box-12>
            </div>
            <div>
              <dv-border-box-12>
                <centerLeft2/>
              </dv-border-box-12>
            </div>
            <!-- 中间 -->
            <div>
              <center/>
            </div>
            <!-- 中间 -->
            <div>
              <centerRight2/>
            </div>
            <div>
              <dv-border-box-13>
                <centerRight1/>
              </dv-border-box-13>
            </div>
          </div>

          <!-- 第四行数据 -->
          <div class="bottom-box">
            <dv-border-box-13>
              <bottomLeft/>
            </dv-border-box-13>
            <dv-border-box-12>
              <bottomRight/>
            </dv-border-box-12>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import drawMixin from "../../../utils/drawMixin";
  import {formatTime} from '../../../utils'
  import centerLeft1 from '../../dataView/centerLeft1'
  import centerLeft2 from '../../dataView/centerLeft2'
  import centerRight1 from '../../dataView/centerRight1'
  import centerRight2 from '../../dataView/centerRight2'
  import center from '../../dataView/center'
  import bottomLeft from '../../dataView/bottomLeft'
  import bottomRight from '../../dataView/bottomRight'

  export default {
    mixins: [drawMixin],
    data() {
      return {
        img: {
          url: require('@/assets/pageBg.png'),
        },
        timing: null,
        loading: true,
        dateDay: null,
        dateYear: null,
        dateWeek: null,
        weekday: ['周日', '周一', '周二', '周三', '周四', '周五', '周六'],
        decorationColor: ['#568aea', '#000000'],
        optionValue: "1",
      }
    },
    components: {
      centerLeft1,
      centerLeft2,
      centerRight1,
      centerRight2,
      center,
      bottomLeft,
      bottomRight
    },
    mounted() {
      this.timeFn()
      this.cancelLoading()
      this.changeBgColor()
    },
    beforeDestroy() {
      clearInterval(this.timing)
    },
    methods: {
      //单击隐藏侧边栏
      changeBgColor() {
        const element = document.getElementById("app");
        element.setAttribute('style', 'background-color: #020308');
      },
      timeFn() {
        this.timing = setInterval(() => {
          this.dateDay = formatTime(new Date(), 'HH: mm: ss')
          this.dateYear = formatTime(new Date(), 'yyyy-MM-dd')
          this.dateWeek = this.weekday[new Date().getDay()]
        }, 1000)
      },
      cancelLoading() {
        setTimeout(() => {
          this.loading = false
        }, 500)
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import "../../../assets/scss/index.scss";

  .d-flex {
    display: flex;
  }

  .jc-center {
    -webkit-box-pack: center;
    -ms-flex-pack: center;
    justify-content: center;
  }

  .jc-between {
    -webkit-box-pack: justify;
    -ms-flex-pack: justify;
    justify-content: space-between;
  }

  .fw-b {
    font-weight: bold;
  }

  .ml-4 {
    margin-left: 1rem;
  }

  .ml-3 {
    margin-left: 0.75rem;
  }

  .mr-3 {
    margin-right: 0.75rem;
  }

  .bg-color-blue {
    background-color: #1a5cd7;
  }
</style>
