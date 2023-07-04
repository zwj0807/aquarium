<template>
	<view class="main">
		<view class="type_title">
			请选择类型
		</view>
		<view class="card_group_box">
			<view class="card_item_box" v-for="(item,index) in menuList" :key="index">
				<image :src="iconList[index]" class="info_icon"></image>
				<view class="info_text">{{item.name}}</view>
			</view>
			<view class="card_item_box" @click="addRemind">
				<image src="../static/remind/cuntom_add_icon.png" class="info_icon"></image>
				<view class="info_text">自定义</view>
			</view>
			
		</view>
		<u-modal :show="show" title="请输入提醒名称" showCancelButton width="560rpx" confirmColor="#16161A"
		 cancelColor="cancelColor" confirmText="确定"
			@cancel="cancel" @confirm="confirm">
			<view class="slot-content">
				<view class="input_box">
					<u-input :focus="focus"  v-model="value" style="height: 100%;"  border="none" placeholder="点击输入" ></u-input>
				</view>
			</view>
		</u-modal>

	</view>
</template>

<script>
	import { mapGetters } from 'vuex';
	export default {
		data() {
			return {
				menuList:[
					{
						name:'滤材更换',
					},
					{
						name:'体内驱虫',
					},
					{
						name:'体外驱虫',
					},
					{
						name:'自定义事件',
					}
				],
				iconList:{
					0 : require('@/static/remind/filterchange_icon.png'),
					1 : require('@/static/remind/expelling_inner_icon.png'),
					2 : require('@/static/remind/expelling_open_icon.png'),
					3 : require('@/static/remind/cuntom_icon.png')
				},
				show:false,
				value:'',
				focus:false
			}
		},
		onLoad() {

		},
		computed: {
			...mapGetters(['systemInfo']),
		},
		methods: {
			addRemind(){
				this.show=true
				setTimeout(()=>this.focus=true,500)
			},
			cancel(){
				this.show=false
				this.value= ''
			},
			confirm(){
				uni.navigateTo({
					url: '/remind/addRemindTwo'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
.main{
	padding: 32rpx;
	.type_title{
		font-size: 32rpx;
		font-weight: 600;
		color: #16161A;
		margin-bottom: 32rpx;
	}
	.card_group_box{
		display: flex;
		justify-content: space-between;
		align-items: flex-start;
		flex-wrap: wrap;
		.card_item_box{
			width: 331rpx;
			height: 144rpx;
			background: #FFFFFF;
			border-radius: 12rpx;
			display: flex;
			align-items: center;
			margin-bottom: 24rpx;
			.info_icon{
				width: 64rpx;
				height: 64rpx;
				margin: 0 24rpx;
			}
			.info_text{
				font-size: 28rpx;
				font-weight: 400;
				color: #16161A;
			}
		}
	}
}
.input_box{
	height: 96rpx;
	background-color: #F7F7F7;
}
/deep/.u-modal__title.data-v-713d0fd3{
	color: #16161A;
}
/deep/.u-modal__content.data-v-713d0fd3 {
    padding: 24rpx 32rpx 20rpx 32rpx;
}
.slot-content{
	width: 100%;
}
/deep/.u-input__content__field-wrapper__field.data-v-fdbb9fe6{
	height: 96rpx;
	margin-left: 20rpx;
}
</style>
