<template>
	<view>
		<view class="tip_title">
			请选择要移入到“{{title}}”的设备
		</view>
		<view v-for="(count,num) in itemList" :key="index">
			<view class="content_box">
				<view class="group_title">{{count.title}}</view>
			</view>
			<view class="dev_main_box">
				<view v-for="(item,index) in count.devList" :key="index">
					<devCard :info="item" @checkboxChange="checkboxChange" :isChecked="true"></devCard>
				</view>
			</view>
		</view>
		<view style="height: 100rpx;"></view>
		<bottomBut :text="'确定移入'" @fun="subenter"></bottomBut>
	</view>
</template>

<script>
	import bottomBut from '@/components/bottomBut.vue'
	import devCard from '@/group/components/devCard.vue'
	export default {
		components: {
			devCard,bottomBut
		},
		data() {
			return {
				title:'',
				itemList:[
					{
						title:'卧室',
						devList:[
							{name:'ph值检测仪1',img:'../../static/nodata.png'},
							{name:'ph值检测仪2',img:'../../static/nodata.png'},
							{name:'ph值检测仪3',img:'../../static/nodata.png'},
							{name:'ph值检测仪4',img:'../../static/nodata.png'},
						],
					},
					{
						title:'客厅',
						devList:[
							{name:'ph值检测仪1',img:'../../static/nodata.png'},
							{name:'ph值检测仪2',img:'../../static/nodata.png'},
							{name:'ph值检测仪3',img:'../../static/nodata.png'},
							{name:'ph值检测仪4',img:'../../static/nodata.png'},
						],
					}
					
				],
				
				checked:[]
			}
		},
		onLoad(options) {
			if(options){
				this.title = options.title
			}
		},
	
		methods: {
			checkboxChange(item,check) {
				if(check){
					this.checked.push(item)
				}else{
					this.checked.splice(this.checked.indexOf(item), 1)
				}
				console.log(11,this.checked)
			},
			subenter(){
				uni.reLaunch({
					url:'/pages/index/index'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.tip_title{
		font-size: 28rpx;
		font-weight: 400;
		color: #797980;
		margin: 32rpx 0 0 32rpx;
	}
	.content_box{
		.group_title{
			font-size: 34rpx;
			font-weight: 600;
			color: #16161A;
			margin: 40rpx 0 32rpx 32rpx;
		}
	}
	.dev_main_box{
		width: 686rpx;
		// min-height: 600rpx;
		margin: 0 auto;
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
	}
</style>