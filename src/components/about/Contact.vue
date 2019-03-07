<template>
  <div class="contact">
    <div class="card text-center">
      <div class="card-header">
        <h3>联系我们</h3>
      </div>
      <div class="card-body">
        <h5 class="card-title"></h5>
        <p class="card-text">欢迎来到pizza 联系我们</p>
        <router-link to="/address" class="btn btn-primary">地址信息</router-link>
        <router-link to="/person" class="btn btn-primary">法人代表</router-link>
        <router-link to="/telphone" class="btn btn-primary">联系方式</router-link>
        <router-view></router-view>
      </div>
      <div class="card-footer text-muted">
        2 days ago
      </div>
    </div>

  </div>
</template>

<script>
  export default {
    name: 'Contact',
    data () {
      return {
        msg: '欢迎来到联系页面'
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


</style>
