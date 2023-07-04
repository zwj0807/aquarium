<template>
	<view class="box">
		<image class="img" src="/static/nodata.png"></image>
		<view class="text">此组暂无设备～</view>
	</view>
</template>

<script>
	export default {
		name:"nodata",
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss" scoped>
.box{
	display: flex;
	justify-content: center;
	align-items: center;
	flex-direction: column;
	.img{
		width: 300rpx;
		height: 229rpx;
	}
	.text{
		margin-top: 24rpx;
		font-size: 28rpx;
		font-weight: 400;
		color: #797980;
	}
}
</style>