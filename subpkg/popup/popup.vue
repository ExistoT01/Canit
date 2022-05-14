<template>
  <view class="big-box">
    <!-- 图片 -->
    <view class="img-box">
      <image src="../../static/popup_icons/pop-img.jpg" mode="widthFix"></image>
    </view>
    <!-- 内容 -->
    <view class="content-box">
      <!-- 数量 -->
      <view class="content-box-amount">
        1份
      </view>
      <view class="content-box-line">
        <!-- 重量 -->
        <view class="content-box-line-weight">
          约 X X 克
        </view>
        <!-- 卡路里 -->
        <view class="content-box-line-calorie">
          X X X 卡
        </view>
        <!-- 碳足迹 -->
        <view class="content-box-line-coal">
          X X X 碳足迹
        </view>
      </view>
      <!-- 输入框 -->
      <view class="content-box-input">
        
      </view>
      <!-- 单位 -->
      <view class="content-box-unit">
        <view class="content-box-unit-text">
          份 / 克
        </view>
      </view>
    </view>
    
    <!-- 按钮 -->
    <view class="button-box">
      <view class="button-box-button">
        确     定
      </view>
    </view>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        wh: 0
      };
    },
    onLoad() {
      const sysInfo = uni.getSystemInfoSync()
      this.wh = sysInfo.windowHeight - 40
    }
  }
</script>

<style lang="scss">
  page, .big-box {
    position: relative;
    &::after {
      content: '  ';
      display: block;
      position: absolute;
      bottom: 0;
      left: 0;
      height: 80px;
      width: 100%;
      border-radius: 15px;
      background-color: #5dbec7;
      transform: translateY(110px);
    }
  }
  .img-box {
    height: 260px;
    width: 100%;
    image {
      height: 100%;
      width: 100%;
      border-radius: 20px;
    }
  }
  
  .content-box {
    margin-top: 40px;
    padding: 0 60px;
    color: #5dbec7;
    height: 180px;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    
    .content-box-line {
      display: flex;
      justify-content: space-between;
    }
    
    .content-box-input {
      background-color: #f6f4f5;
      border-radius: 15px;
      height: 80px;
    }
    
    .content-box-unit {
      display: flex;
      justify-content: flex-end;    
    }
  }

  .button-box {
    height: 60px;
    display: flex;
    justify-content: flex-end;
    align-items: center;
    padding: 0 60px;
    .button-box-button {
      
      height: 30px;
      width: 60px;
      background-color: #5dbec7;
      line-height: 30px;
      text-align: center;
      color: #FFFFFF;
      border-radius: 15px;
    }
    
  }
  
</style>
