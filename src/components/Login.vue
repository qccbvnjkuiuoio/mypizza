<template>
  <div class="login">
    <form class="container col-4 mt-4">
      <h3 class="text-center">登录</h3>
      <div class="form-group mt-3">
        <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="请输入账号" v-model="username">
      </div>
      <div class="form-group">
        <input type="password" class="form-control" id="exampleInputPassword1" placeholder="请输入密码" v-model="psd">
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
    name: 'Login',
    data () {
      return {
        username:'',
        psd:''
      }
    },
    methods:{
      onsubmit(){
        axios.get('./user-qcc.json')
          .then((res)=>{
            // console.log(res.data)
            //通过for-in对res.data（对象）进行循环遍历，然后放入一个新数组result内
            //注意:因为res.data是一个对象，所以只能用for-in进行循环遍历
            var result=[]
            for (var key in res.data) {
              var user=res.data[key]
              result.push(user)
            }
            console.log(result)
            var trueUser=result.filter((user)=>{
              return user.username===this.username && user.psd===this.psd
            })

            if (trueUser!=null&&trueUser.length>0){
                alert('登录成功')
                this.$router.push('./admin')
            } else{
                alert('账号或者密码错误!请重新输入')
            }
          })
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
