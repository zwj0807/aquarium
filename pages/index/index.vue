<template>
	<view>
		<view class="home_main_box" :style="{paddingTop: `${systemInfo.navHeight}rpx` }">
			<view class="my_home_box">
				<view class="home_text" @click="this.groupShow=true">{{homeText}}</view>
				<image class="triangle_down" src="/static/home/triangle_down.png"></image>
				<view class="inform_box">
					<image class="inform_box_img" src="/static/home/inform_icon.png"></image>
					<view class="badge">
						 <text>{{informNum}}</text>
					</view>
				</view>
			</view>
			<view class="home_banner">
				<u-swiper height="216rpx" radius="20"  :list="list3" circular @change="changeBanner">
					<view slot="indicator" class="indicator">
				        <view class="indicator__dot" v-for="(item, index) in list3" :key="index"
				                :class="[index == current ? 'indicator__dot_active' :'indicator__dot']">
				        </view>
				    </view>
				</u-swiper>
			</view>
			<view class="todoList">
				<text class="todoList_title">待办</text>
				<view class="todoList_num">{{todoListNum + '条'}}</view>
			</view>
			<view class="notice" style="margin-top:20rpx;">
				<view class="notice_line" v-for="(item,index) in noticeList" :key="index">
					<view class="notice_left_icon"></view>
					<view class="notice_text">{{item.message}}</view>
					<view class="notice_time">{{item.date}}</view>
				</view>
				<view class="bottom_line"></view>
			</view>
			<view class="device_box">
				<view class="device_title">设备</view>
				<view class="device_add"> <image style="width:100%;height:100%;" src="/static/home/add_device.png" mode=""></image></view>
			</view>
			<dragAndDropSort :controlsList="deviceList" :controlsSize="{width: 331, height: 429}">
				<template #content="{item}">
					<deviceCard></deviceCard>
				</template>
			</dragAndDropSort>
			<view v-if="false" style="height: 450rpx;display: flex;justify-content: center; align-items: center;">
				<nodata></nodata>
			</view>
		</view>
		<!-- 分组管理弹窗 -->
		<view class="group">
			<u-popup :show="groupShow" round="15" mode="center" :safeAreaInsetBottom="false" style="bottom: 1050rpx !important;" >
				<view class="group_box">
					<view style="background-color: #F6F7F9;" v-for="(item,index) in groupList" :key="index" @click="chooseGroup">
						<view  v-if="index >= 1" class="group_line"></view>
						<view class="group_item">
							<image style="width: 32rpx;height: 36rpx;" src="/static/home/group_icon.png" v-if="homeText ==item.name"></image>
							<view class="group_text_checked" :class="{'group_text':homeText !==item.name}">{{item.name}}</view>
						</view>
					</view>
					<view class="group_set" @click="groupSet">
						<view class="set_text">分组管理</view>
						<image style="width: 32rpx;height: 32rpx;margin-left: 413rpx;" src="/static/home/group_set.png"></image>
					</view>
				</view>
			</u-popup>
		</view>
		<!-- 广告弹窗 -->
		<view>
			<u-popup :show="adShow" round="15" mode="center" bgColor="transparent" @close="adClose" :closeOnClickOverlay="false" :safeAreaInsetBottom="false">
			    <view class="ad_box">
			        <image style="width: 100%;height: 100%;" src="../../static/home/ad_banner.png"></image>
					<image class="ad_box_close" src="/static/home/ad_close.png" @click="adClose"></image>
			    </view>
			</u-popup>
		</view>
	</view>


</template>

<script>
	import dragAndDropSort from '@/components/drag/index.vue';
	import deviceCard from '@/components/deviceCard/index.vue'
	import nodata from '@/components/nodata.vue'
	import {
		mapGetters
	} from 'vuex';
	export default {
		components: {
			nodata,dragAndDropSort,deviceCard
		},
		data() {
			return {
				homeText:'水族馆',
				informNum:9,
				list3: [
				    'https://cdn.uviewui.com/uview/swiper/swiper3.png',
				    'https://cdn.uviewui.com/uview/swiper/swiper2.png',
				    'https://cdn.uviewui.com/uview/swiper/swiper1.png',
				],
				current:0,
				todoListNum:9,
				noticeList:[{
					message:'PH值检测仪已离线，请检查网络',
					date:'10-1'
				}],
				deviceList:[{id:1,},{id:2,},{id:3,},{id:4,}],
				adShow:false,
				groupShow:false,
				groupList:[
					{name:'我的家'},{name:'水族馆'},
				],

			}
		},
		onLoad() {
			// this.getAD()
		},
		onShow() {
			
		},
		onHide() {
			
		},
		computed: {
			...mapGetters(['systemInfo']),
		},
		methods: {
			changeBanner(e){
				this.current = e.current
			},
			getAD(){
				this.adShow=true
			},
			adClose(){
				this.adShow=false
			},
			chooseGroup(){
				this.groupShow=false
			},
			groupSet(){
				this.groupShow=false
				uni.navigateTo({
					url:'/group/groupmanage'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
.home_main_box{
	// width: 100%;
	height: 645rpx;
	background: url(https://www.jumidongli.com/template/pc/static/demoImg/home/background.png) no-repeat;
	background-size: 100% 645rpx;
	padding: 0 32rpx;
	.my_home_box{
		margin-top: 13rpx;
		display:flex;
		align-items:center;
		.home_text{
			width: 168rpx;
			height: 78rpx;
			font-size: 56rpx;
			font-weight: 600;
			color: #16161A;
		}
		.triangle_down{
			width:16rpx;
			height: 11rpx;
			margin-left:19rpx;
			
		}
		.inform_box{
			width:48rpx;
			height:48rpx;
			margin-left:245rpx;
			position: relative;
			.inform_box_img{
				width:100%;
				height:100%;
			}
			.badge{
				width: 24rpx;
				height: 24rpx;
				border-radius: 50%;
				background-color: #FE3657;
				display: flex;
				justify-content: center;
				align-items: center;
				position: absolute;
				top:0;
				left: 28rpx;
				text{
					font-size: 20rpx;
					color: #FFFFFF;
				}
			}
		}
	}

	.home_banner{
		width:686rpx;
		height:216rpx;
		margin-top:50rpx;
		.indicator {
		    @include flex(row);
		    justify-content: center;
		    .indicator__dot {
		         height: 12rpx;
		         width: 10rpx;
				 transform: skew(20deg, 0);
		         background-color: #fff;
		         margin: 0 8rpx;
		         transition: background-color 0.3s;
		        
		    }
			.indicator__dot_active {
			     background-color: #3377FF;
			 }
		}
	}
	.todoList{
		margin-top:70rpx;
		height:52rpx;
		display:flex;
		align-items: center;
		.todoList_title{
			font-size: 38rpx;
			font-weight: 600;
			color: #16161A;
		}
		.todoList_num{
			min-width: 63rpx;
			height: 32rpx;
			background: #FE3657;
			border-radius: 16rpx;
			margin-left:12rpx;
			font-size: 24rpx;
			font-weight: 400;
			color: #FFFFFF;
			text-align: center;
			line-height: 32rpx;
		}
	}
	.notice{
		min-height: 96rpx;
		background: #FFFFFF;
		box-shadow: 0rpx 15rpx 30rpx 0rpx rgba(107,143,179,0.05);
		border-radius: 12rpx;
		.notice_line{
			height: 96rpx;
			padding: 0 32rpx;
			display: flex;
			align-items: center;
			.notice_left_icon{
				width: 6rpx;
				height: 32rpx;
				background: #5596F2;
				border-radius: 4rpx;
			}
			.notice_text{
				width: 500rpx;
				font-size: 28rpx;
				font-weight: 400;
				color: #16161A;
				margin-left: 24rpx;
				white-space:nowrap;
				overflow:hidden;
				text-overflow:ellipsis; 
			}
			.notice_time{
				font-size: 24rpx;
				font-weight: 400;
				color: #A8A8AF;
				margin-left: 32rpx;
			}
		}
		.bottom_line{
			width: 592rpx;
			height: 1rpx;
			border-bottom: 1rpx solid #EEEEEE;
			margin: 0 auto;
		}
	}
	.device_box{
		margin-top:71rpx;
		margin-bottom:40rpx;
		height:52rpx;
		display: flex;
		justify-content: space-between;
		align-items: center;
		.device_title{
			font-size: 38rpx;
			font-weight: 600;
			color: #16161A;
			line-height: 52rpx;
		}
		.device_add{
			width:40rpx;
			height:40rpx;
		}
	}


	
}
.ad_box{
	width: 560rpx;
	height:720rpx;
	position: relative;
	.ad_box_close{
		position: absolute;
		bottom: -110rpx;
		left:50%;
		transform: translateX(-50%);
		width: 80rpx;
		height: 80rpx;
	}
}
.group{
	/deep/.u-fade-zoom-enter-active.data-v-39e33bf2, .u-fade-zoom-leave-active.data-v-39e33bf2{
		bottom: 900rpx !important;
	}
	/deep/.data-v-39e33bf2,{
		transition-property: transform, opacity,bottom, -webkit-transform !important;
	}
	.group_box{
		width: 686rpx;
		min-height: 218rpx;
		background: #FFFFFF;
		border-radius: 12rpx;
		overflow: hidden;
		.group_line{
			width: 622rpx;
			height: 1rpx;
			background-color: #EEEEEE;
			border-top: 1rpx solid #EEEEEE;
			margin: 0 auto;
		}
		.group_item{
			height: 109rpx;
			background: #F6F7F9;
			display: flex;
			align-items: center;
			padding: 0 32rpx;
			position: relative;
			.group_text_checked{
				position: absolute;
				font-size: 32rpx;
				font-weight: 600;
				color: #5596F2;
				margin-left: 52rpx;
			}
			.group_text{
				color: #16161A;
			}
		}
		.group_set{
			height: 109rpx;
			display: flex;
			align-items: center;
			.set_text{
				font-size: 32rpx;
				font-weight: 600;
				color: #16161A;
				margin-left: 80rpx;
			}
		}
		
	}
}

</style>