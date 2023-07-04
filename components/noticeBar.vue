<template>
	<view class="notice_bar">
		<view class="icon">
		</view>
		<swiper circular="true" vertical="true" autoplay="true" interval="5000" duration="1000" class="swiper_box" :touchable="false" :disable-touch="true">
			<swiper-item v-for="(item,index) in noticeList" :key="index" class="swiper_box_item" @touchmove.stop>
				<view style="width: 100%;height: 54rpx;">
					<span class="txt1">{{item.message}}</span>
					<span class="txt2">{{item.date}} </span>
				</view>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		name: "noticeBar",
		props:{
			noticeList: {
				type: Array,
				default:[
					
				]
			},
		},	
		data(){
			return{

			}
			
		}
		
	}
</script>

<style lang="scss" scoped>
	.notice_bar{
		width: 100%;
		height: 80rpx;
		background-color: #fff;
		border-radius: 8rpx;
		display: flex;
		align-items: center;
		.icon{
			width: 7rpx;
			height: 32rpx;
			margin-left: 30rpx;
			border-radius: 7rpx;
			background-color: #5596F2;
		}
		.swiper_box{
			width: 620rpx;
			height: 54rpx;
			.swiper_box_item{
				width: 100%;
				height: 54rpx;
				line-height: 54rpx;
				margin-left: 18rpx;
				.txt1{
					width: 400rpx;
					overflow:hidden; 
					text-overflow:ellipsis;
					white-space: nowrap;
					font-size: 28rpx;
					color: #16161A;
					line-height: 54rpx;
					float: left;
				}
				.txt2{
					
					font-size: 24rpx;
					color: #A8A8AF;
					line-height: 54rpx;
					float: right;
					margin-right: 30rpx;
				}
				
			}
			
		}
	}
</style>
