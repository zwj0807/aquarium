<template>
	<view>
		<view class="group_title">
			分组名称
		</view>
		<view class="group_name">
			<view class="input_box">
				<u-input  v-model="value"  border="none" placeholder="请输入分组名称" ></u-input>
			</view>
		</view>
		<bottomBut :text="'下一步'" @fun="addGroup"></bottomBut>
	</view>
</template>

<script>
	import bottomBut from '@/components/bottomBut.vue'
	export default {
		components: {
			bottomBut
		},
		data() {
			return {
				value:''
			}
		},
		onLoad() {
	
		},

		methods: {
			addGroup(){
				uni.navigateTo({
					url:'/group/addGroupTwo'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
.group_title{
	font-size: 34rpx;
	font-weight: 600;
	color: #16161A;
	margin: 32rpx 0 24rpx 32rpx;
}
.group_name{
	width: 686rpx;
	height: 109rpx;
	margin: 0 auto;
	.input_box{
		height: 109rpx;
		background-color: #fff;
		border-radius: 12rpx;
		overflow: hidden;
	}
}


/deep/.data-v-104c43fa .u-input__content__field-wrapper__field{
	height: 109rpx;
	margin-left: 20rpx;
}
</style>