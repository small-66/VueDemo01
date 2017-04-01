<template>
  <div class="login-from">
    <div ckass="g-form">
        <div class="g-form-line">
            <span class="g-form-label">用户名：</span>
            <div class="g-form-input">
                <input v-model="usernameModel" type="text" placeholder="请输入用户名"/>
            </div>
            <span class="g-form-error">{{userErrors.errorText}}</span>
        </div>
        <div class="g-form-line">
            <span class="g-form-label">密码：</span>
            <div class="g-form-input">
                <input v-model="passwordModel" type="text" placeholder="请输入密码"/>
            </div>
            <span class="g-form-error">{{ passwordErrors.errorText }}</span>
        </div>
        <div class="g-form-line">
            <div class="g-form-btn">
                <a class="button" @click="onLogin">登录</a>
            </div>
        </div>
        <p>{{ errorText }}</p>
    </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
        usernameModel: '',
        passwordModel: '',
        errorText: ''
        }
    },
    computed: {
        userErrors () {
            let errorText,status
            if(!/@/g.test(this.usernameModel)){
                status = false
                errorText = '必须包含@'
            }
            else {
                status = true
                errorText = ''
            }
            if(!this.userFlag){
                errorText = ''
                this.userFlag = true
            }
            return {
                status,
                errorText
            }
        },
        passwordErrors(){
            let errorText,status
            if(!/^\w{1,6}$/g.test(this.passwordModel)){
                status = false
                errorText = '1-6位数字或字母'
            }
            else {
                status = true
                errorText = ''
            }
            if(!this.passwordFlag){
                errorText = ''
                this.passwordFlag = true
            }
            return {
                status,
                errorText
            }
        }
    },
    methods: {
        onLogin(){
            if(!this.userErrors.status || !this.passwordErrors.status){
                this.errorText = "规则不通过"
            }else{
                this.errorText = ""
                this.$http.get('api/login').then((res) => {
                    this.$emit('has-log',res.data)
                    console.log(res.data)
                },
                (error) => {
                    console.log(error)
                }
                )
            }
        }
    }
}	
</script>

<style>
</style>
