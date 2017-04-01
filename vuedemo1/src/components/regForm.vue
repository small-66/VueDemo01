<template>
  <div class="reg-from">
    <div ckass="g-form">
        <div class="g-form-line">
            <span class="g-form-label">用户名：</span>
            <div class="g-form-input">
                <input v-model="usernameModel" type="text" placeholder="请输入用户名(必须包含@)"/>
            </div>
        </div>
        <div class="g-form-line">
            <span class="g-form-label">密码：</span>
            <div class="g-form-input">
                <input v-model="passwordModel" type="text" placeholder="请输入密码(1-6位数字字母组合)"/>
            </div>
        </div>
        <div class="g-form-line">
            <div class="g-form-btn">
                <a class="button" @click="onReg">注册</a>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
            usernameModel: '',
            passwordModel: ''
        }
    },
    computed: {
         userErrors () {
            let status
            if(!/@/g.test(this.usernameModel)){
                status = false
            }
            else {
                status = true
            }
            if(!this.userFlag){
                this.userFlag = true
            }
            return {
                status
            }
        },
        passwordErrors(){
            let status
            if(!/^\w{1,6}$/g.test(this.passwordModel)){
                status = false
            }
            else {
                status = true
            }
            if(!this.passwordFlag){
                this.passwordFlag = true
            }
            return {
                status
            }
        }
    },
    methods: {
        onReg () {
            if(!this.userErrors.status || !this.passwordErrors.status){
                alert('规则不正确')
            }else{
                this.$http.get('api/login').then((res) => {
                    this.$emit('has-reg')
                    res.data.username = this.usernameModel
                    res.data.userId = this.passwordModel
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
