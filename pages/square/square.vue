<template>
  <view>
    <!-- 导航栏 -->
    <view class="navigation-box">
      <!-- 头像 -->
      <view class="thumb-box">
        <!-- <uni-icons type="contact" size="30"></uni-icons> -->
        <image src="../../static/square_icons/thumb.jpg" mode="scaleToFill"></image>
      </view>
      <!-- 分页 -->
      <view class="tab-container">
        <view class="tab-box">
          <text> 推 荐 </text>
        </view>
        <view class="tab-box">
          <text> 附 近 </text>
        </view>
        <view class="tab-box">
          <text> 关 注 </text>
        </view>
      </view>
      <!-- 搜索 -->
      <view class="search-box">
        <!-- <uni-icons type="search" size="30"></uni-icons> -->
        <image src="../../static/square_icons/search.png" mode=""></image>
      </view>
    </view>


    <!-- 轮播图 -->
    <uni-swiper-dot :info="info" :current="current" field="content" :mode="mode" :dotsStyles="dotStyle">
      <swiper class="swiper-box" @change="change" @click="toDetail" circular>
        <swiper-item v-for="(item ,index) in info" :key="index">
          <view class="swiper-item">
            <image :src="item.content" mode="widthFix"></image>
          </view>
        </swiper-item>
      </swiper>
    </uni-swiper-dot>

    <!-- <image src="../../static/square_icons/square_content%20(1).jpg" mode=""></image> -->

    <!-- 达人展示 -->
      <!-- 标题 -->
      <view class="title-box">
        <text>* 达 人 展 示 *</text>
      </view>
    
    <view class="content-container">
      <uni-card :cover="cover" @click="onClick">
        <image slot='cover' mode="widthFix" :src="cover"></image>
        <view slot="actions" class="card-actions">
          <view class="card-actions-item" @click="actionsClick('点赞')">
            <uni-icons type="heart" size="18" color="#999"></uni-icons>
            <!-- <text class="card-actions-item-text">点赞</text> -->
          </view>
        </view>
      </uni-card>

      <uni-card :cover="cover" @click="onClick">
        <image slot='cover' mode="widthFix" :src="cover"></image>
        <view slot="actions" class="card-actions">
          <view class="card-actions-item" @click="actionsClick('点赞')">
            <uni-icons type="heart" size="18" color="#999"></uni-icons>
            <!-- <text class="card-actions-item-text">点赞</text> -->
          </view>
        </view>
      </uni-card>

      <uni-card :cover="cover" @click="onClick">
        <image slot='cover' mode="widthFix" :src="cover"></image>
        <view slot="actions" class="card-actions">
          <view class="card-actions-item" @click="actionsClick('点赞')">
            <uni-icons type="heart" size="18" color="#999"></uni-icons>
            <!-- <text class="card-actions-item-text">点赞</text> -->
          </view>
        </view>
      </uni-card>

      <uni-card :cover="cover" @click="onClick">
        <image slot='cover' mode="widthFix" :src="cover"></image>
        <view slot="actions" class="card-actions">
          <view class="card-actions-item" @click="actionsClick('点赞')">
            <uni-icons type="heart" size="18" color="#999"></uni-icons>
            <!-- <text class="card-actions-item-text">点赞</text> -->
          </view>
        </view>
      </uni-card>
    </view>

    <!-- 发布按钮 -->
    <view class="upLoad-box">
      <view class="upLoad-text">
        <text>+</text>
      </view>     
    </view>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        // 设备高度
        wh : 0,
        info: [{
          content: "../../static/swiper_list/square_img%20(1).jpg"
        }, {
          content: "../../static/swiper_list/square_img%20(2).jpg"
        }, {
          content: "../../static/swiper_list/square_img%20(3).jpg"
        }, {
          content: "../../static/swiper_list/square_img%20(4).jpg"
        }, {
          content: "../../static/swiper_list/square_img%20(5).jpg"
        }],
        current: 0,
        mode: 'round',
        dotStyle: {
          backgroundColor: 'rgba(85, 85, 85, 0.3)',
          // border: '1px rgba(255, 255, 255, 0.3) solid',
          color: '#fff',
          selectedBackgroundColor: 'rgba(255, 255, 255, 0.9)',
          // selectedBorder: '1px rgba(255, 255, 255, 0.9) solid'
        },
        cover: '../../static/square_icons/square_content%20(1).jpg',
      };
    },
    methods: {
      change(e) {
        this.current = e.detail.current;
      },
      toDetail() {
        uni.navigateTo({
          url: '../../subpkg/activity/activity'
        })
      },
      onClick(e) {
        console.log(e)
      },
      actionsClick(text) {
        uni.showToast({
          title: text,
          icon: 'none'
        })
      }
    },
    onLoad(){
      const sysInfo = uni.getSystemInfoSync()
      this.wh = sysInfo.windowHeight
    }

  }
</script>

<style lang="scss">
  // 轮播图
  .swiper-box {
    height: 140px;
    width: 100%;

    .swiper-item {
      width: 100%;
      height: 100%;

      image {
        width: 100%;
      }
    }
  }

  .navigation-box {
    height: 60px;
    display: flex;
    justify-content: space-between;
    border-bottom: 1px solid #D3D3D3;

    .thumb-box {
      // background-color: #0A98D5;
      width: 60px;

      image {
        width: 70%;
        height: 70%;
        border-radius: 60px;
        margin-top: 8px;
        margin-left: 8px;
      }
    }

    .tab-container {
      display: flex;
      width: 240px;
      // background-color: #007AFF;
      justify-content: space-around;
      align-items: center;

      .tab-box {
        border: 1px solid #5dbec7;
        border-radius: 15px;

        text {
          color: #5dbec7;
          padding: 0 5px;
        }
      }
    }

    .search-box {
      // background-color: #007AFF;
      width: 60px;

      image {
        width: 30px;
        height: 30px;
        margin-top: 12px;
        margin-left: 8px;
      }
    }
  }

  .title-box {
    // background-color: #0A98D5;
    height: 40px;
    text-align: center;
    align-items: center;
    border: 1px solid #5dbec7;


    text {
      line-height: 40px;
      font-size: 14px;
    }
  }

  .content-container {
    display: flex;
    flex-wrap: wrap;

    align-items: center;
    justify-content: space-between;

    padding: 0 5px;

    .uni-card {
      height: 170px;
      width: 130px;
      display: flex;
      flex-direction: column;
      align-items: center;

      .card-actions {
        // background-color: #007AFF;
        line-height: 40px;
        display: flex;
        justify-content: space-around;
        margin-top: -15px;
      }

      image {
        height: 150px;
        width: 150px;
      }
    }
  }
  
  .upLoad-box {
    position: sticky;
    bottom: 0;
    z-index: 999;
    height: 28px;
    // background-color: #007AFF;
    display: flex;
    justify-content: center;
    
    .upLoad-text {
      
      height: 28px;
      width: 50px;
      background-color: #5dbec7
;
      display: flex;
      
      text-align: center;
      justify-content: center;
      
      border-radius: 80px 80px 0 0;
      
      text {
        line-height: 28px;
        color: #FFFFFF;
        font-size: 30px;
        font-weight: lighter;
      }
    }
  }
</style>
