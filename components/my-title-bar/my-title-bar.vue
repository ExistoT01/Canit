<template>
	<view class="my-title-bar">
		<view class="my-title-dot"></view>
		<view class="my-title-text">{{title}}</view>
	</view>
</template>

<script>
export default {
	name: "title-bar",
	props: {
		title: {
			type: String,
			default: ''
		},
	},
	mounted() {
		
	},
	methods:{
	}
}
</script>


<style>
	.my-title-bar{
		display: flex;
		flex-direction: row !important;
		flex-wrap: nowrap;
		align-items: center;
		height: 40px;
	}
	
	.my-title-dot {
		border-radius: 10px;
		background-color: #409EFF;
		width: 5px;
		height: 16px;
		margin-left: 8px;
	}
	
	.my-title-text {
		font-size: 17px;
		color: #666666;
		margin-left: 8px;
		line-height: 22px;
		height: 22px;
		font-weight: bold;
	}
</style>