<template>
  <div>
    <div class="index-left">
            <div class="index-left-block">
                <h2>全部产品</h2>
                <template v-for="porduct in productList">
                    <h3>{{porduct.title}}</h3>
                    <ul>
                        <li v-for="item in porduct.list">
                            <a :href="item.url">{{item.name}}</a>
                            <span v-if="item.hot" class="hot-tag">HOT</span>
                        </li>
                    </ul>
                    <div v-if="!porduct.last" class="hr"></div>
                </template>
                <div class="index-left-block lastest-news">
                    <h2>最新消息</h2>
                    <ul>
                        <li v-for="item in newsList">
                            <a :href="item.url" class="new-item">{{item.title}}</a>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
        <div class="index-right">
            <slide-show :slides="slides" :inv="slideSpeed"></slide-show>
            <div class="index-board-list">
                <div
                class="index-board-item"
                v-for="(item,index) in boardList"
                :class="[{'line-last' : index %2 !==0},'index-board-'+item.id]"
                >
                   <div class="index-board-item-inner">
                        <h2>{{item.title}}</h2>
                        <p>{{item.description}}</p>
                        <div class="index-board-button">
                            <a href="detail/analysis" class="button">立即购买</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
  </div>
</template>

<script>
import slideShow from '../components/slideShow'


export default {
    components: {
        slideShow
    },
    created(){
        this.$http.get('api/getNewsList')
        .then((res) => {
            this.newsList = res.data
        },(err) => {
            console.log(err);
        })
    },
	data() {
		return {
            slideSpeed:2000
            ,
			productList:{
                pc: {
                    'title': 'PC产品',
                    list: [
                        {
                        name: '数据统计',
                        url: 'detail/count'
                        },
                        {
                        name: '数据预测',
                        url: 'detail/forecast'
                        },
                        {
                        name: '流量分析',
                        url: 'detail/analysis',
                        hot: true
                        },
                        {
                        name: '广告发布',
                        url: 'detail/publish'
                        }
                    ]
                },
                app: {
                    'title': '应用类',
                    last: true,
                    list: [
                        {
                        name: '91助手',
                        url: 'http://weixin.com'
                        },
                        {
                        name: '产品助手',
                        url: 'http://twitter.com'
                        },
                        {
                        name: '智能地图',
                        url: 'http://maps.com'
                        },
                        {
                        name: '团队语音',
                        url: 'http://phone.com'
                        }
                    ]
                }
            },
            newsList:[

            ],
            boardList:[
                {
                title: '开放产品',
                description: '开放产品是一款开放产品',
                id: 'car',
                saleout: false
                },
                {
                title: '品牌营销',
                description: '品牌营销帮助你的产品更好地找到定位',
                id: 'earth',
                saleout: false
                },
                {
                title: '使命必达',
                description: '使命必达快速迭代永远保存最前端的速度',
                id: 'loud',
                saleout: false
                },
                {
                title: '使命必达',
                description: '使命必达快速迭代永远保存最前端的速度',
                id: 'mount',
                saleout: false
                }
            ],
            slides:[
                {
                src: require('../assets/slideShow/1.jpg'),
                title: '流量分析',
                href: 'detail/analysis'
                },
                {
                src: require('../assets/slideShow/2.jpg'),
                title: '数据统计',
                href: 'detail/count'
                },
                {
                src: require('../assets/slideShow/3.jpg'),
                title: '广告发布',
                href: 'detail/publish'
                },
                {
                src: require('../assets/slideShow/4.jpg'),
                title: '数据预测',
                href: 'detail/forecast'
                }
            ]
		}
	}
}
</script>

<style >
.app-content{
    width: 1200px;
    margin: 0 auto;
    overflow: hidden;
}
.index-left {
    float: left;
    width: 300px;
    text-align: left;
}
.index-right {
    float: right;
    width: 900px;
}
.index-left-block {
    margin: 15px;
    background: #fff;
    box-shadow: 0 0 1px #ddd;
}
.index-left-block .hr {
    margin-bottom: 20px;
}
.index-left-block h2 {
    background: #4fc08d;
    color: #fff;
    padding: 10px 15px;
    margin-bottom: 20px;
}
.index-left-block h3 {
    padding: 0 15px 5px 15px;
    font-weight: bold;
    color: #222;
}
.index-left-block ul {
    padding: 10px 15px;
}
.index-left-block li {
    padding: 5px;
}
.index-board-list {
    overflow: hidden;
}
.index-board-item {
    float: left;
    width: 400px;
    background: #fff;
    box-shadow: 0 0 1px #ddd;
    padding: 20px;
    margin-right: 20px;
    margin-bottom: 20px;
}
.index-board-item-inner {
    min-height: 125px;
    padding-left: 120px;
}

.index-board-item h2{
    font-size: 18px;
    font-weight: bold;
    color: #000;
    margin-bottom: 15px;
}
.line-last {
    margin-right: 0;
}
.index-board-button {
    margin-top: 20px;
}
.button {
    background: #4fc08d;
    display: inline-block;
    color: #fff;
    width: 100px;
    text-align: center;
    line-height: 30px;
}
.lastest-news {
    min-height: 512px;
}
.hot-tag {
    background: red;
    color: #fff;
}
.index-board-car .index-board-item-inner{
    background: url(../assets/images/1.jpg) no-repeat;
    background-size: 120px;
}

.index-board-earth .index-board-item-inner{
    background: url(../assets/images/2.jpg) no-repeat;
    background-size: 120px;
}
.index-board-loud .index-board-item-inner{
    background: url(../assets/images/3.jpg) no-repeat;
    background-size: 120px;
}
.index-board-mount .index-board-item-inner{
    background: url(../assets/images/4.jpg) no-repeat;
    background-size: 120px;
}
.new-item{
    display: inline-block;
    width: 200px;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
}
</style>
