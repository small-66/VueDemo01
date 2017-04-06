<template>
	<div class="chooser-component">
		<ul class="chooser-list">
			<li :class="{active:index===nowIndex}" v-for="(item,index) in selectionsOne" @click="chosenSelection(index)">{{ item.label }}</li>
		</ul>
	</div>
</template>
<script>
export default {
	props:{
		selectionsOne: {
			type:Array,
			default: [{
				label: 'test',
				value: 0
			}]
		}
	},
	data(){
		return {
			nowIndex:0
		}
	},
	methods:{
		chosenSelection(index){
			this.nowIndex = index
			this.$emit('on-change',this.selectionsOne[index])
		}
	}
}

</script>
<style scoped>
	.chooser-list{
		width: 100%;
		overflow: hidden;
	}
	.chooser-list li{
		float: left;
		width: 60px;
		line-height: 28px;
		border: 1px solid #e3e3e3;
		margin-right: 2px;
		text-align: center;
		border-radius: 5px;
	}
	.chooser-list li.active{
		background: #4fc08d;
		color: #fff;
	}
</style>