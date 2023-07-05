<template>
	<view class="fun_box_one">
		<view class="item_box" :class="{'top_line': index > 0 }" v-for="(item,index) in list">
			<image style="width: 40rpx;height: 40rpx;" :src="item.img"></image>
			<view class="name">{{item.name}}</view>
			<view class="icon"><u-icon  name="arrow-right" size="25" color="#C6C6CF"></u-icon></view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			list:{
				type: Array,
				default:[ ]
			}
		},
		data() {
			return {
				
			}
		},

		methods: {
	
		}
	}
</script>

<style lang="scss">
.fun_box_one{
	width: 686rpx;
	min-height: 120rpx;
	border-radius: 12rpx;
	margin: 0 auto;
	background-color: #fff;
	.item_box{
		height: 120rpx;
		margin: 0 32rpx;
		display: flex;
		align-items: center;
		.name{
			width: 400rpx;
			font-size: 28rpx;
			font-weight: 400;
			color: #16161A;
			margin-left: 24rpx;
		}
		.icon{
			width: 32rpx;
			height: 32rpx;
			margin-left: 131rpx;
			display: flex;
			align-items: center;
		}
	}
	.top_line{
		border-top: 1rpx solid #EEEEEE;
	}
}
</style>