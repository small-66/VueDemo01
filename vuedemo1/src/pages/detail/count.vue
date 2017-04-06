<template>
  <div class="sales-board">
    <div class="sales-board-intro">
    	<h2>数据统计</h2>
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
    			媒介：
    		</div>
    		<div class="sales-board-line-right">
    		  <selection1 :selections1="porductTypes"></selection1>
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
import selection1 from '../../components/base/selection_all'
import counter from '../../components/base/counter'
export default {
    components:{
        counter,
        selection1
    },
    data () {
        return {
            porductTypes:[
                {
                    label: '纸质报告',
                    value: 0
                },
                {
                    label: 'pdf',
                    value: 1
                },
                {
                    label: '页面报告',
                    value: 2
                },
                {
                    label: '邮件',
                    value: 3
                }
            ]
        }    
    },
    methods:{
        choses(data){
            console.log(data)
        }
    }
}
</script>
<style>
</style>
