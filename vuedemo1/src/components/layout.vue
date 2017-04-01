<template>
  <div class="wrap">
     <div class="app-head">
     	<div class="app-head-inner"> 
            <router-link :to="{path : '/'}">
     		    <img src="../assets/logo.png" />
            </router-link>
     		<div class="head-nav">
     			<ul class="nav-list">
                    <li v-if="username!==''">{{ username }}</li>
                    <li v-if="username!==''" class="nav-pile">|</li>
                    <li v-if="username!==''"  @click="quit">退出</li>
     				<li v-if="username===''" @click="logClick">登录</li>
     				<li v-if="username===''" class="nav-pile">|</li>
     				<li v-if="username===''" @click="regClick">注册</li>
     				<li class="nav-pile">|</li>
     				<li @click="aboutClick">关于</li>
     			</ul>
     		</div>
     	</div>
     </div>
     <div class="app-content">
     	<router-view></router-view>
     </div>
     <div class="app-foot">
     	<p>@ 2016 finshenal MIT</p>
     </div>
     
     <my-dialog :is-show="isShowLogDialog" @on-close="closeDialog('isShowLogDialog')">
        <log-form @has-log="onSuccessLog"></log-form>
     </my-dialog>
     <my-dialog :is-show="isShowRegDialog" @on-close="closeDialog('isShowRegDialog')">
        <reg-form @has-reg="onSuccessReg"></reg-form>
     </my-dialog>
     <my-dialog :is-show="isShowAboutDialog" @on-close="closeDialog('isShowAboutDialog')">
        <p> about</p>
     </my-dialog>
  </div>
</template>

<script>
import Dialog from './dialog'
import logForm from './logForm'
import regForm from './regForm'
export default {
    components: {
        MyDialog: Dialog,
        logForm,
        regForm
    },
	data() {
		return {
			isShowLogDialog: false,
            isShowRegDialog: false,
            isShowAboutDialog: false,
            username: ''
		}
	},
    methods: {
        logClick(){
            this.isShowLogDialog = true
        },
        regClick(){
            this.isShowRegDialog = true
        },
        aboutClick(){
            this.isShowAboutDialog = true
        },
        closeDialog(attr){
            this[attr] = false
        },
        onSuccessLog(data){
            this.username = data.username
            this.closeDialog('isShowLogDialog')
        },
        onSuccessReg(){
            alert('注册成功')
            this.closeDialog('isShowRegDialog')
        },
        quit(){
            this.username = ''
        }
        
    }
}	
</script>

<style>
/**
 * Eric Meyer's Reset CSS v2.0 (http://meyerweb.com/eric/tools/css/reset/)
 * http://cssreset.com
 */
html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed,
figure, figcaption, footer, header,
menu, nav, output, ruby, section, summary,
time, mark, audio, video, input {
    margin: 0;
    padding: 0;
    border: 0;
    font-size: 100%;
    font-weight: normal;
    vertical-align: baseline;
}

/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure,
footer, header, menu, nav, section {
    display: block;
}

body {
    line-height: 1;
}

blockquote, q {
    quotes: none;
}

blockquote:before, blockquote:after,
q:before, q:after {
    content: none;
}

table {
    border-collapse: collapse;
    border-spacing: 0;
}

/* custom */
a {
    color: #7e8c8d;
    text-decoration: none;
    -webkit-backface-visibility: hidden;
}

li {
    list-style: none;
}

::-webkit-scrollbar {
    width: 5px;
    height: 5px;
}

::-webkit-scrollbar-track-piece {
    background-color: rgba(0, 0, 0, 0.2);
    -webkit-border-radius: 6px;
}

::-webkit-scrollbar-thumb:vertical {
    height: 5px;
    background-color: rgba(125, 125, 125, 0.7);
    -webkit-border-radius: 6px;
}

::-webkit-scrollbar-thumb:horizontal {
    width: 5px;
    background-color: rgba(125, 125, 125, 0.7);
    -webkit-border-radius: 6px;
}

html, body {
    width: 100%;
}

body {
    -webkit-text-size-adjust: none;
    -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
    font-size: 14px;
    color: #444;
}

.app-head {
	background: #363636;
	color: #b2b2b2;
	height: 90px;
	line-height: 90px;
	width: 100%;
}
.app-head-inner {
	width: 1200px;
	margin: 0 auto;
}
.app-logo {
	float: left;
}
.app-head-inner img {
	width: 50px;
	margin-top: 20px;
}
.head-nav {
	float: right;
}
.head-nav ul {
	overflow: hidden;
}
.head-nav li {
	cursor: pointer;
	float: left;
}
.nav-pile {
	padding: 0 10px;

}
.app-foot {
	text-align: center;
	height: 80px;
	width: 100%;
	line-height: 80px;
	background: #e3e4e8;
	clear: both;
	margin-top: 30px;
}
.container {
	width: 1200px;
	margin: 0 auto;
}



.g-form {
    
}
.g-form-line {
    padding: 15px 0;
}
.g-form-label {
    width: 100px;
    font-size: 16px;
    display: inline-block;
}
.g-form-input {
    display: inline-block;
}
.g-form-input input {
    width: 200px;
    height: 30px;
    line-height: 30px;
    vertical-align: middle;
    padding: 0 10px;
    border: 1px solid #ccc;
}
.g-form-btn {
    padding-left: 100px;
}
.g-form-error {
    color: red;
    padding-left: 15px;
}
</style>
