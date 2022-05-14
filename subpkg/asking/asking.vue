<template>
  <view>
    <!-- 标题 -->
    <view class="title-box">
      这是问题
    </view>
    <!-- 问题 -->
    <view class="content-box">
      补充问题中…………
    </view>
    <!-- 工具 -->
    <view class="tools-bar">
      <!-- 具体工具 -->
      <view class="tools-box">
        <image src="../../static/askpage_icons/pic.png"></image>
        <image src="../../static/askpage_icons/at.png"></image>
        <image src="../../static/askpage_icons/hashtag.png"></image>
      </view>
      <!-- 发布按钮 -->
      <view class="submit-box">
        <view class="submit-button">
          发    布
        </view>
      </view>     
    </view>
    <!-- 输入 -->
    <view class="input-box">
      请输入…………
    </view>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        
      };
    }
  }
</script>

<style lang="scss">
  .title-box {
    line-height: 40px;
    border-bottom: 1px solid #5dbec7;
    font-size: 18px;
    color: #5dbec7;
    margin: 0 10px 0 10px;
  }
  
  .content-box {
    height: 360px;
    border-bottom: 1px solid #5dbec7;
    font-size: 14px;
    color: #5dbec7;
    margin: 5px 10px 0 10px;
  }
  
  .tools-bar {
    height: 40px;
    display: flex;
    justify-content: space-between;
    margin: 5px
     10px 0 10px;
    .tools-box {
      image {
        height: 40px;
        width: 40px;
      }
    }
    
    .submit-box {
      width: 60px;
      display: flex;
      justify-content: center;
      align-items: center;
      .submit-button {
        display: flex;
        justify-content: center;
        width: 60px;
        height: 20px;
        text-align: center;
        background-color: #5dbec7;
        color: #FFFFFF;
        border-radius: 20px;
      }
    }
    
  }
  
  .input-box {
    font-size: 12px;
    color: #5dbec7;
    margin: 5px 10px 0 10px;
  }
</style>
