<template>
	<view>
		<view style="height:176rpx;"><view class="nav_bar"><view class="nav_bar_title" :style="{paddingTop: `${systemInfo.navHeight}rpx` }">提醒</view></view></view>
		<view class="main_box">
			<view class="box_title">计划提醒</view>
			<view class="remind_card" v-for="(item,index) in 3" :key="index">
				<view class="card_title_line">
					<image class="card_img" src="/static/remind/filterchange_icon.png"></image>
					<view class="card_title">滤材更换</view>
					<view class="icon"><u-icon  name="arrow-right"color="#C6C6CF"></u-icon></view>
				</view>
				<view class="card_info_box">
					<view class="info_label_line">
						<text class="info_label">时间</text>
						<text class="info_text">2023/10/12 08:00</text>
						<text class="info_day">160天后</text>
					</view>
					<view class="info_label_line">
						<text class="info_label">重复</text>
						<text class="info_text">1周</text>
					</view>
					<view class="info_label_line">
						<text class="info_label">备注</text>
						<text class="info_text">客厅设备更换，不能保留！</text>
					</view>
					<view class="success_box">标记完成</view>
				</view>
			</view>

		</view>
		<view style="height: 96rpx;">
			<view class="add_remind">
				<u-button color="#5596F2"  text="新建提醒" @click="addRemind"></u-button>
			</view>
		</view>
	</view>
</template>

<script>
	import {
		mapGetters
	} from 'vuex';
	export default {
		components: {  },
		data() {
			return {

			}
		},
		onLoad() {

		},
		computed: {
			...mapGetters(['systemInfo']),
		},
		methods: {
			addRemind(){
				uni.navigateTo({
					url:'/remind/addRemindOne'
				})
			},
		}

	}
</script>

<style lang="scss" scoped>
.nav_bar{
	width: 100%;
	height: 176rpx;
	position: fixed;
	top: 0;
	left: 0;
	background: url(https://www.jumidongli.com/template/pc/static/demoImg/remind/remind_bg.png) no-repeat;
	background-size: 100% 176rpx;
	.nav_bar_title{
		font-size: 34rpx;
		font-weight: 600;
		color: #16161A;
		padding-left: 32rpx;
		margin-top: 28rpx;
	}
}
.main_box{
	padding: 0 32rpx;
	.box_title{
		font-size: 40rpx;
		font-weight: 600;
		color: #16161A;
		margin: 32rpx 0;
	}
	.remind_card{
		min-height: 312rpx;
		background: #FFFFFF;
		border-radius: 12rpx;
		overflow: hidden;
		margin-bottom: 24rpx;
		.card_title_line{
			height: 64rpx;
			margin: 20rpx 24rpx;
			display: flex;
			align-items: center;
			.card_img{
				width: 64rpx;
				height: 64rpx;
			}
			.card_title{
				margin-left: 8rpx;
				font-size: 28rpx;
				font-weight: 400;
				color: #16161A;
			}
			.icon{
				margin-left: 425rpx;
			}
		}
		.card_info_box{
			min-height: 88rpx;
			background: #F6F7F9;
			border-radius: 12rpx;
			margin: 0 24rpx;
			padding: 0rpx 24rpx 24rpx 24rpx;
			.info_label_line{
				height: 40rpx;
				display: flex;
				align-items: center;
				padding-top: 24rpx;
				.info_label{
					font-size: 28rpx;
					font-weight: 400;
					color: #797980;
				}
				.info_text{
					font-size: 28rpx;
					font-weight: 400;
					color: #16161A;
					margin-left: 40rpx;
				}
				.info_day{
					margin-left: 157rpx;
					font-size: 28rpx;
					font-family: PingFangSC-Regular, PingFang SC;
					font-weight: 400;
					color: #16161A;
				}
			}
			.success_box{
				float: right;
				width: 152rpx;
				height: 56rpx;
				border-radius: 29rpx;
				border: 2rpx solid #5596F2;
				font-size: 28rpx;
				font-weight: 600;
				color: #5596F2;
				line-height: 56rpx;
				text-align: center;
				margin-top: 56rpx;
				margin-bottom: 40rpx;
			}
		}
	}
}
.add_remind{
	width: calc(100% - 64rpx);
	height: 96rpx;
	padding: 0 32rpx;
	background: #FFFFFF;
	position: fixed;
	bottom: 0;
	left: 0;

}
/deep/.u-icon__icon.data-v-172979f2{
	font-size: 26rpx !important;
}
/deep/.u-button.data-v-3bf2dba7{
	height: 100% !important;
}
</style>
