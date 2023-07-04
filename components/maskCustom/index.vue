<template>
		<view class="popup-bg" v-if="show" @click="maskClick" catchtouchmove="true">
			<slot></slot>
		</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		computed: {
	
		},
		props:{
			//控制显示
			show:{
				type:Boolean,
				default:false
			},
			//点击遮罩层关闭
			clickOff:{
				type:Boolean,
				default:true
			}
		},
		methods: {
			maskClick(){
				if(this.clickOff){
					this.$emit('clickOff',false)
				}
			}
		}
	
	}
</script>

<style lang="scss" scoped>
	.popup-bg{
		  z-index: 999;
	      width: 100%;
	      height: 100%;
	      position: fixed;
	      top: 0;
	      bottom: 0;
	      background-color: rgba(1,1,1,0.3);
	}
</style>