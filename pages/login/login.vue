<template>
	<view>
		<image class="icon" src="/static/liangxianghe.png"></image>
		<view class="denglu weixin">
			微信一键登录
		</view>
		<view class="denglu phone" @click="goPhone">
			手机号登录
		</view>
		<view class="agr_bottom">
			登录即代表您已同意<text>《靓相和用户协议》</text>和<text>《隐私协议》</text>
		</view>
	</view>
	
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		onLoad() {
			
			 
		},
		methods: {
			goPhone(){
				uni.navigateTo({
					url: '/pages/login/loginphone'
				})
			}
		}
	}
</script>
<style>
	page{
		background-color: #FFFFFF;
	}
</style>
<style lang="scss" scoped>
	.icon{
		width: 200rpx;
		height: 200rpx;
		margin: 120rpx 275rpx;
	}
	.denglu{
		width: 686rpx;
		height: 96rpx;
		border-radius: 8rpx;
		margin: 0 auto;
		font-size: 34rpx;
		font-weight: 600;
		line-height: 96rpx;
		text-align: center;
	}
	.weixin{
		color: #FFFFFF;
		background: #0ABF64;
	}
	.phone{
		margin-top: 24rpx;
		color: #16161A;	
		background: #F6F7F9;
	}
	.agr_bottom{
		position: fixed;
		width: 100%;
		bottom:100rpx;
		font-size: 24rpx;
		font-weight: 400;
		color: #A8A8AF;
		text-align: center;
		text{
			color: #748EB3;
		}
	}
</style>