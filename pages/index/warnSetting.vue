<template>
	<u-transition :show="show" mode="fade" duration="500">
		<maskCustom :show="show" @clickOff="clickOff">
			<template>
				<view class="warn-box" :style="warnStyle">提醒闹钟</view>
			</template>
		</maskCustom>
	</u-transition>
</template>
<script>
	import maskCustom from '@/components/maskCustom/index.vue'
	export default {
		components: {
			maskCustom
		},
		data() {
			return {
				warnStyle: '',
				winSize: {},
			}
		},
		props:{
			wxPupData:{
				type:Object,
				default:{
					
				}
			},
			show:{
				type:Boolean,
				default:false
			}
		},
		created() {
			this.getWindowSize()
		},
		computed: {

		},
		watch: {
			wxPupData(e, oldVal) {
				let [touches, style, index ] = [e.touches[0], "", e.currentTarget.dataset.index];
				if (touches.clientY > (this.winSize.height / 2)) {
					style = `bottom:${this.winSize.height-touches.clientY + 100}rpx;`;
				} else {
					style = `top:${touches.clientY + 100}rpx;`;
				}
				if (touches.clientX > (this.winSize.witdh / 2)) {
					style += `right:${ this.winSize.witdh-touches.clientX + 100}rpx`;
				} else {
					style += `left:${touches.clientX + 10}rpx`;
				}
				this.warnStyle = style;

			},
		},
		methods: {
			clickOff(val) {
				this.$emit('clickOff',val)
			},
			getWindowSize() {
				uni.getSystemInfo({
					success: (res) => {
						this.winSize = {
							"witdh": res.windowWidth,
							"height": res.windowHeight
						}
					}
				})
			},
		}

	}
</script>
<style lang="scss" scoped>
	.warn-box {
		position: fixed;
		width: 25%;
		height: 90rpx;
		background-color: #fff;
		border-radius: 10rpx;
	}
</style>