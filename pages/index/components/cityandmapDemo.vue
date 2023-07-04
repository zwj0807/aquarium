<template>
	<view>
		<cityPicker  :propValue="propValue" @cityPickerConfirm="cityPickerConfirm"></cityPicker>
		<map @click="mapFun" class='map' :latitude="latitude" :longitude="longitude" :markers="covers" />
	</view>
</template>

<script>
	import cityPicker from '@/components/cityPicker/index.vue'
	
	export default {
		components: { cityPicker },
		data() {
			return {
				propValue:'山东省 枣庄市 台儿庄区',
				latitude: 39.909,
				longitude: 116.39742,
				covers: [{
					id:1,
					latitude: 39.909,
					longitude: 116.39742,
					width:'30',
					height:"45"
				}],
			}
		},
		onLoad() {

		},
		computed: {
			
		},
		methods: {
			mapFun() {
				    uni.openLocation({
					latitude: this.latitude, //纬度 - 目的地/坐标点
			 		longitude: this.longitude, //经度 - 目的地/坐标点
					name: "天安门",
					address: "长安街1号"
				    });
			   },
			   cityPickerConfirm(arrName,arrCode){
				   console.log('确认改变数据',arrName,arrCode)
				   this.propValue =arrName
			   }
		}

	}
</script>

<style>
.map{
	width: 100%;

}

</style>
