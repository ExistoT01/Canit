<template>
  <view>
    <!-- 搜索栏 -->
    <uni-search-bar @confirm="search" @input="input" ></uni-search-bar>   
    
    <!-- 问题列表 -->
    <view class="questions-container" v-for="(item, index) in questions" :key="index">
      <view class="question-box">
        <view class="question-item">
          <!-- 标题 -->
          <view class="question-title">
            {{item.title}}
          </view>
          <!-- 内容 -->
          <view class="question-content">
            {{item.content}}
          </view>
          <!-- 详情按钮 -->
          <view class="detail-container">
            <view class="detail-box" >
              >
            </view>
          </view>        
        </view>
      </view>
    </view>
    
    <!-- 底部结构 -->
    <view class="bottom-box">
      <view class="ask-box" @click="toAskPage">
        我要提问
      </view>
      
      <view class="answer-box" @click="toAnsPage">
        我要回答
      </view>
    </view>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        questions: [
          {
            title: '这是标题',
            content: '这是大概这是大概这是大概这是大概这是大概……',
          },
          {
            title: '这是标题',
            content: '这是大概这是大概这是大概这是大概这是大概……',
          },
          {
            title: '这是标题',
            content: '这是大概这是大概这是大概这是大概这是大概……',
          },
          {
            title: '这是标题',
            content: '这是大概这是大概这是大概这是大概这是大概……',
          },
          {
            title: '这是标题',
            content: '这是大概这是大概这是大概这是大概这是大概……',
          },
          {
            title: '这是标题',
            content: '这是大概这是大概这是大概这是大概这是大概……',
          },
          {
            title: '这是标题',
            content: '这是大概这是大概这是大概这是大概这是大概……',
          },
          {
            title: '这是标题',
            content: '这是大概这是大概这是大概这是大概这是大概……',
          },
          {
            title: '这是标题',
            content: '这是大概这是大概这是大概这是大概这是大概……',
          },
          {
            title: '这是标题',
            content: '这是大概这是大概这是大概这是大概这是大概……',
          },
          {
            title: '这是标题',
            content: '这是大概这是大概这是大概这是大概这是大概……',
          },
          {
            title: '这是标题',
            content: '这是大概这是大概这是大概这是大概这是大概……',
          },
          {
            title: '这是标题',
            content: '这是大概这是大概这是大概这是大概这是大概……',
          },
          {
            title: '这是标题',
            content: '这是大概这是大概这是大概这是大概这是大概……',
          },
          {
            title: '这是标题',
            content: '这是大概这是大概这是大概这是大概这是大概……',
          },
        ]
      };
    },
    
    methods: {
      toAskPage() {
        uni.navigateTo({
          url: '../../subpkg/asking/asking'
        })
      },
      toAnsPage() {
        uni.navigateTo({
          url: '../../subpkg/anspage_recommend/anspage_recommend'
        })
      }
    }
    
  }
</script>

<style lang="scss">
  .questions-container {
    
    .question-box {
      height: 100px;
      background-color: #d7f3f6;
      margin-top: 10px;
      margin-left: 10px;
      margin-right: 10px;
      border-radius: 10px;
      display: flex;
      justify-content: center;
      align-items: center;
      
      .question-item {
        height: 72%;
        width: 92%;
        background-color: #FFFFFF;
        .question-title {
          margin: 0 5px 0 5px;
          font-weight: bold;
          font-size: 14px;
          color: #878787;
          border-bottom: 1px solid #878787;
        }
        .question-content {
          margin: 0 5px 0 5px;
          color: #878787;
          
        }
        
        .detail-container {
          display: flex;
          justify-content: flex-end;
          .detail-box {
            width: 20px;
            height: 20px;
            border-radius: 80px;
            background-color: #5dbec7;
            display: flex;
            justify-content: center;
            align-items: center;
            
            color: #FFFFFF;
            font-size: 20px;
            
            margin-right: 10px;
          }
        }
        
      }
    }
  }
  
  .bottom-box {
    position: sticky;
    bottom: 0;
    z-index: 999;
    
    height: 40px;
    background-color: #FFFFFF;
    border-top: 1px solid #5dbec7;
    
    
    display: flex;
    justify-content: space-around;
    align-items: center;
    .ask-box {
      width: 100px;
      line-height: 24px;
      text-align: center;
      border: 1px solid #5dbec7;
      border-radius: 20px;
      color: #5dbec7;
    }
    
    .answer-box {
      width: 100px;
      line-height: 24px;
      text-align: center;
      border: 1px solid #5dbec7;
      border-radius: 20px;
      color: #5dbec7;
    }
  }
</style>
