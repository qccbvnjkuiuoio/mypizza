<template>
  <div class="register">
    <form class="container col-4 mt-4">
      <h3 class="text-center">注册</h3>
      <div class="form-group">
        <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="请输入账号" v-model="username">
      </div>
      <div class="form-group">
        <input type="password" class="form-control" id="exampleInputPassword1" placeholder="请输入密码" v-model="psd">
      </div>
      <div class="form-group">
        <input type="password" class="form-control" id="exampleInputPassword2" placeholder="请再次输入密码" v-model="repsd">
      </div>
      <div class="form-check">
        <input type="checkbox" class="form-check-input" id="exampleCheck1">
        <label class="form-check-label" for="exampleCheck1">Check me out</label>
      </div>
      <button type="submit" class="btn btn-primary btn-block" @click.prevent="onsubmit">Submit</button>
    </form>
  </div>
</template>

<script>
  import axios from 'axios'
  export default {
    name: 'Register',
    data () {
      return {
        username:'',
        psd:'',
        repsd:''
      }
    },
    methods:{
      onsubmit(){
        if (this.username==''||this.psd==''||this.repsd==''){
          alert('当前表单不能为空！')
        } else {
          if (this.psd===this.repsd){
            var formData={
              username:this.username,
              psd:this.psd
            }
            axios.post('./user-qcc.json',formData)
              .then(res=>{
                // console.log('当前数据抛出成功！')
                //页面路径跳转,通过push或者通过replace
                this.$router.push('/login')
              })
          }
        }

      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
