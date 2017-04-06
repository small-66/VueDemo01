<template>
  <div class="sales-board">
    <div class="sales-board-intro">
    	<h2>数据预测</h2>
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
    		   <counter ></counter>
    		</div>
    	</div>
    	<div class="sales-board-line">
    		<div class="sales-board-line-left">
    			产品类型：
    		</div>
    		<div class="sales-board-line-right">
    		      <selections-one :selections-one="porductTypes"></selections-one>
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
import selectionsOne from '../../components/base/selection_1'
import counter from '../../components/base/counter'

export default {
    components:{
        selectionsOne,
        counter
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
</style>
