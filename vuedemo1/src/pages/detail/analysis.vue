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
    		
    		</div>
    	</div>
    	<div class="sales-board-line">
    		<div class="sales-board-line-left">
    			产品类型：
    		</div>
    		<div class="sales-board-line-right">
    			<vselected :selections="porductTypes" ></vselected>
    		</div>
    	</div>
    	<div class="sales-board-line">
    		<div class="sales-board-line-left">
    			有效时间
    		</div>
    		<div class="sales-board-line-right">
    			半年
    		</div>
    	</div>
    	<div class="sales-board-line">
    		<div class="sales-board-line-left">
    			总价：
    		</div>
    		<div class="sales-board-line-right">
    			500元
    		</div>
    	</div>
    	<div class="sales-board-line">
    		<div class="sales-board-line-left">
    			&nbsp;
    		</div>
    		<div class="sales-board-line-right">
    			<div class="button">
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
  </div>
</template>

<script>
import vselected from '../../components/selection'
export default {
	components:{
		vselected
	},
    data () {
        return {
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
        	]

        }    
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
</style>
