<template>
	<view>
		<view class="group_title">
			请选择需要移入的设备
		</view>
			<view class="dev_main_box">
				<view v-for="(item,index) in devList" :key="index">
					<devCard :info="item" :key="index" @checkboxChange="checkboxChange" :isChecked="true"></devCard>
				</view>
			</view>
		<bottomBut :text="'完成创建'" @fun="addFinish"></bottomBut>
	</view>
</template>

<script>
	import bottomBut from '@/components/bottomBut.vue'
	import devCard from '@/group/components/devCard.vue'
	export default {
		components: {
			bottomBut,devCard
		},
		data() {
			return {
				value:'',
				devList:[
					{name:'ph值检测仪1',img:'../../static/nodata.png'},
					{name:'ph值检测仪2',img:'../../static/nodata.png'},
					{name:'ph值检测仪3',img:'../../static/nodata.png'},
					{name:'ph值检测仪4',img:'../../static/nodata.png'},
				],
				checked:[] //选中的item
			}
		},
		onLoad() {
	
		},

		methods: {
			addFinish(){
				uni.switchTab({
					url:'/pages/index/index'
				})
			},
			 checkboxChange(item,check) {
				if(check){
					this.checked.push(item)
				}else{
					this.checked.splice(this.checked.indexOf(item), 1)
				}
				console.log(11,this.checked)
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
.dev_main_box{
	width: 686rpx;
	margin: 0 auto;
	display: flex;
	flex-wrap: wrap;
	justify-content: space-between;
	
}


/deep/.data-v-104c43fa .u-input__content__field-wrapper__field{
	height: 109rpx;
	margin-left: 20rpx;
}
</style>