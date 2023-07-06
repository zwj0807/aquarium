<template>
	<view class="button">
		<view class="add_group">
			<u-button :color="color"  :text="text" @click="click"></u-button>
		</view>
	</view>
</template>

<script>
	export default {
		components: {
			
		},
		props:{
			text:{
				type:String,
				default:'确认'
			},
			color:{
				type:String,
				default:'#5596F2'
			}
			
		},
		data() {
			return {
				
			}
		},
		options: {
			styleIsolation: 'shared', // 解除样式隔离
		},
		onLoad() {
	
		},

		methods: {
			click(){
				this.$emit('fun')
			}
		}
	}
</script>
<style lang="scss" scoped>
.button{
	height: 96rpx;
	.add_group{
		width: calc(100% - 64rpx);
		height: 96rpx;
		padding: 0 32rpx;
		background: #FFFFFF;
		position: fixed;
		bottom: 60rpx;
		left: 0;
		
	}
}
/deep/.u-button.data-v-3bf2dba7{
	height: 100% !important;
}

</style>