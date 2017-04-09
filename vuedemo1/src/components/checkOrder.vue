<template>
	<div>
    <t-dialog :is-show="isShowCheckDialog" @on-close="checkStatus">
      请检查你的支付状态！
      <div class="button" @click="checkStatus">支付成功</div>
      <div class="button" @click="checkStatus">支付失败</div>
    </t-dialog>
    <t-dialog :is-show="isShowSuccessDialog" @on-close="toOrderList">购买成功</t-dialog>
    <t-dialog :is-show="isShowFailDialog" @on-close="toOrderList">购买失败</t-dialog>
	</div>
</template>
<script>
  import Dialog from './base/dialog'
  export default{
    components:{
      tDialog:Dialog
    },
    props:{
      isShowCheckDialog: {
        type: Boolean,
        default: true
       },
      orderId:{
          type: [String,Number]
      }
    },
    data(){
      return {
        isShowSuccessDialog: false,
        isShowFailDialog: false
      }
    },
    methods:{
      closeDialog(){
        this.isShowSuccessDialog = false
      },
      checkStatus(){
          this.$http.get('/api/checkOrder',{
              orderId : this.orderId
          }).then((res)=>{
            this.isShowSuccessDialog = true
            this.$emit('on-close-check-dialog')

          },(error)=>{
            this.isShowFailDialog = true
          })
      },
      toOrderList(){
          this.$router.push({path: '/orderList'})
      }
    }
}
</script>
<style>
</style>
