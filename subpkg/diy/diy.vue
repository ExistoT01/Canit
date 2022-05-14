<template>
  <view class="big-box">
    <view class="list-container">
      <!-- 名称 -->
      <view class="list-item">
        <text class="uni-subtitle">名称：</text>
        <uni-easyinput class="uni-mt-5" trim="all" v-model="value" placeholder="请输入内容" @input="input"></uni-easyinput>
      </view>
      <!-- 分量 -->
      <view class="list-item">
        <text class="uni-subtitle">分量：</text>
        <uni-easyinput class="uni-mt-5" trim="all" v-model="value" placeholder="请输入内容" @input="input"></uni-easyinput>
      </view>
      <!-- 热量 -->
      <view class="list-item">
        <text class="uni-subtitle">热量：</text>
        <uni-easyinput class="uni-mt-5" trim="all" v-model="value" placeholder="请输入内容" @input="input"></uni-easyinput>
      </view>
      <!-- 碳足迹 -->
      <view class="list-item">
        <text class="uni-subtitle">碳足迹：</text>
        <uni-easyinput class="uni-mt-5" trim="all" v-model="value" placeholder="请输入内容" @input="input"></uni-easyinput>
      </view>
    </view>
    
    <!-- 确定 -->
    <button class="btn" type="default">确定</button>
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
  page, .big-box {
  }
  
  .list-container {
    display: flex;
    flex-direction: column;
    padding: 0 60px;
  }
  
  .list-item {
    margin-top: 30px;
    height: 80px;
    
    .uni-subtitle {
      color: #808080;
      font-size: 18px;
    }
    
    .uni-easyinput {
      margin-top: 20px;
    }
  }
  
  .btn {
    margin-top: 80px;
    margin-right: 80px;
    margin-left: 80px;
  }
</style>
