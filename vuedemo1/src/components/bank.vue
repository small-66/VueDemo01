<template>
	<div class="chooser-component">
		<ul class="chooser-list">
			<li v-for="(item,index) in banks"
			:class="{active:index===nowIndex}"
			@click="chosenSelection(index)"
			:title="item.label"
			>{{ item.label }}</li>
		</ul>
	</div>
</template>
<script>
export default{
	data(){
		return {
			nowIndex: 0,
			banks:[
			{
				id: 201,
				label: '招商银行',
				name: 'zhaoshang'
			},
			{
				id: 301,
				label: '中国建设银行',
				name: 'jianshe'
			},
			{
				id: 601,
				label: '浦发银行',
				name: 'pufa'
			},
			{
				id: 1101,
				label: '交通银行',
				name: 'jiaotong'
			},
			{
				id: 101,
				label: '中国工商银行',
				name: 'gongshang'
			},
			{
				id: 401,
				label: '中国农业银行',
				name: 'nongye'
			},
			{
				id: 1201,
				label: '中国银行',
				name: 'zhongguo'
			},
			{
				id: 501,
				label: '中信银行',
				name: 'zhongxin'
			}]
		}
	},
	methods:{
		chosenSelection(index){
			this.nowIndex = index
			this.$emit('on-change',this.banks[index])
		}
	}
}
</script>
<style scoped>
.chooser-component {
	position: relative;
	display: inline-block;
}
.chooser-list li.active{
	border: 1px solid #4fc08d;
}
.chooser-list li{
	display: inline-block;
	text-align: center;
	width: 117px;
	height: 32px;
	line-height: 32px;
	margin: 5px;
	border: 1px solid #e3e3e3;
	cursor: pointer;
}
</style>