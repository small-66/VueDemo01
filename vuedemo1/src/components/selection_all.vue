<template>
	<div class="Vselection-component">
		<ul class="Vselection">
			<li :class="{active:item.flag}" v-for="(item,index) in selections1" @click="onChose(index)">{{ item.label }}</li>
		</ul>
	</div>
</template>
<script>
export default {
	props:{
		selections1: {
			type:Array,
			default: [{
				label: 'test',
				value: 0,
				flag: false
			}]
		}
	},
	data(){
		return {
			choseIndex:0
		}
	},
	methods:{
		onChose(index){
			this.choseIndex = index
			this.selections1[index].flag = !this.selections1[index].flag
			this.$emit('on-chose', this.choseIndex)
		}
	}
}

</script>
<style scoped>
	.Vselection{
		width: 100%;
		overflow: hidden;
	}
	.Vselection li{
		float: left;
		width: 60px;
		line-height: 28px;
		border: 1px solid #e3e3e3;
		margin-right: 2px;
		text-align: center;
		border-radius: 5px;
	}
	.Vselection li.active{
		background: #4fc08d;
		color: #fff;
	}
</style>