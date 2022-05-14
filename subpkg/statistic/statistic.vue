<template>
  <view>
    <!-- 统计表 -->
    <view class="graph-container">
      <!-- 柱状图 -->
      <view class="graph-container-column">
        <qiun-data-charts type="column" :chartData="graphData" />
      </view>      
      <!-- 评价 -->
      <view class="graph-container-judgement">
        <qiun-data-charts type="arcbar" :opts="{title:{name:'80%',color:'#FFFFFF',fontSize:20},subtitle:{name:'优',color:'#FFFFFF',fontSize:25}}" :chartData="judgementData"/>
      </view>
    </view>
    <!-- 早中晚果列表 -->
    <view class="list-container">
      <view class="list-item-box" v-for="(item, index) in list" :key="index">
        <!-- 左盒子 -->
        <view class="list-item-box-left">
          <view class="list-item-box-left-head">
            {{item.title}}
          </view>
          <view class="list-item-box-left-detail-box">
            <view class="list-item-box-left-detail" v-for="(d, index2) in item.detail" :key="index2">
              {{d}}
            </view>
          </view>       
        </view>
        <!-- 右盒子 -->
        <view class="list-item-box-right">
          <view class="list-item-box-right-left">
            <view class="list-item-box-right-left-coal">
              碳足迹 : {{item.coal}}
            </view>
            <view class="list-item-box-right-left-coal-total">
              共 : {{item.coal_total}}
            </view>           
          </view>
          <view class="list-item-box-right-right">
            <view class="list-item-box-right-right-calorie">
              卡路里 : {{item.calorie}}
            </view>
            <view class="list-item-box-right-right-calorie-total">
              共 : {{item.calorie_total}}
            </view>
          </view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
  import demodata from '@/mockdata/demodata.json'
  
  export default {
    data() {
      return {
        graphData: {},
        judgementData: {},
        list: [
          {
            title: '早',
            detail: {
              d1: 'XXX',
              d2: 'XXX',
              d3: 'XXX'
            },             
            coal: '0 0 0',
            calorie: '0 0 0',
            coal_total: '. . . . . . .',
            calorie_total: '. . . . . . .'
          },
          {
            title: '中',
            detail: {
              d1: 'XXX',
              d2: 'XXX',
              d3: 'XXX'
            }, 
            coal: '0 0 0',
            calorie: '0 0 0',
            coal_total: '. . . . . . .',
            calorie_total: '. . . . . . .'
          },
          {
            title: '晚',
            detail: {
              d1: 'XXX',
              d2: 'XXX',
              d3: 'XXX'
            }, 
            coal: '0 0 0',
            calorie: '0 0 0',
            coal_total: '. . . . . . .',
            calorie_total: '. . . . . . .'
          },
          {
            title: '果',
            detail: {
              d1: 'XXX',
              d2: 'XXX',
              d3: 'XXX'
            }, 
            coal: '0 0 0',
            calorie: '0 0 0',
            coal_total: '. . . . . . .',
            calorie_total: '. . . . . . .'
          }
        ]
      };
    },
    onReady() {
      this.getSeverData()
    },
    methods: {
      getSeverData() {
        setTimeout(() => {
          this.graphData = JSON.parse(JSON.stringify(demodata.Column))
          this.judgementData = JSON.parse(JSON.stringify(demodata.Arcbar))
        }, 150)
      }
    }
  }
</script>

<style lang="scss">
  .graph-container {
    margin-top: 10px;
    background-color: #5dbec7;
    height: 160px;
    border-radius: 15px 15px 0 0;
    position: relative;
    overflow: hidden;
    display: flex;
    justify-content: space-around;
    align-items: center;
    
    &::after {
      content: '   ';
      display: block;
      height: 40px;
      width: 100%;
      background-color: #FFFFFF;
      position: absolute;
      bottom: 0;
      left: 0;
      transform: translateY(50%);
      border-radius: 15px 15px 0 0;
    }
    
    
    .graph-container-column {
      height: 120px;
      width: 240px;
      
    }
    
    .graph-container-judgement {
      height: 100px;
      width: 100px;
    }
  }
  
  .list-container {
    color: #5dbec7;
    .list-item-box {
      height: 85px;
      background-color: #d7f3f6;
      margin-top: 10px;
      border-radius: 10px;
      margin-left: 10px;
      margin-right: 10px;
      display: flex;
      justify-content: space-around;
      align-items: center;
      
      .list-item-box-left {
        border-right: 1px solid #5dbec7;
        width: 120px;
        height: 72px;
        display: flex;
        justify-content: space-around;
        align-items: center;
        .list-item-box-left-head {
          height: 30px;
          width: 30px;
          line-height: 30px;
          border-radius: 100%;
          background-color: #FFFFFF;
          text-align: center;
          font-size: 20px;
        }
        
        .list-item-box-left-detail-box {
          display: flex;
          flex-direction: column;
          
        }
      }
      
      .list-item-box-right {
        height: 72px;
        width: 200px;
        display: flex;
        justify-content: space-around;
        align-items: center;
        .list-item-box-right-left {
          height: 100%;
          display: flex;
          flex-direction: column;
          justify-content: space-around;
          .list-item-box-right-left-coal {
            
          }
        }
        .list-item-box-right-right {
          height: 100%;
          display: flex;
          flex-direction: column;
          justify-content: space-around;
          .list-item-box-right-right-calorie {
          }
        }
      }
    }
  }
</style>
