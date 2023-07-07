<template>
	<view>
		<view class="title">
			输入新组名
		</view>
		<view class="input_box">
			<u-input v-model="name"  border="none" placeholder="请输入新组名" ></u-input>
		</view>
		<bottomBut :text="'保存'" @fun="save"></bottomBut>
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
				name:''
				
			}
		},
		onLoad(options) {
			if(options){
				
			}
		},
	
		methods: {
			save(){
				uni.reLaunch({
					url:'/pages/index/index'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.title{
		font-size: 34rpx;
		font-weight: 600;
		color: #16161A;
		margin: 32rpx 0 0 32rpx;
	}
	.input_box{
		width: 686rpx;
		height: 96rpx;
		background-color: #FFFFFF;
		border-radius: 12rpx;
		margin: 32rpx auto 0 auto;
	}
	/deep/.u-input__content__field-wrapper__field.data-v-fdbb9fe6{
		height: 96rpx;
		margin-left: 20rpx;
	}
</style>