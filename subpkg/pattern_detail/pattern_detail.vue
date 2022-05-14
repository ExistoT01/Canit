<template>
  <view>
    <!-- 导航栏 -->
    <view class="navigation-box">
      <view class="navigation-tab" v-for="(item, index) in tabs" :key="index">
        <!-- 图标 -->
        <view class="img-box">
          <image :src="item.image" @click="todiy"></image>
        </view>
        <!-- 文字 -->
        <view class="text-box">
          {{item.text}}
        </view>      
      </view>
    </view>
    <!-- 列表 -->
    <view class="list-box">
      <view class="list-item" v-for="(item, index) in list" :key="index">
        <!-- 左边盒子 -->
        <view class="list-item-left-box">
          <!-- 标题 -->
          <view class="list-item-left-box-title">
            {{item.title}}
          </view>
          <!-- 碳&卡路里 -->
          <view class="list-item-left-box-coalAndCalorie">
            <view class="list-item-left-box-coalAndCalorie-coal">
              碳足迹：{{item.coal}}
            </view>
            <view class="list-item-left-box-coalAndCalorie-coal-calorie">
              卡路里：{{item.calorie}} / 100克
            </view>
          </view>
        </view>
        <!-- 右边盒子 -->
        <view class="list-item-right-box" @click="toPopup">
          <image :src="item.image" mode=""></image>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        tabs: [
          {
            image: '../../static/pattern_detail_icons/veg_r.png',
            text: '菜品'
          },         
          {
            image: '../../static/pattern_detail_icons/diy_r.png',
            text: '自定义'
          },
          {
            image: '../../static/pattern_detail_icons/rec_r.png',
            text: '推荐'
          }
        ],
        list: [
          {
            title: 'XXX',
            coal: '. . .',
            calorie: '. . .',
            image: '../../static/pattern_detail_icons/ic_1.jpg'
          },
          {
            title: 'XXX',
            coal: '. . .',
            calorie: '. . .',
            image: '../../static/pattern_detail_icons/ic_1.jpg'
          },
          {
            title: 'XXX',
            coal: '. . .',
            calorie: '. . .',
            image: '../../static/pattern_detail_icons/ic_1.jpg'
          },
          {
            title: 'XXX',
            coal: '. . .',
            calorie: '. . .',
            image: '../../static/pattern_detail_icons/ic_1.jpg'
          },
          {
            title: 'XXX',
            coal: '. . .',
            calorie: '. . .',
            image: '../../static/pattern_detail_icons/ic_1.jpg'
          },
          {
            title: 'XXX',
            coal: '. . .',
            calorie: '. . .',
            image: '../../static/pattern_detail_icons/ic_1.jpg'
          },
          {
            title: 'XXX',
            coal: '. . .',
            calorie: '. . .',
            image: '../../static/pattern_detail_icons/ic_1.jpg'
          },
          {
            title: 'XXX',
            coal: '. . .',
            calorie: '. . .',
            image: '../../static/pattern_detail_icons/ic_1.jpg'
          },
          {
            title: 'XXX',
            coal: '. . .',
            calorie: '. . .',
            image: '../../static/pattern_detail_icons/ic_1.jpg'
          },
          {
            title: 'XXX',
            coal: '. . .',
            calorie: '. . .',
            image: '../../static/pattern_detail_icons/ic_1.jpg'
          },
          {
            title: 'XXX',
            coal: '. . .',
            calorie: '. . .',
            image: '../../static/pattern_detail_icons/ic_1.jpg'
          },
          {
            title: 'XXX',
            coal: '. . .',
            calorie: '. . .',
            image: '../../static/pattern_detail_icons/ic_1.jpg'
          },
          {
            title: 'XXX',
            coal: '. . .',
            calorie: '. . .',
            image: '../../static/pattern_detail_icons/ic_1.jpg'
          },
          {
            title: 'XXX',
            coal: '. . .',
            calorie: '. . .',
            image: '../../static/pattern_detail_icons/ic_1.jpg'
          },
          {
            title: 'XXX',
            coal: '. . .',
            calorie: '. . .',
            image: '../../static/pattern_detail_icons/ic_1.jpg'
          },
          {
            title: 'XXX',
            coal: '. . .',
            calorie: '. . .',
            image: '../../static/pattern_detail_icons/ic_1.jpg'
          },
          {
            title: 'XXX',
            coal: '. . .',
            calorie: '. . .',
            image: '../../static/pattern_detail_icons/ic_1.jpg'
          }
        ]
      };
    },
    methods: {
      toPopup() {
        uni.navigateTo({
          url: '../popup/popup'
        })
      },
      todiy() {
        uni.navigateTo({
          url: '../diy/diy'
        })
      }
    }
  }
</script>

<style lang="scss">
  .navigation-box {
    height: 120px;
    background-color: #25919b;
    border-radius: 15px 15px 0 0;
    position: relative;
    overflow: hidden;
    
    display: flex;
    justify-content: space-around;
    align-items: center;
    
    .navigation-tab {
      width: 80px;
      margin-bottom: 10px;
      .img-box {
        display: flex;
        justify-content: center;
        image {
          height: 50px;
          width: 50px;
        }
      }
      .text-box {
        text-align: center;
        line-height: 20px;
        display: flex;
        justify-content: center;
        color: #FFFFFF;
        font-weight: bold;
      }
    }
    
    &::after {
      content: '  ';
      display: block;
      width: 100%;
      height: 40px;
      background-color: #FFFFFF;
      position: absolute;
      bottom: 0;
      left: 0;
      border-radius: 15px 15px 0 0;
      transform: translateY(50%);
    }
  }
  
  .list-box {
    background-color: #FFFFFF;
    border-radius: 15px 15px 0 0;
    
    .list-item {
      margin-bottom: 10px;
      background-color: #d7f3f6;
      display: flex;
      justify-content: space-around;
      
      .list-item-left-box {
        width: 200px;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        color: #25919b;
        margin: 10px 0;
        
        border-bottom: 1px dashed #25919b;
        .list-item-left-box-coalAndCalorie {
          display: flex;
          margin-bottom: 5px;
        }
      }
      
      .list-item-right-box {
        display: flex;
        align-items: center;
        image {
          height: 60px;
          width: 85px;
        }
      }
    }
  }
</style>
