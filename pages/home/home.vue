<template>
  <view>
    <!-- 轮播图 -->
    <uni-swiper-dot :info="info" :current="current" field="content" :mode="mode" :dotsStyles="dotStyle">
      <swiper class="swiper-box" @change="change" circular>
        <swiper-item v-for="(item ,index) in info" :key="index">
          <view class="swiper-item">
            <image :src="item.content"></image>
          </view>
        </swiper-item>
      </swiper>
    </uni-swiper-dot>

    <!-- 日历 -->
    <view class="calendar-box">
      <view class="my_calendar">
        <view class="calendar_title">
          <view class="leftTriangle" @click="preWeeks()">
            <view class="triagle"></view>
          </view>
          <view class="rightTriangle" @click="nextWeeks()">
            <view class="triagle"></view>
          </view>
          <picker mode="date" :value="getDay(currDay)" @change="bindDateChange">
            <!-- <view class="helthy_icon_calendar">&#xe752;</view> -->
            <view class="txt">{{currDay.getFullYear()}}年{{currDay.getMonth()+1}}月</view>
          </picker>
        </view>
        <view class="calendar_content">
          <view class="uni-flex uni-row">
            <view class="flex-item">日</view>
            <view class="flex-item">一</view>
            <view class="flex-item">二</view>
            <view class="flex-item">三</view>
            <view class="flex-item">四</view>
            <view class="flex-item">五</view>
            <view class="flex-item">六</view>
          </view>
          <view class="uni-flex uni-row">
            <view class="flex-item" v-for="(val,ind) in currWeek" :key="ind" @click="changeDay(ind)">
              <view :class="{item:true,on:getDay(val.data) == getDay(selectDay.data)}" v-text="val.data.getDate()">
              </view>
              <view class="isSpot" v-if="val.isTrue"></view>
            </view>
          </view>
        </view>
      </view>

    </view>

    <!-- 四大板块 -->
    <view class="pattern-box-container">
      <view class="pattern-box" v-for="(item, index) in patterns" :key="index" @click="toDetail(index)">
        <view class="img-box">
          <image :src="item.img" mode="widthFix"></image>
        </view>
        <view class="text-box">
          <text>{{item.text}}</text>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
  import myCalendar from '@/components/myCalendar/index.vue'
  const app = getApp();

  export default {
    name: "MyCalendar",
    props: ["currData"],
    data() {
      return {
        info: [{
          content: "../../static/swiper_list/swiperList_img%20(1).jpg"
        }, {
          content: "../../static/swiper_list/swiperList_img%20(2).jpg"
        }, {
          content: "../../static/swiper_list/swiperList_img%20(3).jpg"
        }, {
          content: "../../static/swiper_list/swiperList_img%20(4).jpg"
        }],
        patterns: [
          {
            img: "../../static/home_icons/breakfast.jpg",
            text: "早餐"
          },
          {
            img: "../../static/home_icons/lunch.jpg",
            text: "午餐"
          },
          {
            img: "../../static/home_icons/dinner.jpg",
            text: "晚餐"
          },
          {
            img: "../../static/home_icons/fruits.jpg",
            text: "水果"
          }
        ],
        current: 0,
        mode: 'round',
        dotStyle: {
          backgroundColor: 'rgba(85, 85, 85, 0.3)',
          // border: '1px rgba(255, 255, 255, 0.3) solid',
          color: '#fff',
          selectedBackgroundColor: 'rgba(255, 255, 255, 0.9)',
          // selectedBorder: '1px rgba(255, 255, 255, 0.9) solid'
        },
        GLOBAL: this.GLOBAL,
        // 选择的日期
        selectDay: {
          data: new Date(),
          // 是否需要加点
          isTrue: false,
        },
        // 当前日期，本周的某一天
        currDay: new Date(),
        // 本周
        currWeek: [],
        timelist: []
      }
    },
    methods: {
      toDetail(key) {
        console.log(key)
        uni.navigateTo({
          url: '../../subpkg/pattern_detail/pattern_detail?index='+key
        })
      },
      change(e) {
        this.current = e.detail.current;
      },
      initTime() {
        // selectDay.isTrue需要使用时在这个函数里面写你自己的代码
        uni.navigateTo({
          url: '../../subpkg/statistic/statistic'
        })
      },
      // 日历选择日期
      bindDateChange(e) {
        this.currDay = new Date(e.target.value);
        this.selectDay.data = new Date(e.target.value);
        for (var i = 0; i < this.timelist.length; i++) {
          if (this.timelist[i] == e.target.value) {
            this.selectDay.isTrue = true;
          }
        }
        this.currWeek = this.getWeeks(e.target.value);
        this.$emit('func', this.selectDay)
        // this.initTime();
      },
      // 本周选择日期
      changeDay(ind) {
        // console.log(this.currWeek[ind])
        this.currDay = this.currWeek[ind].data;
        this.selectDay = this.currWeek[ind];
        this.$emit('func', this.selectDay)
        this.initTime();
      },
      // 获取本周
      getWeeks(data) {
        var t = [];
        var d = new Date(data);
        var timesStamp = d.getTime();
        var time = 24 * 60 * 60 * 1000;
        var a = d.getDay();
        for (var i = 0; i < 7; i++) {
          t[i] = {
            data: "",
            isTrue: false
          }
          if (a == i) {
            t[i].data = d;
          } else if (a > i) {
            t[i].data = new Date(timesStamp - time * (a - i));
          } else {
            t[i].data = new Date(timesStamp + time * (i - a));
          }
        }
        return t;
      },
      // 获取上一周
      preWeeks() {
        var time = this.currDay.getTime();
        var d = new Date(time - 7 * 24 * 60 * 60 * 1000);
        this.currDay = d;
        this.currWeek = this.getWeeks(d);
        // this.initTime();
      },
      //获取下一周
      nextWeeks() {
        var time = this.currDay.getTime();
        var d = new Date(time + 7 * 24 * 60 * 60 * 1000);
        this.currDay = d;
        this.currWeek = this.getWeeks(d);
        // this.initTime();
      },
      // 格式化日期
      getDay(time) {
        let date = new Date(time);
        let year = date.getFullYear();
        let month = date.getMonth() + 1;
        let day = date.getDate();
        month = month > 9 ? month : '0' + month;;
        day = day > 9 ? day : '0' + day;
        return `${year}-${month}-${day}`;
      }

    },
    created() {
      this.currWeek = this.getWeeks(new Date());
      // this.initTime();
    },
  }
</script>

<style lang="scss">
  // 轮播图
  .swiper-box {
    height: 180px;
    width: 100%;

    .swiper-item {
      width: 100%;
      height: 100%;

      image {
        width: 100%;
      }
    }
  }

  // 日历
  .my_calendar {
    width: 100%;
    height: 80px;
    border-bottom: 1px solid #D3D3D3;

    .calendar_title {
      font-size: 30rpx;
      color: #272727;
      text-align: center;
      margin: 0 26rpx;
      height: 30rpx;
      line-height: 30rpx;

      &::after {
        clear: both;
      }

      .txt {
        vertical-align: middle;
        display: inline-block;
      }

      .leftTriangle,
      .rightTriangle {
        position: relative;
        z-index: 88;
        width: 15%;
        margin-top: 20rpx;

        .triagle {
          width: 0;
          height: 0;
        }
      }

      .leftTriangle {
        float: left;

        .triagle {
          border-top: 16rpx solid transparent;
          border-right: 20rpx solid #999;
          border-bottom: 16rpx solid transparent;
        }
      }

      .rightTriangle {
        float: right;

        .triagle {
          float: right;
          border-top: 16rpx solid transparent;
          border-left: 20rpx solid #999;
          border-bottom: 16rpx solid transparent;
        }
      }
    }

    .calendar_content {
      margin: 26rpx;
      text-align: center;

      .uni-row {
        &:first-child {
          .flex-item {
            color: #CCCCCC;
          }
        }

        .flex-item {
          color: #333333;
          width: 14.2%;

          .item {
            width: 51rpx;
            height: 51rpx;
            line-height: 51rpx;
            margin: auto;
          }

          .on {
            color: #fff;
            background-color: #5dbec7;
            -moz-border-radius: 50%;
            -webkit-border-radius: 50%;
            border-radius: 5px;
          }

          .isSpot {
            width: 10rpx;
            height: 10rpx;
            background-color: #93D879;
            margin: 20rpx auto;
            -moz-border-radius: 50%;
            -webkit-border-radius: 50%;
            border-radius: 50%;
          }
        }
      }

    }
  }

  // 四大板块
  .pattern-box-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    padding: 0 5px;
    margin-top: 10px;
    .pattern-box {
      height: 140px;
      width: 180px;
      display: flex;
      flex-direction: column;

      .img-box {
        height: 100px;
        width: 100%;

        image {
          height: 100%;
          width: 100%;
        }
      }
      
      .text-box {
        background-color: #5dbec7;
        height: 30px;
        width: 100%;
        text-align: center;
        align-items: center;
        text {
          font-size: 17px;
          color: #FFFFFF;
        }
      }
    }
  }
</style>
