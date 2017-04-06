<template>
	<div class="counter-component">
		<div class="counter-btn" @click="minus">-</div>
		<div class="counter-show">
			<input type="text" v-model="number" @keyup="fixNumber"/>
		</div>
		<div class="counter-btn" @click="add">+</div>
	</div>
</template>
<script>
export default {
	props:{
		max:{
			type: Number,
			default: 50
		},
		min:{
			type: Number,
			default: 1
		}
	},
	data(){
		return {
			number:this.min
		}
	},
	watch: {
		number(){
			this.$emit('on-change',this.number)
		}
	},
	methods:{
		fixNumber(){
			let fix
			if(typeof this.number === 'string'){
				fix = Number(this.number.replace(/\D/g,''))
			}
			else {
				fix = this.number
			}
			if (fix > this.max || fix < this.min){
				fix = this.min
			}
			this.number = fix
		},
		minus(){
			if(this.number <= this.min){
				return 
			}
			this.number --
		},
		add(){
			if(this.number >= this.max){
				return 
			}
			this.number ++
		}
	}
}

</script>
<style scoped>
.counter-component{
	overflow: hidden;
}
.counter-btn,.counter-show{
	float: left;
}
.counter-btn{
	width: 18px;
	line-height: 18px;
	display: block;
	text-align: center;
	border: 1px solid #e3e3e3;
}
.counter-btn:hover{
	color: #fff;
	background: #4fc08d;
}
.counter-show input{
	width: 40px;
	text-align: center;
}
</style>