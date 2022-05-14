<template>
  <view>
    <!-- 导航栏 -->
    <view class="nav-bar-container">
      <view class="nav-bar-items-box" v-for="(item, index) in navbar" :key="index">
        <!-- 图片 -->
       <view class="nav-bar-items-imgbox">
          <image :src="item.icon"></image>
        </view>
        <!-- 文字 -->
        <view class="nav-bar-items-textbox">
          <text>{{item.text}}</text>
        </view>
      </view>
    </view>
    
    <!-- 列表 -->
    <view class="answer-list-container">
      <view class="answer-box" v-for="(item2, index2) in anslist" :key="index2">
        <!-- 标题 -->
        <view class="answer-title">
          <text>{{item2.text}}</text>
        </view>
        <!-- 回答按钮 -->
        <view class="answer-button-container">
          <view class="answer-button-box" >
            回   答
          </view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        wh: 0,
        navbar: [{
            "icon": '../../static/anspage_icons/recommend.png',
            "text": '推  荐'
          },
          {
            "icon": '../../static/anspage_icons/nearby.png',
            "text": '附  近'
          },
          {
            "icon": '../../static/anspage_icons/follow.png',
            "text": '关  注'
          }
        ],
        anslist: [
          {
            "text": '这是标题这是标题'
          },
          {
            "text": '这是标题这是标题'
          },
          {
            "text": '这是标题这是标题'
          },
          {
            "text": '这是标题这是标题'
          },
          {
            "text": '这是标题这是标题'
          },
          {
            "text": '这是标题这是标题'
          },
          {
            "text": '这是标题这是标题'
          },
          {
            "text": '这是标题这是标题'
          },
          {
            "text": '这是标题这是标题'
          },
          {
            "text": '这是标题这是标题'
          },
          {
            "text": '这是标题这是标题'
          },
          {
            "text": '这是标题这是标题'
          }
        ]
      }
    },
    methods: {

    },
    onLoad() {
      const sysInfo = uni.getSystemInfoSync()
      this.wh = sysInfo.windowHeight
    }
  }
</script>

<style lang="scss">
  .nav-bar-container {
    margin-top: 10px;
    height: 60px;
    display: flex;
    justify-content: space-around;
    
    .nav-bar-items-box {
      .nav-bar-items-imgbox {
        height: 40px;
        width: 40px;
        
        image {
          height: 100%;
          width: 100%;
        }
      }
      
      .nav-bar-items-textbox {
        margin-top: 5px;
        height: 20px;
        width: 40px;
        text-align: center;
        border: 1px solid #23909b;
        border-radius: 20px;
        
        text {
          line-height: 20px;
          font-size: 12px;
          color: #23909b;
        }
      }
    }
  }
  
  .answer-list-container {
    background-color: #d7f3f6;
    margin-top: 20px;
    
    .answer-box {
      transform: translateY(15px);
      background-color: #FFFFFF;
      height: 60px;
      margin-top: 15px;
      
      .answer-title {
        margin: 0 12px 0 12px;
        font-size: 16px;
        color: #808080;
        border-bottom: 1px solid #808080;
      }
      
      .answer-button-container {
        display: flex;
        justify-content: flex-end;
        .answer-button-box {
          width: 60px;
          margin-right: 20px;
          margin-top: 5px;
          color: #FFFFFF;
          background-color: #25919b;
          border-radius: 20px;
          text-align: center;
        }
      }
    }
  }
</style>
