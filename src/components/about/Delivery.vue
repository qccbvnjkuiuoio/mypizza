<template>
  <div class="delivery">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
  export default {
    name: 'Delivery',
    data () {
      return {
        msg: '欢迎来到快递消息页面'
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
