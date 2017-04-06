<template>
	<div class="Vselection-component">
		<ul class="Vselection">
			<li :class="{active: checkAction(index)}"
			 v-for="(item,index) in selections1"
			 @click="toggleSelection(index)"
			>{{ item.label }}</li>
		</ul>
	</div>
</template>
<script>
import _ from 'lodash'
export default {
	props:{
		selections1: {
			type:Array,
			default: [{
				label: 'test',
				value: 0
			}]
		}
	},
	data(){
		return {
			nowIndexes: [0]
		}
	},
	methods:{
		toggleSelection(index){
			if(this.nowIndexes.indexOf(index) === -1){
				this.nowIndexes.push(index)
			}else{
				this.nowIndexes = _.remove(this.nowIndexes, (idx) => {
					return idx !== index
				})
			}
			let nowObjArray = _.map(this.nowIndexes,(idx) =>{
				return this.selections1[idx]
			})
			this.$emit('on-change',nowObjArray)
		},
		checkAction(index){
			return this.nowIndexes.indexOf(index) !== -1
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