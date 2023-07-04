<template>
	<view class="wid-box-100">
		<u--input 
		placeholder="请选择" 
		border="surround" 
		:readonly="true" 
		suffixIcon="arrow-right" 
		v-model="value"
		@click.native="show=true"
		></u--input>
		<u-picker :defaultIndex="selected" :show="show" ref="uPicker" :columns="columns" keyName="name" @confirm="confirm" @cancel="this.show=false"  @change="changeHandler"></u-picker>
	</view>
</template>
<script>
	import {county} from "./data.js"
	export default {
		model:{
			event:'cityPickerConfirm',
		},
		data() {
			return {
				value:'',
				show: false,
				columns: [],//默认初始数据
				columnData: [],//第二列的数据
				columnData2:[],//第三列的数据
				selected:[0,0,0]
			}
		},
		props:{
			propValue:{
				type:String,
				default:''
			}
		},
		watch:{
			propValue: {
			    handler (newName, oldName) {
			       this.value=newName
			    },
			    immediate: true
			}
		},
		created() {
			const arrOne = []//省(第一列数据)
			county.forEach(item=>{
				arrOne.push({
					name:item.name,
					code:item.code
				})
			})
			const arrTwo = []//市(第二列数据)
			county.forEach(item=>{
				const list = item.children.map(ite=>{
					return {
								name:ite.name,
								code:ite.code
							}
				})
				arrTwo.push(list)
			})
			const arrThree = []//区(第三列数据)
			county.forEach(item=>{
				const listItem = item.children.map(ite=>{
					const listItem1 = ite.children.map(it=>{
						return {
								name:it.name,
								code:it.code
							}
					})
					return listItem1
				})
				arrThree.push(listItem)
			})
			this.columns[0] = arrOne
			this.columns[1] = arrTwo[0]
			this.columns[2] = arrThree[0][0]//赋值初始值
			this.columnData = arrTwo
			this.columnData2 = arrThree
			let ol1= this.columns[0].indexOf( this.columns[0].find(item=>item.name==this.propValue.split(' ')[0]))
			this.columns[1] = arrTwo[ol1]
			let ol2= this.columnData[ol1].indexOf( this.columnData[ol1].find(item=>item.name==this.propValue.split(' ')[1]))
			this.columns[2] = arrThree[ol1][ol2]
			let ol3= this.columnData2[ol1][ol2].indexOf( this.columnData2[ol1][ol2].find(item=>item.name==this.propValue.split(' ')[2]))
			this.selected=[ol1,ol2,ol3]
		},
		methods: {
			changeHandler(e) {
				const {
					columnIndex,//当前滚动的列
					value,//当前选中值
					values, // values为当前变化列的数组内容
					index,//当前滚动列的数据索引
					indexs,//所有列的数据索引值
					// 微信小程序无法将picker实例传出来，只能通过ref操作
					picker = this.$refs.uPicker
				} = e
				// 当第一列值发生变化时，变化第二列(后一列)对应的选项
				if (columnIndex === 0) {
					// picker为选择器this实例，变化第二列对应的选项
					picker.setColumnValues(1, this.columnData[index])//设置第二列的数据
					picker.setColumnValues(2, this.columnData2[index][0])//设置第三列的数据
				}if (columnIndex === 1){
					picker.setColumnValues(2, this.columnData2[indexs[0]][index])//设置第三列的数据
				}
			},
			confirm(e) {
				const {value} = e//当前选中值
				let arrName = []
				let arrCode = []
				value.forEach(item=>{
					arrName.push(item.name)
					arrCode.push(item.code)
				})
				this.show = false
				this.$emit('cityPickerConfirm',arrName.join(' '),arrCode)
				this.value = arrName.join(' ')
			},

		}
	}
</script>