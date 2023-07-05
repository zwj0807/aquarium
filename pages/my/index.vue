<template>
	<view>
		<view class="home_main_box" :style="{paddingTop: `${systemInfo.navHeight}rpx` }">
			<view class="top_txt">我的</view>
			<view class="personal_detail_box">
				<image class="img" src="/static/my/default_head.png"></image>
				<view class="name_phone">
					<view class="name" @click="login">点击登录</view>
					<view class="phone">13371480807</view>
				</view>
				<view class="personal_data" @click="goPersonal">
					个人资料
				</view>
			</view>
			<view class="menu_box">
				<view class="menu_item" v-for="(item,index) in iconList" :key="index">
					<image style="width: 64rpx; height: 64rpx;" :src="item.img"></image>
					<view class="text">{{item.name}}</view>
				</view>
			</view>
		</view>
		<menuCard :list="funListOne"></menuCard>
		<view style="margin-top: 24rpx;">
			<menuCard :list="funListTwo"></menuCard>
		</view>
		<view class="logout_box">
			注销账户
		</view>
		<u-gap height="12" ></u-gap>
	</view>

</template>

<script>
	import {
		mapGetters
	} from 'vuex';
	import menuCard from './components/menuCard.vue'
	export default {
		components: {
			menuCard
		},
		data() {
			return {
				iconList:[
					{
						name:'操作视频',
						img: require('@/static/my/operation_video.png'),
					},
					{
						name:'网点查询',
						img: require('@/static/my/branch_search.png'),
					},
					{
						name:'产品介绍',
						img: require('@/static/my/product_presentation.png'),
					}
				],
				funListOne:[
					{
						name: '报警设置',
						img: require('@/static/my/warn_setting.png'),
					},
					{
						name: '物联网卡短信电话续费',
						img: require('@/static/my/renew.png'),
					},
					{
						name: '共享管理',
						img: require('@/static/my/my_share.png'),
					}
				],
				funListTwo:[
					{
						name: '修改密码',
						img: require('@/static/my/change_password.png'),
					},
					{
						name: '常见问题',
						img: require('@/static/my/issue.png'),
					},
					{
						name: '关于我们',
						img: require('@/static/my/about.png'),
					},
					{
						name: '服务协议｜隐私政策',
						img: require('@/static/my/agreement.png'),
					}
				]
				
			}
		},
		onLoad() {

		},
		computed: {
			...mapGetters(['systemInfo']),
		},
		methods: {
			login(){
				
			},
			goPersonal(){
				uni.navigateTo({
					url: '/my/personalInfo'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
.home_main_box{
	height: 490rpx;
	background: url(https://www.jumidongli.com/template/pc/static/demoImg/home/background.png) no-repeat;
	background-size: 100% 645rpx;
	padding: 0 32rpx;
	.top_txt{
		font-size: 34rpx;
		font-weight: 600;
		color: #16161A;
		margin-top: 30rpx;
	}
	.personal_detail_box{
		height: 128rpx;
		margin-top: 52rpx;
		display: flex;
		// align-items: center;
		.img{
			width: 128rpx;
			height: 128rpx;
			border-radius: 50%;
		}
		.name_phone{
			width: 360rpx;
			margin-left: 32rpx;
			margin-top: 10rpx;
			.name{
				width: 100%;
				font-size: 40rpx;
				font-weight: 600;
				color: #16161A;
				overflow:hidden;
				white-space: nowrap;
				text-overflow: ellipsis;
			}
			.phone{
				margin-top: 11rpx;
				font-size: 26rpx;
				font-weight: 400;
				color: #797980;
			}
		}
		.personal_data{
			width: 136rpx;
			height: 45rpx;
			border-radius: 45rpx;
			border: 1rpx solid #979797;
			font-size: 24rpx;
			font-weight: 400;
			color: #797980;
			line-height: 45rpx;
			text-align: center;
			margin-left: 36rpx;
			margin-top: 40rpx;
		}
	}
	.menu_box{
		width: 686rpx;
		height: 176rpx;
		background: #FFFFFF;
		border-radius: 12rpx;
		margin: 40rpx auto 24rpx auto;
		padding: 0 58rpx;
		box-sizing: border-box;
		display: flex;
		justify-content: space-between;
		align-items: center;
		.menu_item{
			display: flex;
			flex-direction: column;
			align-items: center;
			.text{
				font-size: 28rpx;
				font-weight: 400;
				color: #16161A;
				margin-top: 8rpx;
			}
		}
	}
}

.logout_box{
	width: 686rpx;
	height: 104rpx;
	background: #FFFFFF;
	border-radius: 12rpx;
	margin: 24rpx auto 0 auto;
	font-size: 28rpx;
	font-weight: 400;
	color: #16161A;
	line-height: 104rpx;
	text-align: center;
}
</style>
