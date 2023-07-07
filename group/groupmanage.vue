<template>
	<view>
		<view class="group">
			<view class="group_item" :class="{'item_top': index > 0 }" v-for="(item,index) in groupList" :key="index" @click="groupDetail(item)">
				<view class="title">{{item.name}}</view>
				<view class="dev_box">
					<text>{{item.num}}个设备</text>
					<view class="icon"><u-icon size="25" name="arrow-right"color="#C6C6CF"></u-icon></view>
				</view>
			</view>
		</view>
		<bottomBut :text="'增加设备分组'" @fun="addGroup"></bottomBut>
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
				groupList:[
					{name:'未分组',num:0},
					{name:'客厅',num:2},
					{name:'书房',num:3},
					{name:'卧室',num:4},
				]
				
			}
		},
		onLoad() {
	
		},
		// computed: {
		// 	...mapGetters(['systemInfo']),
		// },
		methods: {
			addGroup(){
				uni.navigateTo({
					url: '/group/addGroupOne'
				})
			},
			groupDetail(item){
				uni.navigateTo({
					url: `/group/groupDetail?title=${item.name}`
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.group{
		width: 686rpx;
		margin: 32rpx auto 0 auto;
		min-height: 125rpx;
		border-radius: 12rpx;
		background-color: #fff;
		.group_item{
			height: 125rpx;
			margin: 0 32rpx;
			box-sizing: border-box;
			display: flex;
			align-items: center;
			.title{
				width: 380rpx;
				font-size: 32rpx;
				font-weight: 400;
				color: #16161A;
			}
			.dev_box{
				width: 240rpx;
				margin-left: 10rpx;
				display: flex;
				justify-content: flex-end;
				align-items: center;
				font-size: 32rpx;
				font-weight: 400;
				color: #A8A8AF;
				.icon{
					height: 19rpx;
					margin-left: 10rpx;
				}
			}
		}
		.item_top{
			border-top: 1rpx solid #EEEEEE;
		}
	}
</style>