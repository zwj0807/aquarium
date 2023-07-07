<template>
	<view>
		<view class="dev_name_box">
			<view class="name">{{title}}</view>
			<view class="change_name" @click="changeName">
				修改名称
				<view class="icon">
					<u-icon size="25" name="arrow-right"color="#C6C6CF"></u-icon>
				</view>
			</view>
		</view>
		<view class="dev_main_box">
			<template v-if="devList.length>0">
				<view v-for="(item,index) in devList" :key="index">
					<devCard :info="item" :isChecked="false"></devCard>
				</view>
			</template>
			<u-empty :show="devList.length==0" width="220rpx" height="220rpx" textSize="28rpx"  text="此组暂无设备～" icon="/static/nodata.png"></u-empty>
		</view>
		<view class="button">
			<view class="add_group">
				<u-button color="#FFFFFF" :customStyle="{color:'#797980'}"  text="删除该组" @click="deleteGroup"></u-button>
				<u-button color="#FFFFFF" :customStyle="{color:'#5596F2'}" text="移入设备" @click="addGroup"></u-button>
				<u-button color="#5596F2"  text="进入该组" @click="enterGroup"></u-button>
			</view>
		</view>
	</view>
</template>

<script>
	import devCard from '@/group/components/devCard.vue'
	export default {
		components: {
			devCard
		},
		data() {
			return {
				title:'',
				devList:[
					{name:'ph值检测仪1',img:'../../static/nodata.png'},
					{name:'ph值检测仪2',img:'../../static/nodata.png'},
					{name:'ph值检测仪3',img:'../../static/nodata.png'},
					{name:'ph值检测仪4',img:'../../static/nodata.png'},
				],
				
			}
		},
		onLoad(options) {
			if(options){
				this.title = options.title
				uni.setNavigationBarTitle({
				    title: this.title
				})
			}
		},

		methods: {
			changeName(){
				uni.navigateTo({
					url: `/group/changeGroupName`
				})
			},
			deleteGroup(){
				
			},
			addGroup(){
				uni.navigateTo({
					url: `/group/enterDev?title=${this.title}`
				})
			},
			enterGroup(){
				
			}
		}
	}
</script>

<style lang="scss" scoped>
	.dev_name_box{
		width: 686rpx;
		height: 109rpx;
		background: #FFFFFF;
		border-radius: 12rpx;
		margin: 32rpx auto;
		display: flex;
		justify-content: space-between;
		align-items: center;
		.name{
			font-size: 32rpx;
			font-weight: 500;
			color: #16161A;
			margin-left: 32rpx;
		}
		.change_name{
			font-size: 28rpx;
			font-weight: 400;
			color: #5596F2;
			display: flex;
			align-items: center;
			margin-right:32rpx;
			.icon{
					height: 23rpx;
					margin-left: 10rpx;
				}
		}
	}
	.dev_main_box{
		width: 686rpx;
		min-height: 600rpx;
		margin: 0 auto;
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		
	}
	.button{
		height: 96rpx;
		.add_group{
			width: calc(100% - 64rpx);
			height: 96rpx;
			padding: 0 32rpx;
			// background: #FFFFFF;
			position: fixed;
			bottom: 60rpx;
			left: 0;
			display: flex;
			justify-content: space-between;
		}
	}
	/deep/.u-button.data-v-3bf2dba7{
		width: 218rpx;
		height: 100% !important;
	}
	/deep/.u-empty {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		margin: 0 auto !important;
	}
</style>