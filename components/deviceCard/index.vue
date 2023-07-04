<template>
	<view style="display: flex; align-items: center; justify-content: center; width: 100%; height: 100%;">
		<view class="device_list_item">
			<view class="close"><u-icon name="close" color="#aacaf8"></u-icon></view>
			<view class="item_title_line">
				<image style="width:56rpx;height:56rpx;" src="/static/home/device_icon.png"></image>
				<text class="item_title">PH检测仪两行测试文本</text>
			</view>
			<view class="title_bottom_line"></view>
			<view class="item_info">
				<view class="info_line_one">
					<view class="line_one_box">
						<view class="line_one_val">7.5</view>
						<view class="line_one_txt">PH值</view>
					</view>
					<view class="line_two_box">
						<view class="line_one_val">439</view>
						<view class="line_one_txt">TDS值</view>
					</view>
				</view>
				<view class="info_line_two">
					<view class="line_one_box">
						<view class="line_one_val">26.8°C</view>
						<view class="line_one_txt">水温</view>
					</view>
				</view>
			</view>
			<view class="item_state_box_success">
				<text class="state"><text style="margin-right:14rpx;">·</text> 运行中</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "deviceCard",
		props:{
			info: {
				type: Object,
				default:{
					devName:'PH检测仪'
				}
			},
		},	
		data(){
			return{
	
			}
			
		}
		
	}
</script>

<style lang="scss" scoped>
	.device_list_item{
		width:331rpx;
		height: 429rpx;
		background: #5596F2;
		border-radius: 24rpx;
		position:relative;
		margin-bottom:24rpx;
		box-shadow: 0rpx 22rpx 22rpx -26rpx rgba(0,0,0,0.3);
		.close{
			position: absolute;
			top:16rpx;
			right:20rpx;
		}
		.item_title_line{
			display:flex;
			padding:16rpx;
			.item_title{
				width: 179rpx;
				height: 90rpx;
				text-overflow: -o-ellipsis-lastline;
				overflow: hidden;				//溢出内容隐藏
				text-overflow: ellipsis;		//文本溢出部分用省略号表示
				display: -webkit-box;			//特别显示模式
				-webkit-line-clamp: 2;			//行数
				line-clamp: 2;					
				-webkit-box-orient: vertical;	//盒子中内容竖直排列
				font-size: 32rpx;
				font-weight: 600;
				color: #FFFFFF;
				margin-left:15rpx;
			}
		}
		.title_bottom_line{
			height: 1rpx;
			border-bottom: 1rpx solid rgba(255,255,255,0.5);
		}
		.item_info{
			margin:24rpx 32rpx;
			.info_line_one{
				display: flex;
			}
			.info_line_two{
				margin-top: 24rpx;
				display: flex;
			}
			.line_one_box{
				margin-right: 64rpx;
			}
			.line_one_val{
				font-size: 36rpx;
				font-weight: 500;
				color: #FFFFFF;
			}
			.line_one_txt{
				font-size: 24rpx;
				font-weight: 400;
				color: rgba(255,255,255,0.7);
			}
		}
		.item_state_box_success{
			width: 100%;
			height:72rpx;
			background: #00D8D9;
			border-radius: 0rpx 0rpx 24rpx 24rpx;
			position: absolute;
			bottom:0;
			left:0;
			.state{
				font-size: 28rpx;
				font-weight: 500;
				color: #FFFFFF;
				line-height: 72rpx;
				margin-left: 32rpx;
			}
		}
		.item_state_box_fail{
			width: 100%;
			height:72rpx;
			background: #B0B1B3;
			border-radius: 0rpx 0rpx 24rpx 24rpx;
			position: absolute;
			bottom:0;
			left:0;
			.state{
				font-size: 28rpx;
				font-weight: 500;
				color: #FFFFFF;
				line-height: 72rpx;
				margin-left: 32rpx;
			}
		}
	}
</style>