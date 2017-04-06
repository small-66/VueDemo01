<template>
	<div class="selection-component">
		<div class="selection-show" @click="toggleDrop">
			<span>{{ selections[nowIndex].label }}</span>
			<div class="arrow"></div>
		</div>
		<div class="selection-list" v-if="isDrop">
			<ul>
				<li v-for="(item,index) in selections" @click="choseSelection(index)">{{ item.label }}</li>
			</ul>
		</div>
	</div>
</template>
<script>
export default {
	props:{
		selections: {
			type:Array,
			default: [{
				label: 'test',
				value: 0
			}]
		}
	},
	data(){
		return {
			isDrop: false,
			nowIndex: 0
		}
	},
	methods:{
		toggleDrop(){
			this.isDrop =!this.isDrop
		},
		choseSelection(index){
			this.nowIndex = index
			this.isDrop = false
			this.$emit('on-change', this.selections[index])
		}
	}
}
</script>
<style><style>