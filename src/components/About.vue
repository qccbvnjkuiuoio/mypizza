<template>
  <div class="about container row mt-5 ml-5">
    <div class="col-4 text-center">
      <div class="alert alert-primary" role="alert">
         <router-link to="/activity" class="alert-link">热门活动</router-link>
      </div>
      <div class="alert alert-secondary" role="alert">
         <router-link to="/contact" class="alert-link">联系我们</router-link>
      </div>
      <div class="alert alert-success" role="alert">
         <router-link to="/history" class="alert-link">历史订单</router-link>
      </div>
      <div class="alert alert-danger" role="alert">
        <router-link to="/delivery" class="alert-link">快递信息</router-link>
      </div>
    </div>
    <div class="col-8">
      <router-view></router-view>
    </div>

  </div>
</template>

<script>
  export default {
    name: 'about',
    data () {
      return {
        msg: '欢迎来到关于我们页面'
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
