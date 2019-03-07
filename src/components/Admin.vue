<template>
  <div class="admin container row" >
    <div id="box1 " class="col-6 ml-4"><Addpizza></Addpizza></div>
    <div id="box2 " class="col-5">123458</div>
  </div>
</template>

<script>
  import Addpizza from '@/components/Addpizza'
  export default {
    name: 'Admin',
    data () {
      return {
        msg: '欢迎来到管理员页面'
      }
    },

    components:{
      'Addpizza':Addpizza
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
