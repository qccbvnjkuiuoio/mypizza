<template>
  <div id="app" class="container">
    <Header></Header>
    <router-view/>
  </div>
</template>

<script>
// <!--引入Header-->
import Header from '@/components/Header'
export default {
  name: 'App',
  data(){
    return{

    }
  },
  components:{
    'Header':Header
  }
}

</script>

<style>

</style>
