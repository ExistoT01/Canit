<template>
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
				<view class="flex-item" v-for="(val,ind) in currWeek" :key="ind"  @click="changeDay(ind)">
					<view :class="{item:true,on:getDay(val.data) == getDay(selectDay.data)}" 
							v-text="val.data.getDate()">
					</view>
					<view class="isSpot" v-if="val.isTrue"></view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	const app = getApp();
	export default {
		name: "MyCalendar",
		props:["currData"],
		data() {
			return {
				GLOBAL:this.GLOBAL,
				// 选择的日期
				selectDay:{
					data:new Date(),
					// 是否需要加点
					isTrue:false,
				},
				// 当前日期，本周的某一天
				currDay:new Date(),
				// 本周
				currWeek:[],
				timelist:[]
			}
		},
		created() {
			this.currWeek = this.getWeeks(new Date());
			this.initTime();
		},
		methods: {
			initTime(){
				// selectDay.isTrue需要使用时在这个函数里面写你自己的代码
			},
			// 日历选择日期
			bindDateChange(e) {
				this.currDay = new Date(e.target.value);
				this.selectDay.data = new Date(e.target.value);
				for(var i =0;i<this.timelist.length;i++){
					if(this.timelist[i] == e.target.value){
						this.selectDay.isTrue = true;
					}
				}
				this.currWeek = this.getWeeks(e.target.value);
				this.$emit('func',this.selectDay)
				this.initTime();
			},
			// 本周选择日期
			changeDay(ind){
				this.currDay = this.currWeek[ind].data;
				this.selectDay = this.currWeek[ind];
				this.$emit('func',this.selectDay)
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
			preWeeks(){
				var time = this.currDay.getTime();
				var d = new Date(time - 7 * 24 * 60 * 60 * 1000);
				this.currDay = d;
				this.currWeek = this.getWeeks(d);
				this.initTime();
			},
			//获取下一周
			nextWeeks(){
				var time = this.currDay.getTime();
				var d = new Date(time + 7 * 24 * 60 * 60 * 1000);
				this.currDay = d;
				this.currWeek = this.getWeeks(d);
				this.initTime();
			},
			// 格式化日期
			getDay(time){
				let date = new Date(time);
				let year = date.getFullYear();
				let month = date.getMonth() + 1;
				let day = date.getDate();
				month = month > 9 ? month : '0' + month;;
				day = day > 9 ? day : '0' + day;
				return `${year}-${month}-${day}`;
			}
		}
	}
</script>

<style lang="scss" scoped>
	.my_calendar {
		width: 100%;
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
      
			.txt{
				vertical-align: middle;
				display: inline-block;
			}
			.leftTriangle,
			.rightTriangle {
				position: relative;
				z-index: 88;
				width: 15%;
				margin-top: 20rpx;
				.triagle{
					width: 0;
					height: 0;
				}
			}

			.leftTriangle {
				float: left;
				.triagle{
					border-top: 16rpx solid transparent;
					border-right: 20rpx solid #999;
					border-bottom: 16rpx solid transparent;
				}
			}

			.rightTriangle {
				float: right;
				.triagle{
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
						background-color: #93D879;
						-moz-border-radius: 50%;
						-webkit-border-radius: 50%;
						border-radius: 50%;
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
</style>
