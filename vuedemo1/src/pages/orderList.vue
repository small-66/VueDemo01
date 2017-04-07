<template>
  <div class="order-wrap">
    <div class="order-list-choose">
      <div class="order-list-option">
        选择产品：
        <v-selection :selections="products" @on-change="productChange"></v-selection>
      </div>
      <div class="order-list-option">
        开始日期：
        <v-datepicker @change="changeStartDate"></v-datepicker>
      </div>
      <div class="order-list-option">
        结束日期：
        <v-datepicker @change="changeEndDate"></v-datepicker>
      </div>
      <div class="order-list-option">
        关键词：
        <input type="text" v-model.lazy="query" class="order-query"/>
      </div>
    </div>
  </div>
</template>

<script>
import vSelection from '../components/base/selection'
import vDatepicker  from '../components/base/datepicker'
export default {
    components: {
      vSelection,
      vDatepicker
    },
	data() {
		return {
      query: '',
      startDate: '',
      endDate: '',
      productId: 0,
      products: [
        {
          label: '数据统计',
          value: 0
        },
        {
          label: '数据预测',
          value: 1
        },
        {
          label: '流量分析',
          value: 2
        },
        {
          label: '广告发布',
          value: 3
        }
      ]
		}
	},
  watch:{
        query(){
            console.log( 'on query change')
        }
  },
  methods:{
    productChange(obj){
      this.productId = obj.value
      console.log(this.productId)
    },
    changeStartDate(date){
      this.startDate = date
    },
    changeEndDate(date){
      this.endDate = date
    }
  }
}
</script>

<style >
  .order-wrap {
    width: 1200px;
    min-height: 800px;
    margin: 0 auto;
    overflow: hidden;
  }
  .order-query {
    height: 25px;
    line-height: 25px;
    border: 1px solid #e3e3e3;
    outline: none;
    text-indent: 10px;
  }
  .order-list-option{
    display: inline-block;
    padding-left: 15px;

  }
  .order-list-option:first-child{
    padding-left: 0;
  }
</style>
