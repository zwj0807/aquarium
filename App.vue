<script>
	import {
		getSystemInfo
	} from '@/utils/common.js'
	export default {
		onLaunch: function() {
			console.log('App Launch')
			getSystemInfo()
			// uni.switchTab({
			// 	url: '/pages/index/index'
			// });
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		},

	}
</script>

<style lang="scss">
	/*每个页面公共css */
	@import "uview-ui/index.scss"
	
</style>

<style>
page{
	background: #F6F7F9;
}
</style>
