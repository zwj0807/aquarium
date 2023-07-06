<template>
	<view class="main">
		<view class="title_box">
			<image :src="iconList[0]" class="info_icon"></image>
			<view class="info_text">{{'滤材更换'}}</view>
		</view>
		<view class="basic_info">基本信息</view>
		<view class="info_box">
			<view class="line_box line_one">
				<view class="line_text_1">提醒时间</view>
				<view style="display: flex; align-items: center;">
					<view class="line_text_2">选择时间</view>
					<view class="icon"><u-icon  name="arrow-right"color="#C6C6CF"></u-icon></view>
				</view>
			</view>
			<view class="line_box">
				<view class="line_text_1">重复提醒</view>
				<view style="display: flex; align-items: center;">
					<view class="line_text_3">无</view>
					<view class="icon"><u-icon  name="arrow-right"color="#C6C6CF"></u-icon></view>
				</view>
			</view>
		</view>
		<view class="basic_info">备注</view>
		<view class="info_box">
			<u-textarea v-model="textareaValue" placeholder="有需要的话,备注一下吧~" height="200" border="none"></u-textarea>
		</view>
		<bottomBut :text="'保存'" @fun="addRemind"></bottomBut>
	</view>
</template>

<script>
	import { mapGetters } from 'vuex';
	import bottomBut from '@/components/bottomBut.vue'
	export default {
		components: {
			bottomBut
		},
		data() {
			return {
				iconList:{
					0 : require('@/static/remind/filterchange_icon.png'),
					1 : require('@/static/remind/expelling_inner_icon.png'),
					2 : require('@/static/remind/expelling_open_icon.png'),
					3 : require('@/static/remind/cuntom_icon.png')
				},
				textareaValue:''
			}
		},
		onLoad() {

		},
		computed: {
			...mapGetters(['systemInfo']),
		},
		methods: {
			addRemind(){
				
			}
		}
	}
</script>

<style lang="scss" scoped>
.main{
	padding: 32rpx;
	.title_box{
		height: 144rpx;
		background-color: #fff;
		border-radius: 12rpx;
		display: flex;
		align-items: center;
		.info_icon{
			width: 64rpx;
			height: 64rpx;
			margin: 0 24rpx;
		}
		.info_text{
			font-size: 28rpx;
			font-weight: 400;
			color: #16161A;
		}
	}
	.basic_info{
		margin-top: 40rpx;
		font-size: 28rpx;
		font-weight: 400;
		color: #797980;
	}
	.info_box{
		background: #FFFFFF;
		border-radius: 12rpx;
		height: 241rpx;
		padding: 0 24rpx;
		margin: 16rpx 0 40rpx 0;
		.line_box{
			height: 120rpx;
			display: flex;
			align-items: center;
			justify-content: space-between;
		}
		.line_one{
			border-bottom: 1rpx solid #EEEEEE;
		}
		.line_text_1{
			font-size: 28rpx;
			font-weight: 400;
			color: #16161A;
		}
		.line_text_2{
			font-size: 28rpx;
			font-weight: 400;
			color: #5596F2;
			text-align: right;
			margin-right: 10rpx;
		}
		.line_text_3{
			font-size: 28rpx;
			font-weight: 400;
			color: #16161A;
			margin-right: 10rpx;
			text-align: right;
		}
		.icon{
			margin-left: 12rpx;
		}
	}
}
/deep/.u-icon__icon.data-v-172979f{
	font-size: 24rpx !important;
}

</style>
