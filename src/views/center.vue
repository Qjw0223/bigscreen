<template>
  <div id="center">
    <div class="up">
      <div
        class="bg-color-black item"
        v-for="item in titleItem"
        :key="item.title"
      >
        <p class="ml-3 colorBlue fw-b fs-xl">{{ item.title }}</p>
        <div>
          <dv-digital-flop
            class="dv-dig-flop ml-1 mt-2 pl-3"
            :config="item.number"
          />
        </div>
      </div>
    </div>
    <div class="down">
      <div class="ranking bg-color-black">
        <span>
          <icon name="chart-pie" class="text-icon"></icon>
        </span>
        <span class="fs-xl text mx-2 mb-1 pl-3">护工年度订单完成量</span>
        <dv-scroll-ranking-board class="dv-scr-rank-board mt-1" :config="ranking" />
      </div>
      <div class="percent">
        <div class="item bg-color-black">
          <span>今日完结订单占比</span>
          <CenterChart
            :id="rate[0].id"
            :tips="rate[0].tips"
            :colorObj="rate[0].colorData"
          />
        </div>
        <div class="item bg-color-black">
          <span>今日新订单占比</span>
          <CenterChart
            :id="rate[1].id"
            :tips="rate[1].tips"
            :colorObj="rate[1].colorData"
          />
        </div>
        <div class="water">
          <dv-water-level-pond class="dv-wa-le-po" :config="water" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CenterChart from '@/components/echart/center/centerChartRate'

export default {
  data() {
    return {
      titleItem: [
        {
          title: '今年完结订单总数',
          number: {
            number: [120],
            toFixed: 0,
            textAlign: 'center',
            content: '{nt}',
            style: {
              fontSize: 32
            }
          }
        },
        {
          title: '本月完结订单总数',
          number: {
            number: [18],
            toFixed: 0,
            textAlign: 'center',
            content: '{nt}',
            style: {
              fontSize: 32
            }
          }
        },
        {
          title: '今日完结订单数',
          number: {
            number: [2],
            toFixed: 0,
            textAlign: 'center',
            content: '{nt}',
            style: {
              fontSize: 32
            }
          }
        },
        {
          title: '在护人数',
          number: {
            number: [14],
            toFixed: 0,
            textAlign: 'center',
            content: '{nt}',
            style: {
              fontSize: 32
            }
          }
        },
        {
          title: '护工人数',
          number: {
            number: [106],
            toFixed: 0,
            textAlign: 'center',
            content: '{nt}',
            style: {
              fontSize: 32
            }
          }
        },
        {
          title: '欠费待缴数额',
          number: {
            number: [100],
            toFixed: 2,
            textAlign: 'center',
            content: '{nt}',
            style: {
              fontSize: 32
            }
          }
        }
      ],
      ranking: {
        data: [
          {
            name: 'xxx',
            value: 55
          },
          {
            name: 'xxx',
            value: 120
          },
          {
            name: 'xxx',
            value: 78
          },
          {
            name: 'xxx',
            value: 66
          },
          {
            name: 'xxx',
            value: 50
          },
          {
            name: 'xxx',
            value: 91
          },
          {
            name: 'xxx',
            value: 29
          },
          {
            name: 'xxx',
            value: 80
          },
          {
            name: 'xxx',
            value: 43
          },
        ],
        sort:false,
        carousel: 'single',
        unit: '笔'
      },
      water: {
        data: [60, 40],
        shape: 'roundRect',
        formatter: '{value}%',
        waveNum: 4
      },
      // 占比的组件复用数据
      rate: [
        {
          id: 'centerRate1',
          tips: 60,
          colorData: {
            textStyle: '#3fc0fb',
            series: {
              color: ['#00bcd44a', 'transparent'],
              dataColor: {
                normal: '#03a9f4',
                shadowColor: '#97e2f5'
              }
            }
          }
        },
        {
          id: 'centerRate2',
          tips: 40,
          colorData: {
            textStyle: '#67e0e3',
            series: {
              color: ['#faf3a378', 'transparent'],
              dataColor: {
                normal: '#ff9800',
                shadowColor: '#fcebad'
              }
            }
          }
        }
      ]
    }
  },
  components: {
    CenterChart
  }
}
</script>

<style lang="scss" scoped>
#center {
  display: flex;
  flex-direction: column;
  .up {
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    .item {
      border-radius: 6px;
      padding-top: 8px;
      margin-top: 8px;
      width: 32%;
      height: 70px;
      .dv-dig-flop {
        width: 150px;
        height: 30px;
      }
    }
  }
  .down {
    padding: 6px 4px;
    padding-bottom: 0;
    width: 100%;
    display: flex;
    height: 255px;
    justify-content: space-between;
    .bg-color-black {
      border-radius: 5px;
    }
    .ranking {
      padding: 10px;
      width: 59%;
      .dv-scr-rank-board {
        height: 224px;
      }
    }
    .percent {
      width: 40%;
      display: flex;
      flex-wrap: wrap;
      .item {
        width: 50%;
        height: 120px;
        span {
          margin-top: 8px;
          font-size: 14px;
          display: flex;
          justify-content: center;
        }
      }
      .water {
        width: 100%;
        .dv-wa-le-po {
          height: 120px;
        }
      }
    }
  }
}
</style>
