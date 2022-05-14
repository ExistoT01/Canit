<template>
  <view class="big-box">
    <!-- 海报 -->
    <view class="post-box">
      <image src="../../static/square_icons/activity.jpg" mode="scaleToFill"></image>
    </view>

    <!-- 内容 -->
    <view class="content-box">
      <view class="content-box-summary">
        <!-- 活动名称 -->
        <view class="content-box-item">
          <text style="font-weight: bold;">活动名称：</text>名称
        </view>
        <!-- 主办单位 -->
        <view class="content-box-item">
          <text style="font-weight: bold;">主办单位：</text>单位
        </view>
        <!-- 报名时间 -->
        <view class="content-box-item">
          <text style="font-weight: bold;">报名时间：</text>时间
        </view>
        <!-- 活动时间 -->
        <view class="content-box-item">
          <text style="font-weight: bold;">活动时间：</text>时间
        </view>
        <view class="content-box-item">
          <text style="font-weight: bold;">活动详情：</text>
          <text class="clickText" @click="toggle('center')">点击获取详情</text>
        </view>
      </view>

    </view>
    
    <view>
    	<!-- 普通弹窗 -->
    	<uni-popup ref="popup" background-color="#fff" @change="change">
    		<view class="popup-content" :class="{ 'popup-height': type === 'left' || type === 'right' }"><text
    				class="text">活动详情活动详情活动详情活动详情活动详情活动详情活动详情活动详情活动详情活动详情活动详情活动详情活动详情活动详情活动详情活动详情活动详情活动详情活动详情活动详情活动详情活动详情</text></view>
    	</uni-popup>
    </view>

    <!-- 底部栏 -->
    <view class="bottom-box">
      <uni-goods-nav :fill="true" :options="options" :buttonGroup="buttonGroup" @click="onClick"
        @buttonClick="buttonClick" />
    </view>

  </view>
</template>

<script>
  export default {
    data() {
      return {
        type: 'center',
        options: [{
          icon: 'star',
          text: '收藏'
        }, {
          icon: 'chat',
          text: '评论',
        }, ],
        buttonGroup: [{
          text: '我要参加',
          backgroundColor: '#5dbec7',
          color: '#fff'
        }, ]
      };
    },
    methods: {
      onClick(e) {
        uni.showToast({
          title: `点击${e.content.text}`,
          icon: 'none'
        })
      },
      buttonClick(e) {
        console.log(e)
      },
      toggle(type) {
        this.type = type
        console.log("ok")
        // open 方法传入参数 等同在 uni-popup 组件上绑定 type属性
        this.$refs.popup.open(type)
      },
    }
  }
</script>

<style lang="scss">
  page,
  .big-box {
    width: 100%;
    background-color: #f3f3f3;
  }

  .post-box {
    height: 200px;
    width: 100%;

    image {
      height: 100%;
      width: 100%;
    }
  }

  .content-box {
    height: 320px;
    background-color: #d7f3f6;
    

    margin: 10px 20px 0 20px;
    .content-box-summary {
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-around;
      
      .content-box-item {
        margin: 0 30px 0 30px;
        box-shadow: #BBBBBB 3px 3px 10px; 
        background-color: #FFFFFF;
        color: #458d93;
        padding: 0 40px;
        margin-top: 8px;
        display: flex;
      }
    }
    
  }

  .bottom-box {
    background-color: #FFFFFF;
    display: flex;
    flex-direction: column;
    position: fixed;
    left: 0;
    right: 0;
    bottom: 0;
  }
</style>
