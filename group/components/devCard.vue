<template>
	<view class="dev_item" :class="{'item_checked':isChecked && checked}">
		<image class="img" :src="info.img"></image>
		<view class="txt">{{info.name}}</view>
		<view class="checked_box" v-if="isChecked">
			 <u-checkbox size="40rpx"  iconSize="25" shape="circle" activeColor="#5596F2" @change="checkboxChange(info)" :checked="checked"></u-checkbox>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			isChecked:{
				type:Boolean,
				default: false
			},
			info:{
				type:Object,
				default:{}
			}
		},
		data() {
			return {
				checked:false
			}
		},
		onLoad() {
	
		},

		methods: {
			checkboxChange(item){
				this.checked=!this.checked
				this.$emit('checkboxChange',item,this.checked)
			}
		}
	}
</script>

<style lang="scss" scoped>
.dev_item{
	width: 331rpx;
	height: 277rpx;
	background: #FFFFFF;
	border-radius: 16rpx;
	display: flex;
	flex-direction: column;
	flex-direction: center;
	align-items: center;
	position: relative;
	margin-bottom:24rpx;
	.img{
		margin-top: 24rpx;
		width: 168rpx;
		height: 168rpx;
	}
	.txt{
		margin-top: 16rpx;
		font-size: 32rpx;
		font-weight: 600;
		color: #16161A;
	}
	.checked_box{
		position: absolute;
		top: 24rpx;
		right: 24rpx;
		width: 40rpx;
		height: 40rpx;
	}
}
.item_checked{
	border: 1rpx solid #5596F2;
}
</style>