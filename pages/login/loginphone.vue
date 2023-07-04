<template>
	<view>
		<image class="img" src="/static/liangxianghe.png"></image>
		<view class="login_state">
			<view class="state_font" :class="{'state_font_select' : selected==0}" @click="chooseSelected(0)">验证码登录</view>
			<view class="cutline"></view>
			<view class="state_font" :class="{'state_font_select' : selected==1}" @click="chooseSelected(1)">密码登录</view>
		</view>
		
		<view class="input_box">
			<u-input v-model="phoneNum"  border="none" placeholder="请输入手机号码" ></u-input>
		</view>
		<view class="input_box code" v-show="selected==0">
			<u-input v-model="code"  border="none" placeholder="请输入验证码" ></u-input>
			<view class="pas_code">
				<view v-show="showTimeDown" class="code_text_active" @click="clickTimeDown">
					{{message}}
				</view>
				<view v-show="!showTimeDown" class="code_text_active">
					<text>重新获取(</text>
					<u-count-down  @finish="finish" ref="countDown" :autoStart="false" :time="61 * 1000" format="ss"></u-count-down>
					<text>S)</text>
				</view>
			</view>
		</view>
		<view class="input_box code" v-show="selected==1">
			<u-input v-model="passward" type="password"  border="none" placeholder="请输入登录密码" ></u-input>
			<view class="pas_code">
				<view class="forget">忘记密码</view>
			</view>
		</view>
		<view class="submit">
			<u-button :disabled="subDisabled" color="#5596F2"  type="primary">立即登录</u-button>
		</view>
		<view class="agr_bottom">
			登录即代表您已同意<text>《靓相和用户协议》</text>和<text>《隐私协议》</text>
		</view>
	</view>
	
</template>

<script>
	export default {
		data() {
			return {
				selected:0,
				phoneNum:'',
				code:'',
				passward:'',
				message: '获取验证码',
				showTimeDown: true,
				subDisabled:true
			}
		},
		onLoad() {
			
			 
		},
		computed: {
		      listenChange () {
		        const {phoneNum,code,passward,selected} = this
		        return {phoneNum,code,passward,selected}
		      }
		}, 
		watch: {
			listenChange: {
				handler(newVal, oldVal) {
					if (this.phoneNum && this.selected==0 && this.code){
						this.subDisabled=false
					}else if (this.phoneNum && this.selected==1 && this.passward){
						this.subDisabled=false
					}else{
						this.subDisabled=true
					}
				},
				immediate:true
			}
		},
		methods: {
			chooseSelected(index){
				this.selected=index
				this.code=''
				this.passward=''
			},
			clickTimeDown() {
				if (this.phoneNum == '') {
					this.$util.toast("请输入手机号码")
					return false;
				}
				if (!this.$util.verifyMobile(this.phoneNum)) {
					this.$util.toast("手机号码格式不正确")
					return false;
				}
				this.getSmsCode()
			},
			async getSmsCode() {
				// let res = await getCodeImg({
				// 	phone: this.phone,
				// 	type: 4,
				// })
				// if (res.code == 200) {
					this.$util.toast("短信验证码发送成功")
					this.showTimeDown = false
					this.$refs.countDown.reset();
					this.$refs.countDown.start();
				// }
			},
			finish() {
				this.showTimeDown = true
			},
		}
	}
</script>
<style>
	page{
		background-color: #FFFFFF;
		padding:32rpx;
	}
</style>
<style lang="scss" scoped>
	.img{
		width: 120rpx;
		height: 120rpx;
	}
	.login_state{
		margin-top: 64rpx;
		display: flex;
		align-items: center;
		.state_font{
			font-size: 32rpx;
			font-weight: 400;
			color: #A8A8AF;
		}
		.state_font_select{
			font-weight: 600;
			color: #16161A;
		}
		.cutline{
			width: 1rpx;
			height: 24rpx;
			border-left: 1rpx solid #C6C6CF;
			margin: 0 32rpx;
		}
	}
.input_box{
	width: 686rpx;
	height: 96rpx;
	background-color: #F7F7F7;
	margin-top: 55rpx;
}
/deep/.u-input__content__field-wrapper__field.data-v-fdbb9fe6{
	height: 96rpx;
	margin-left: 20rpx;
}
.code{
	margin-top: 24rpx;
	position: relative;
	.pas_code{
		position: absolute;
		top: 50%;
		transform: translateY(-50%);
		right: 24rpx;
		z-index:999;
		width: 220rpx;
		height: 50rpx;
		text-align: right;
		.code_text_active{
			font-size: 28rpx;
			font-weight: 500;
			color: #5596F2;
			line-height: 50rpx;
		}  
		.forget{
			font-size: 28rpx;
			font-weight: 500;
			color: #797980;
			line-height: 50rpx;
		}
	}
}
/deep/.u-count-down {
	display: inline-block !important;
}
/deep/.u-count-down__text.data-v-072523e7{
	color: #5596F2!important;
}
.submit{
	width: 686rpx;
	height: 96rpx;
	margin-top: 44rpx;
	/deep/.u-button.data-v-3bf2dba7 {
		height: 100%;
		font-size: 34rpx;
		font-weight: 600;
	}
}
.agr_bottom{
		position: fixed;
		width: 686rpx;
		bottom:100rpx;
		font-size: 24rpx;
		font-weight: 400;
		color: #A8A8AF;
		text-align: center;
		left: 50%;
		transform: translateX(-50%);
		text{
			color: #748EB3;
		}
	}
</style>