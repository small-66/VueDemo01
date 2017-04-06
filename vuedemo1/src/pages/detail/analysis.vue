<template>
  <div class="sales-board">
    <div class="sales-board-intro">
    	<h2>流量分析</h2>
    	<p>随便打字随便打字随便打字随便打字随便打字随便打字随便打字随便打字随便打字
    	随便打字随便随便打字随便打字随便打字随便打字随便打字随便打字随便打字随便打字
    	</p>
    </div>
    <div class="sale-board-form">
    	<div class="sales-board-line">
    		<div class="sales-board-line-left">
    			购买数量：
    		</div>
    		<div class="sales-board-line-right">
    		   <counter  @on-change="onParamChange('buyNum' , $event)" ></counter>
    		</div>
    	</div>
    	<div class="sales-board-line">
    		<div class="sales-board-line-left">
    			产品类型：
    		</div>
    		<div class="sales-board-line-right">
    			<vselected :selections="porductTypes" @on-change="onParamChange('buyType', $event)" ></vselected>
    		</div>
    	</div>
        <div class="sales-board-line">
            <div class="sales-board-line-left">
                有效时间
            </div>
            <div class="sales-board-line-right">
                <selections-one :selections-one="porductTypesTime"  @on-change="onParamChange('period' , $event)" ></selections-one>
            </div>
        </div>
    	<div class="sales-board-line">
    		<div class="sales-board-line-left">
    			产品版本：
    		</div>
    		<div class="sales-board-line-right">
    			<selection1 :selections1="porductTypesAll"  @on-change="onParamChange('version'  , $event)" ></selection1>
    		</div>
    	</div>
    	<div class="sales-board-line">
    		<div class="sales-board-line-left">
    			总价：
    		</div>
    		<div class="sales-board-line-right">
    			$  {{ price }}
    		</div>
    	</div>
    	<div class="sales-board-line">
    		<div class="sales-board-line-left">
    			&nbsp;
    		</div>
    		<div class="sales-board-line-right">
    			<div class="button" @click="showPayDailog" >
    				立即购买
    			</div>
    		</div>
    	</div>
    </div>
    <div class="sales-board-des">
    	<h2>产品说明</h2>
    	<p>产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说产品说明</p>
    	<h3>用户行为指标</h3>
    	<ul>
    		<li>产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明
    		</li>
    		<li>产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明
    		</li>
    		<li>品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明
    		</li>
    		<li>明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明产品说明
    		</li>
    	</ul>
    	<h3>浏览网站方式</h3>
    	<ul>
    		<li>用户上网设备类型</li>
    		<li>用户浏览器名称及版本</li>
    		<li>访问者电脑分辨率显示模式</li>
    		<li>用户所使用的操作系统名称及版本</li>
    		<li>用户所在地区分布</li>
    	</ul>
    </div>
    <my-dialog :is-show="isShowPayDialog"  @on-close="closeDialog('isShowPayDialog')">
        <table class="buy-dialog-table">
            <tr>
                <th>购买数量</th>
                <th>产品类型</th>
                <th>有效时间</th>
                <th>产品版本</th>
                <th>总价</th>
            </tr>
            <tr>
                <td>{{ buyNum }}</td>
                <td>{{ buyType.label }}</td>
                <td>{{ period.label  }}</td>
                <td><span v-for="item in version">{{ item.label }} </span></td>
                <td>{{ price }}</td>
            </tr>
        </table>
        <h3 class="buy-dialog-title">请选择银行</h3>
        <bank-chooser @on-change="onChangeBanks"></bank-chooser>
        <div class="button buy-dialog-btn" @click="confirmBuy">确认购买</div>
     </my-dialog>
    <my-dialog :is-show="isShowErrDialog" @on-close="hideErrDialog">支付失败</my-dialog>
    <my-check :is-show-check-dialog="isShowCheckDialog"></my-check>
  </div>
</template>

<script>
import selection1 from '../../components/base/selection_all'
import vselected from '../../components/base/selection'
import selectionsOne from '../../components/base/selection_1'
import counter from '../../components/base/counter'
import Dialog from '../../components/base/dialog'
import bankChooser from '../../components/bank'
import checkOrder from '../../components/checkOrder'
import _ from 'lodash'
export default {
	components:{
		    vselected,
        counter,
        selection1,
        selectionsOne,
        MyDialog: Dialog,
        bankChooser,
        myCheck:checkOrder
	},
    data () {
        return {
            buyNum: 20,
            buyType:{},
            version:[],
            period:{},
            price: 0,
            porductTypesTime:[
                {
                    label: '半年',
                    value: 0
                },
                {
                    label: '一年',
                    value: 1
                },
                {
                    label: '三年',
                    value: 2
                }
            ],
            porductTypesAll:[
                {
                    label: '客户版',
                    value: 0
                },
                {
                    label: '代理商版',
                    value: 1
                },
                {
                    label: '专家版',
                    value: 2
                }
            ],
        	porductTypes:[
        		{
        			label: '入门版',
        			value: 0
        		},
        		{
        			label: '中级版',
        			value: 1
        		},
        		{
        			label: '高级版',
        			value: 2
        		}
        	],
            isShowPayDialog: false,
            bankId: null,
            isShowCheckDialog: false,
            isShowErrDialog: false

        }
    },
    methods: {
        onParamChange(attr,val){
            this[attr] = val
            this.getPrice()
        },
        getPrice(){
            let buyVersionsArray = _.map(this.version, (item)=> {
                return item.value
            })
            let passParams = {
                buyNum : this.buyNum,
                buyType: this.buyType.value,
                version: buyVersionsArray.join(','),
                period: this.period.value
            }
            this.$http.get('/api/getP', passParams).then((res) => {
                let data = JSON.parse(res.data.rem)
                this.price = data
            })
        },
        showPayDailog(){
            this.isShowPayDialog = true
        },
        closeDialog(attr){
            this[attr] = false
        },
        onChangeBanks(bankObj){
            this.bankId = bankObj.id
            console.log(this.bankId)
        },
        hideErrDialog(){
            this.isShowErrDialog = false
        },
        confirmBuy(){
            let buyVersionsArray = _.map(this.version, (item)=> {
                return item.value
            })
            let passParams = {
                buyNum : this.buyNum,
                buyType: this.buyType.value,
                version: buyVersionsArray.join(','),
                period: this.period.value,
                bankId: this.bankId
            }
            this.$http.get('/api/createOrder', passParams).then((res) => {
                let orderId = res.data.orderId
                console.log(orderId)
                this.isShowCheckDialog = true
                this.isShowPayDialog = false
            },(error)=>{
                this.isShowErrDialog = true
                this.isShowPayDialog = true
            })
        }
    },
    mounted (){
        this.buyNum = 1,
        this.buyType = this.porductTypes[0],
        this.version = [this.porductTypesAll[0]],
        this.period = this.porductTypesTime[0],
        this.getPrice()
    }
}
</script>
<style>
.selection-component {
	position: relative;
	display: inline-block;
}
.selection-show {
	border: 1px solid #e3e3e3;
	padding: 0 20px 0 10px;
	position: relative;
	display: inline-block;
	cursor: pointer;
	height: 25px;
	line-height: 25px;
	border-radius: 3px;
}
.selection-show .arrow {
	display: inline-block;
	border-left: 4px solid transparent;
	border-right: 4px solid transparent;
	border-top: 5px solid #e3e3e3;
	width: 0;
	height: 0;
	margin-top: -1px;
	margin-left: 6px;
	margin-right: -14px;
	vertical-align: middle;
}
.selection-list {
	display: inline-block;
	position: absolute;
	left: 0;
	top: 25px;
    width: 100%;
    background: #fff;
    border-top: 1px solid #e3e3e3;
    border-bottom: 1px solid #e3e3e3;
    z-index: 5;
}
.selection-list li{
	padding: 5px 15px 5px 10px;
	border-left: 1px solid #e3e3e3;
	border-right: 1px solid #e3e3e3;
	cursor: pointer;
	background: #fff;
	white-space: nowrap;
	overflow: hidden;
	text-overflow: ellipsis;
}
.selection-list li:hover{
	background: #e3e3e3;
}


.buy-dialog-title{
    font-size: 16px;
    font-weight: bold;
}
.buy-dialog-btn {
    margin-top: 20px;
    margin-left: 200px;
}
.buy-dialog-table {
    width: 100%;
    margin-bottom: 20px;
}
.buy-dialog-table th,
.buy-dialog-table td{
    border: 1px solid #e3e3e3;
    text-align: center;
    padding: 5px 0;
}
.buy-dialog-table th{
    background: #4fc08d;
    color: #fff;
}
</style>
