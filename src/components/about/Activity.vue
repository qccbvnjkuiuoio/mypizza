<template>
  <div class="activity">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
  export default {
    name: 'Activity',
    data () {
      return {
        msg: '欢迎来到活动页面'
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1, h2 {
    font-weight: normal;
  }

</style>
