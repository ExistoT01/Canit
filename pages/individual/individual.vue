<template>
  <view class="login-container" v-if="!nickName">
    <uni-icons type="contact-filled" size="100" color="#AFAFAF"></uni-icons>
    <button type="primary" class="btn-login" @click="getUserProfile">一键登录</button>
    <text class="tips-text">登录后尽享更多权益</text>
  </view>
  
  
  <view class="logon-container" v-else>
    <!-- 头像和昵称区域 -->
    <view class="top-box">
      <image :src="avatarUrl" class="avatar"></image>
      <view class="nickname">{{nickName}}</view>
    </view>
    
    <!-- 面板区域 -->
    <view class="panel-list">
      <!-- 第1个面板 -->
      <view class="panel">
        <view class="panel-body">
          <view class="panel-item">
            <image src="../../static/individual_icons/like.png" mode=""></image>
          </view>
          <view class="panel-item">
            <image src="../../static/individual_icons/fav.png" mode=""></image>
          </view>
          <view class="panel-item">
            <image src="../../static/individual_icons/collection.png" mode=""></image>
          </view>
        </view>
      </view>
    
      <!-- 第2个面板 -->
      <view class="panel"> 
        <view class="panel-body">
          <view class="panel-item">
            <image src="../../static/individual_icons/coal.png" class="icon"></image>
            <text>碳足迹</text>
          </view>
          <view class="panel-item">
            <image src="../../static/individual_icons/calories.png" class="icon"></image>
            <text>卡路里 / 周</text>
          </view>
        </view>
      </view>
    
      <!-- 第3个面板 -->
      <view class="panel">
        <view class="panel-list-item">
          <view class="panel-list-item-name">
            <image src="../../static/individual_icons/health.png" mode=""></image>
            <text>健康数据</text>
          </view>         
          <uni-icons type="arrowright" size="15"></uni-icons>
        </view>
        <view class="panel-list-item">
          <view class="panel-list-item-name">
            <image src="../../static/individual_icons/rank.png" mode=""></image>
            <text>排行榜单</text>
          </view>            
          <uni-icons type="arrowright" size="15"></uni-icons>
        </view>
        <view class="panel-list-item" @click="logout">
          <view class="panel-list-item-name">
            <image src="../../static/individual_icons/forest.png" mode=""></image>
            <text>我的森林</text>
          </view>         
          <uni-icons type="arrowright" size="15"></uni-icons>
        </view>
        <view class="panel-list-item">
          <view class="panel-list-item-name">
            <image src="../../static/individual_icons/activity.png" mode=""></image>
            <text>活动进度</text>
          </view>         
          <uni-icons type="arrowright" size="15"></uni-icons>
        </view>
        <view class="panel-list-item">
          <view class="panel-list-item-name">
            <image src="../../static/individual_icons/post.png" mode=""></image>
            <text>我的帖子</text>
          </view>          
          <uni-icons type="arrowright" size="15"></uni-icons>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        nickName: '',
        avatarUrl: '',
        authResult: {}
      };
    },
    methods: {
      getUserProfile() {
        let code = ''
        uni.login({
          provider: "weixin",
          success: function(loginRes) {
            console.log("getUserProfile", loginRes);
            code = loginRes.code;
            console.log(code)
          },
        });

        uni.getUserProfile({
          desc: '登录',
          success: (res) => {
            console.log(res);
            let info = JSON.parse(res.rawData);
            console.log(info);
            this.nickName = info.nickName
            this.avatarUrl = info.avatarUrl
          }
        })       

      }
    },
  }
</script>

<style lang="scss">
  .login-container {
    height: 750rpx;
    background-color: #F8F8F8;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: relative;
    overflow: hidden;

    &::after {
      content: ' ';
      display: block;
      width: 100%;
      height: 40px;
      background-color: white;
      position: absolute;
      bottom: 0;
      left: 0;
      border-radius: 100%;
      transform: translateY(50%);
    }

    .btn-login {
      width: 90%;
      border-radius: 100px;
      margin: 15px 0;
      background-color: #5dbec7;
    }

    .tips-text {
      font-size: 12px;
      color: gray;
    }
  }

  
  .logon-container {
    height: 100%;
    background-color: #F4F4F4;
  
    .top-box {
      height: 360rpx;
      background-color: #5dbec7;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
  
      .avatar {
        width: 90px;
        height: 90px;
        border-radius: 45px;
        border: 2px solid #FFF;
        box-shadow: 0 1px 5px black;
      }
  
      .nickname {
        font-size: 16px;
        color: #FFF;
        font-weight: bold;
        margin-top: 10px;
      }
    }
  }
  
  .panel-list {
    padding: 0 10px;
    position: relative;
    top: -10px;
  
    .panel {
      background-color: white;
      border-radius: 3px;
      margin-bottom: 8px;
  
      .panel-body {
        display: flex;
        justify-content: space-around;
  
        .panel-item {
          display: flex;
          flex-direction: column;
          align-items: center;
          justify-content: space-around;
          padding: 10px 0;
          font-size: 13px;
          image {
            height: 32px;
            width: 32px;
          }
  
          .icon {
            width: 35px;
            height: 35px;
          }
          
          text {
            color: #458d93;
            font-weight: bold;
          }
        }
      }
    }
  }
  
  .panel-list-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 15px;
    padding: 0 10px;
    line-height: 45px;
    .panel-list-item-name {
      width: 100px;
      display: flex;
      font-size: 15px;
      align-items: center;
      justify-content: space-around;
      image {
        height: 20px;
        width: 20px;
      }
    }
  }
  
</style>
